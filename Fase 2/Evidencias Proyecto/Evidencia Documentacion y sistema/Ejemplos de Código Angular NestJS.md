# Ejemplos de Código - Stack Angular + NestJS

> **Implementación específica** para AkiraFlex con Angular frontend y NestJS backend
> **Patrones aplicados**: Multi-tenant, JWT Guards, Event-driven, CQRS

---

## 🏗️ **Arquitectura NestJS Modular**

### **Estructura de Proyecto Recomendada**

```
akira-flex-backend/
├── src/
│   ├── app.module.ts              # Módulo principal
│   ├── config/                    # Configuraciones
│   │   ├── database.config.ts
│   │   ├── jwt.config.ts
│   │   └── redis.config.ts
│   ├── common/                    # Utilidades compartidas
│   │   ├── decorators/
│   │   │   ├── tenant.decorator.ts
│   │   │   └── roles.decorator.ts
│   │   ├── guards/
│   │   │   ├── jwt-auth.guard.ts
│   │   │   ├── roles.guard.ts
│   │   │   └── tenant.guard.ts
│   │   ├── interceptors/
│   │   │   ├── tenant.interceptor.ts
│   │   │   └── audit.interceptor.ts
│   │   └── filters/
│   │       └── http-exception.filter.ts
│   ├── modules/
│   │   ├── auth/                  # Módulo de autenticación
│   │   ├── finance/               # Módulo de finanzas
│   │   │   ├── cash/
│   │   │   ├── accounts-receivable/
│   │   │   ├── accounts-payable/
│   │   │   └── reconciliation/
│   │   ├── sales/                 # Módulo de ventas
│   │   ├── inventory/             # Módulo de inventario
│   │   └── reports/               # Módulo de reportes
│   └── main.ts                    # Entry point
├── package.json
└── tsconfig.json
```

---

## 🔐 **Autenticación Multi-Tenant con NestJS**

### **JWT Strategy con Tenant Validation**

```typescript
// src/modules/auth/strategies/jwt.strategy.ts
import { Injectable, UnauthorizedException } from '@nestjs/common';
import { PassportStrategy } from '@nestjs/passport';
import { ExtractJwt, Strategy } from 'passport-jwt';
import { AuthService } from '../auth.service';

export interface JwtPayload {
  sub: string;          // user ID
  username: string;
  tenantId: string;     // empresa/organización
  branchId?: string;    // sucursal (opcional)
  roles: string[];
  iat: number;
  exp: number;
}

@Injectable()
export class JwtStrategy extends PassportStrategy(Strategy) {
  constructor(private readonly authService: AuthService) {
    super({
      jwtFromRequest: ExtractJwt.fromAuthHeaderAsBearerToken(),
      ignoreExpiration: false,
      secretOrKey: process.env.JWT_SECRET,
    });
  }

  async validate(payload: JwtPayload) {
    // Validar que el tenant existe y está activo
    const tenant = await this.authService.validateTenant(payload.tenantId);
    if (!tenant || !tenant.active) {
      throw new UnauthorizedException('Tenant inactive or invalid');
    }

    // Validar que el usuario existe y pertenece al tenant
    const user = await this.authService.validateUser(payload.sub, payload.tenantId);
    if (!user) {
      throw new UnauthorizedException('User not found or invalid tenant');
    }

    return {
      userId: payload.sub,
      username: payload.username,
      tenantId: payload.tenantId,
      branchId: payload.branchId,
      roles: payload.roles,
      tenant,
      user
    };
  }
}
```

### **Guards Personalizados para Multi-Tenancy**

```typescript
// src/common/guards/tenant.guard.ts
import { Injectable, CanActivate, ExecutionContext, ForbiddenException } from '@nestjs/common';
import { Reflector } from '@nestjs/core';

@Injectable()
export class TenantGuard implements CanActivate {
  constructor(private reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const request = context.switchToHttp().getRequest();
    const user = request.user;

    // Si la ruta requiere un tenant específico
    const requiredTenant = this.reflector.get<string>('tenant', context.getHandler());
    if (requiredTenant && user.tenantId !== requiredTenant) {
      throw new ForbiddenException(`Access denied for tenant: ${user.tenantId}`);
    }

    // Si la ruta requiere una sucursal específica
    const requiredBranch = this.reflector.get<string>('branch', context.getHandler());
    if (requiredBranch && user.branchId !== requiredBranch) {
      throw new ForbiddenException(`Access denied for branch: ${user.branchId}`);
    }

    return true;
  }
}

// src/common/guards/roles.guard.ts
import { Injectable, CanActivate, ExecutionContext } from '@nestjs/common';
import { Reflector } from '@nestjs/core';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.get<string[]>('roles', context.getHandler());
    if (!requiredRoles) {
      return true;
    }

    const request = context.switchToHttp().getRequest();
    const user = request.user;

    return requiredRoles.some((role) => user.roles?.includes(role));
  }
}
```

### **Decoradores Personalizados**

```typescript
// src/common/decorators/roles.decorator.ts
import { SetMetadata } from '@nestjs/common';

export const Roles = (...roles: string[]) => SetMetadata('roles', roles);

// src/common/decorators/tenant.decorator.ts
import { SetMetadata } from '@nestjs/common';

export const RequireTenant = (tenantId: string) => SetMetadata('tenant', tenantId);
export const RequireBranch = (branchId: string) => SetMetadata('branch', branchId);
```

---

## 💰 **Módulo de Finanzas con NestJS**

### **Controlador de Arqueo de Caja**

```typescript
// src/modules/finance/cash/cash.controller.ts
import {
  Controller, Post, Get, Body, Param, UseGuards,
  HttpStatus, HttpException
} from '@nestjs/common';
import { ApiTags, ApiOperation, ApiResponse, ApiBearerAuth } from '@nestjs/swagger';
import { JwtAuthGuard } from '../../../common/guards/jwt-auth.guard';
import { RolesGuard } from '../../../common/guards/roles.guard';
import { TenantGuard } from '../../../common/guards/tenant.guard';
import { Roles } from '../../../common/decorators/roles.decorator';
import { CurrentUser } from '../../../common/decorators/current-user.decorator';
import { CashService } from './cash.service';
import { CashClosureDto, CashClosureResponseDto } from './dto/cash-closure.dto';

@ApiTags('Cash Management')
@ApiBearerAuth()
@Controller('finance/cash')
@UseGuards(JwtAuthGuard, TenantGuard, RolesGuard)
export class CashController {
  constructor(private readonly cashService: CashService) {}

  @Post('closure')
  @Roles('cashier', 'supervisor')
  @ApiOperation({
    summary: 'Cerrar caja diaria',
    description: 'Realiza el arqueo y cierre de caja con validación de diferencias'
  })
  @ApiResponse({
    status: 200,
    description: 'Cierre realizado exitosamente',
    type: CashClosureResponseDto
  })
  @ApiResponse({
    status: 400,
    description: 'Diferencia crítica requiere autorización'
  })
  async closeCash(
    @CurrentUser() user: any,
    @Body() closureDto: CashClosureDto
  ): Promise<CashClosureResponseDto> {
    try {
      const result = await this.cashService.closeCash(
        user.tenantId,
        user.branchId || closureDto.branchId,
        user.userId,
        closureDto
      );

      return result;
    } catch (error) {
      if (error.code === 'CRITICAL_DIFFERENCE') {
        throw new HttpException(
          {
            message: 'Diferencia crítica detectada',
            difference: error.difference,
            requiresApproval: true
          },
          HttpStatus.BAD_REQUEST
        );
      }
      throw error;
    }
  }

  @Get('status/:branchId')
  @Roles('cashier', 'supervisor', 'manager')
  @ApiOperation({ summary: 'Consultar estado de caja por sucursal' })
  async getCashStatus(
    @CurrentUser() user: any,
    @Param('branchId') branchId: string
  ) {
    return this.cashService.getCashStatus(user.tenantId, branchId);
  }

  @Post('reopen')
  @Roles('supervisor', 'manager')
  @ApiOperation({ summary: 'Reabrir caja cerrada (requiere autorización)' })
  async reopenCash(
    @CurrentUser() user: any,
    @Body('closureId') closureId: string,
    @Body('reason') reason: string
  ) {
    return this.cashService.reopenCash(
      user.tenantId,
      closureId,
      user.userId,
      reason
    );
  }
}
```

### **Servicio de Arqueo con Reglas de Negocio**

```typescript
// src/modules/finance/cash/cash.service.ts
import { Injectable, BadRequestException } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { EventEmitter2 } from '@nestjs/event-emitter';
import { CashClosure } from './entities/cash-closure.entity';
import { CashMovement } from './entities/cash-movement.entity';
import { CashClosureDto } from './dto/cash-closure.dto';

@Injectable()
export class CashService {
  constructor(
    @InjectRepository(CashClosure)
    private cashClosureRepo: Repository<CashClosure>,
    @InjectRepository(CashMovement)
    private cashMovementRepo: Repository<CashMovement>,
    private eventEmitter: EventEmitter2
  ) {}

  async closeCash(
    tenantId: string,
    branchId: string,
    userId: string,
    closureDto: CashClosureDto
  ) {
    // 1. Calcular total esperado de ventas del día
    const expectedAmount = await this.calculateExpectedAmount(tenantId, branchId);

    // 2. Calcular diferencia
    const difference = closureDto.countedAmount - expectedAmount;
    const absoDifference = Math.abs(difference);

    // 3. Aplicar reglas de negocio
    const closureResult = await this.applyBusinessRules(
      difference,
      absoDifference,
      closureDto
    );

    // 4. Crear registro de cierre
    const closure = this.cashClosureRepo.create({
      tenantId,
      branchId,
      userId,
      expectedAmount,
      countedAmount: closureDto.countedAmount,
      difference,
      closureDate: new Date(),
      status: closureResult.status,
      requiresApproval: closureResult.requiresApproval,
      notes: closureDto.notes,
      evidence: closureDto.evidence
    });

    const savedClosure = await this.cashClosureRepo.save(closure);

    // 5. Emitir eventos para auditoría y alertas
    this.eventEmitter.emit('cash.closed', {
      tenantId,
      branchId,
      userId,
      closureId: savedClosure.id,
      difference,
      requiresApproval: closureResult.requiresApproval
    });

    if (closureResult.requiresApproval) {
      this.eventEmitter.emit('cash.difference.critical', {
        tenantId,
        branchId,
        difference,
        closureId: savedClosure.id
      });
    }

    return {
      closureId: savedClosure.id,
      expectedAmount,
      countedAmount: closureDto.countedAmount,
      difference,
      status: closureResult.status,
      requiresApproval: closureResult.requiresApproval,
      message: closureResult.message
    };
  }

  private async applyBusinessRules(
    difference: number,
    absoDifference: number,
    closureDto: CashClosureDto
  ) {
    // Reglas de negocio para AkiraFlex
    const NORMAL_THRESHOLD = 1000;      // $1,000 CLP
    const CRITICAL_THRESHOLD = 5000;    // $5,000 CLP

    if (absoDifference <= NORMAL_THRESHOLD) {
      return {
        status: 'CLOSED',
        requiresApproval: false,
        message: 'Cierre normal - diferencia dentro del umbral permitido'
      };
    } else if (absoDifference <= CRITICAL_THRESHOLD) {
      if (!closureDto.notes) {
        throw new BadRequestException(
          'Diferencia significativa requiere justificación'
        );
      }
      return {
        status: 'PENDING_APPROVAL',
        requiresApproval: true,
        message: 'Diferencia significativa - requiere aprobación de supervisor'
      };
    } else {
      // Diferencia crítica
      throw new BadRequestException({
        code: 'CRITICAL_DIFFERENCE',
        message: 'Diferencia crítica - requiere autorización de gerencia',
        difference: difference,
        threshold: CRITICAL_THRESHOLD
      });
    }
  }

  private async calculateExpectedAmount(tenantId: string, branchId: string): Promise<number> {
    // Query optimizada con RLS automático
    const result = await this.cashMovementRepo
      .createQueryBuilder('movement')
      .select('SUM(movement.amount)', 'total')
      .where('movement.tenantId = :tenantId', { tenantId })
      .andWhere('movement.branchId = :branchId', { branchId })
      .andWhere('DATE(movement.createdAt) = CURRENT_DATE')
      .andWhere('movement.type = :type', { type: 'SALE' })
      .getRawOne();

    return parseFloat(result?.total || '0');
  }
}
```

### **DTOs con Validación**

```typescript
// src/modules/finance/cash/dto/cash-closure.dto.ts
import { IsNumber, IsOptional, IsString, IsUUID, Min } from 'class-validator';
import { ApiProperty, ApiPropertyOptional } from '@nestjs/swagger';

export class CashClosureDto {
  @ApiProperty({
    description: 'Monto contado físicamente en caja',
    example: 124500,
    minimum: 0
  })
  @IsNumber({ maxDecimalPlaces: 0 })
  @Min(0)
  countedAmount: number;

  @ApiPropertyOptional({
    description: 'ID de sucursal (si no se envía, usa la del usuario)',
    example: 'branch-uuid-123'
  })
  @IsOptional()
  @IsUUID()
  branchId?: string;

  @ApiPropertyOptional({
    description: 'Observaciones sobre diferencias encontradas',
    example: 'Cliente devolvió $500 en efectivo por producto defectuoso'
  })
  @IsOptional()
  @IsString()
  notes?: string;

  @ApiPropertyOptional({
    description: 'URLs de evidencias (fotos, documentos)',
    example: ['https://storage/evidence1.jpg', 'https://storage/receipt2.pdf']
  })
  @IsOptional()
  @IsString({ each: true })
  evidence?: string[];
}

export class CashClosureResponseDto {
  @ApiProperty({ example: 'closure-uuid-456' })
  closureId: string;

  @ApiProperty({ example: 125000 })
  expectedAmount: number;

  @ApiProperty({ example: 124500 })
  countedAmount: number;

  @ApiProperty({ example: -500 })
  difference: number;

  @ApiProperty({ example: 'CLOSED' })
  status: string;

  @ApiProperty({ example: false })
  requiresApproval: boolean;

  @ApiProperty({ example: 'Cierre normal - diferencia dentro del umbral permitido' })
  message: string;
}
```

---

## 📱 **Frontend Angular con Integración**

### **Servicio Angular para Arqueo de Caja**

```typescript
// src/app/modules/finance/services/cash.service.ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable, BehaviorSubject } from 'rxjs';
import { map, tap } from 'rxjs/operators';

export interface CashClosureRequest {
  countedAmount: number;
  branchId?: string;
  notes?: string;
  evidence?: string[];
}

export interface CashClosureResponse {
  closureId: string;
  expectedAmount: number;
  countedAmount: number;
  difference: number;
  status: string;
  requiresApproval: boolean;
  message: string;
}

@Injectable({
  providedIn: 'root'
})
export class CashService {
  private baseUrl = '/api/finance/cash';
  private cashStatusSubject = new BehaviorSubject<any>(null);
  public cashStatus$ = this.cashStatusSubject.asObservable();

  constructor(private http: HttpClient) {}

  closeCash(request: CashClosureRequest): Observable<CashClosureResponse> {
    return this.http.post<CashClosureResponse>(`${this.baseUrl}/closure`, request)
      .pipe(
        tap(response => {
          // Actualizar estado local
          this.refreshCashStatus();
        })
      );
  }

  getCashStatus(branchId: string): Observable<any> {
    return this.http.get(`${this.baseUrl}/status/${branchId}`)
      .pipe(
        tap(status => this.cashStatusSubject.next(status))
      );
  }

  reopenCash(closureId: string, reason: string): Observable<any> {
    return this.http.post(`${this.baseUrl}/reopen`, { closureId, reason });
  }

  private refreshCashStatus(): void {
    // Obtener branchId del usuario actual y refrescar estado
    // Implementación específica según tu manejo de estado
  }
}
```

### **Componente Angular para Arqueo**

```typescript
// src/app/modules/finance/components/cash-closure/cash-closure.component.ts
import { Component, OnInit } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';
import { MatSnackBar } from '@angular/material/snack-bar';
import { MatDialog } from '@angular/material/dialog';
import { CashService, CashClosureRequest } from '../../services/cash.service';

@Component({
  selector: 'app-cash-closure',
  templateUrl: './cash-closure.component.html',
  styleUrls: ['./cash-closure.component.scss']
})
export class CashClosureComponent implements OnInit {
  closureForm: FormGroup;
  isLoading = false;
  expectedAmount = 0;

  constructor(
    private fb: FormBuilder,
    private cashService: CashService,
    private snackBar: MatSnackBar,
    private dialog: MatDialog
  ) {
    this.closureForm = this.fb.group({
      countedAmount: [0, [Validators.required, Validators.min(0)]],
      notes: ['']
    });
  }

  ngOnInit(): void {
    this.loadExpectedAmount();
  }

  loadExpectedAmount(): void {
    // Cargar monto esperado del día
    this.cashService.getCashStatus('current-branch').subscribe(
      status => {
        this.expectedAmount = status.expectedAmount;
      }
    );
  }

  get difference(): number {
    const countedAmount = this.closureForm.get('countedAmount')?.value || 0;
    return countedAmount - this.expectedAmount;
  }

  get differenceClass(): string {
    const diff = this.difference;
    if (Math.abs(diff) <= 1000) return 'difference-normal';
    if (Math.abs(diff) <= 5000) return 'difference-warning';
    return 'difference-critical';
  }

  onSubmit(): void {
    if (this.closureForm.invalid) return;

    const request: CashClosureRequest = {
      countedAmount: this.closureForm.get('countedAmount')?.value,
      notes: this.closureForm.get('notes')?.value
    };

    this.isLoading = true;

    this.cashService.closeCash(request).subscribe(
      response => {
        this.isLoading = false;

        if (response.requiresApproval) {
          this.snackBar.open(
            'Diferencia significativa - Requiere aprobación de supervisor',
            'OK',
            { duration: 5000, panelClass: 'warning-snackbar' }
          );
        } else {
          this.snackBar.open(
            'Caja cerrada exitosamente',
            'OK',
            { duration: 3000, panelClass: 'success-snackbar' }
          );
        }
      },
      error => {
        this.isLoading = false;

        if (error.error?.code === 'CRITICAL_DIFFERENCE') {
          this.handleCriticalDifference(error.error);
        } else {
          this.snackBar.open(
            error.error?.message || 'Error al cerrar caja',
            'OK',
            { duration: 5000, panelClass: 'error-snackbar' }
          );
        }
      }
    );
  }

  private handleCriticalDifference(error: any): void {
    // Mostrar dialog para diferencias críticas
    const dialogRef = this.dialog.open(CriticalDifferenceDialogComponent, {
      width: '500px',
      data: {
        difference: error.difference,
        threshold: error.threshold
      }
    });

    dialogRef.afterClosed().subscribe(result => {
      if (result === 'contact-manager') {
        this.snackBar.open(
          'Contacte a gerencia para autorización',
          'OK',
          { duration: 5000 }
        );
      }
    });
  }
}
```

---

## 🔄 **Sistema de Eventos para Alertas**

### **Event Listeners con NestJS**

```typescript
// src/modules/alerts/listeners/cash-events.listener.ts
import { Injectable } from '@nestjs/common';
import { OnEvent } from '@nestjs/event-emitter';
import { AlertsService } from '../alerts.service';

@Injectable()
export class CashEventsListener {
  constructor(private alertsService: AlertsService) {}

  @OnEvent('cash.difference.critical')
  async handleCriticalDifference(payload: any) {
    await this.alertsService.sendCriticalAlert({
      type: 'CASH_DIFFERENCE_CRITICAL',
      tenantId: payload.tenantId,
      branchId: payload.branchId,
      data: {
        difference: payload.difference,
        closureId: payload.closureId
      },
      recipients: ['supervisor', 'manager'],
      channels: ['email', 'sms', 'push']
    });
  }

  @OnEvent('cash.closed')
  async handleCashClosed(payload: any) {
    // Log de auditoría para cierres normales
    console.log(`Caja cerrada - Tenant: ${payload.tenantId}, Diferencia: ${payload.difference}`);
  }
}
```

Este stack **Angular + NestJS** te proporciona:

1. **✅ Type Safety completo** - TypeScript end-to-end
2. **✅ Arquitectura consistente** - Decoradores en ambos lados
3. **✅ Multi-tenancy nativo** - Guards y RLS integrados
4. **✅ API auto-documentada** - Swagger automático
5. **✅ Testing integrado** - Mocking y DI simplificados
6. **✅ Escalabilidad** - Modular desde el diseño

¿Te gustaría que profundice en algún módulo específico o que creemos más ejemplos de integración Angular-NestJS?
