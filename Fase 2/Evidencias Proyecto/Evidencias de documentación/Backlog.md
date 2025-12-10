# AkiraFlex

> Clasificación de los 13 módulos y backlog inicial. Enfoque Kanban con entregas incrementales.

## Clasificación de módulos

- CORE (MVP, indispensables):
  - Configuración y Seguridad (CFG/USR): autenticación, roles/permisos, activación de módulos, auditoría.
  - Finanzas (FIN): caja/bancos, CxC, CxP, conciliación CSV, KPIs de liquidez.
  - Gestión Comercial/Ventas (SAL): clientes, ventas, comprobantes, reglas de descuento.
  - Inventario y Productos (INV): stock por bodega, categorías, alertas, trazabilidad.
  - Reportes (REP): dashboard básico y exportación.
  - Sucursales (SUC): usuarios e inventario por sede (si aplica al cliente).

- Aplicados a RepUSA (taller automotriz):
  - CORE anteriores + Compras y Proveedores (COM), Agendas (AGE) y Citas (CIT) para reservas/OT.

- Aplicados a Joyas Origen (taller artesanal):
  - CORE anteriores + Producción (PRO) y Compras y Proveedores (COM).

- Pospuestos (post-MVP salvo necesidad explícita):
  - RRHH, Flota, Logística e integraciones tributarias/pagos avanzadas.

## Product Backlog

> **Formato**: Historias de Usuario priorizadas con criterios de aceptación
> **Etiquetas**: Core, FIN, SAL, INV, COM, CFG, USR, REP, SUC, AGE, CIT, PRO, DB, API, UI, Test, Docs, RepUSA, Joyas
> **Estimación**: S (Small 1-3 días), M (Medium 4-7 días), L (Large 8-14 días), XL (Epic >2 semanas)

### **ÉPICA 1: AUTENTICACIÓN Y SEGURIDAD**

*Priority: HIGH | Epic Size: XL*

#### **US-001: Autenticación de Usuarios**

**Como** gerente de taller/empresa
**Quiero** poder ingresar al sistema con mi email y contraseña
**Para** acceder de forma segura a la información de mi negocio

**Priority:** HIGH | **Size:** M | **Labels:** Core, USR, API, UI

**Criterios de Aceptación:**

- **Given** un usuario registrado, **When** ingresa credenciales válidas, **Then** accede al dashboard principal
- **Given** un usuario no registrado, **When** intenta ingresar, **Then** ve mensaje de error específico
- **Given** un usuario registrado, **When** olvida su contraseña, **Then** puede recuperarla por email

**Tasks Técnicas:**
Checklist:

- [ ] DB: tablas usuarios/sesiones, índices
- [ ] API: endpoints auth (login, refresh, forgot/reset)
- [ ] UI: formularios y validaciones
- [ ] Test: unitarios + integración (happy/errores)
- [ ] Docs: flujos y claims JWT

---
Title: [USR] Roles y permisos por módulo/acción (RBAC)
Labels: Core, USR, API, UI, Test, Docs
Description: Matriz de permisos por vista/acción; guardas en backend/frontend.
Checklist:

- [ ] DB: tablas roles, permisos, role_user
- [ ] API: guards/decorators por permiso
- [ ] UI: visibilidad de componentes por rol
- [ ] Test: acceso autorizado/no autorizado
- [ ] Docs: matriz mínima por módulo

---
Title: [CFG] Activación de módulos por plan de suscripción
Labels: Core, CFG, API, UI, Test, Docs
Description: Mostrar/ocultar módulos en UI y bloquear llamadas en API.
Checklist:

- [ ] DB: tablas plan, plan_module, tenant_plan
- [ ] API: middleware de módulo activo
- [ ] UI: feature flags por módulo
- [ ] Test: módulo inactivo bloquea rutas
- [ ] Docs: cómo activar módulos

---
Title: [CFG] Auditoría de acciones (Mongo)
Labels: Core, CFG, REP, API, DB, Docs
Description: Registrar acciones sensibles con traceId/userId/tenantId; retención ≥180 días.
Checklist:

- [ ] DB: colección logs/auditoría
- [ ] API: interceptor de auditoría
- [ ] REP: reporte de auditoría básico
- [ ] Test: eventos generados
- [ ] Docs: campos y políticas de retención

---
Title: [CFG] Aislamiento multi-tenant con RLS en PostgreSQL
Labels: Core, CFG, DB, Test, Docs
Description: Políticas RLS por tenant/empresa y por sucursal cuando aplique.
Checklist:

- [ ] DB: columnas tenant_id, políticas RLS
- [ ] Seeds: usuarios de prueba por tenant
- [ ] Test: accesos cruzados fallan
- [ ] Docs: guía de RLS

---
Title: [FIN] Arqueo y cierre de caja por sucursal
Labels: Core, FIN, SUC, API, UI, DB, Test
Description: Arqueo diario, registro de diferencias, bloqueo tras cierre.
Checklist:

- [ ] DB: movimientos, cierres, evidencias
- [ ] API: endpoints arqueo/cierre/reapertura
- [ ] UI: flujo de cierre con resumen y adjuntos
- [ ] Test: cierre con diferencias
- [ ] Docs: procedimiento de arqueo

---
Title: [FIN] Conciliación bancaria por CSV/Excel (reglas básicas)
Labels: Core, FIN, API, UI, DB, Test
Description: Importar extractos, matching por monto/fecha/referencia, cola manual.
Checklist:

- [ ] DB: tabla importaciones y estados
- [ ] API: carga, validación, matching
- [ ] UI: revisión y confirmación manual
- [ ] Test: ≥80% matching automático en dataset de prueba
- [ ] Docs: formato soportado

---
Title: [FIN] Cuentas por Cobrar (aging y alertas)
Labels: Core, FIN, API, UI, DB, Test
Description: Segmentos 0–30/31–60/61+ días; recordatorios y promesas de pago.
Checklist:

- [ ] DB: facturas, pagos, promesas
- [ ] API: aging y notificaciones
- [ ] UI: vista aging y acciones
- [ ] Test: alertas programadas
- [ ] Docs: políticas de recordatorio

---
Title: [FIN] Cuentas por Pagar (calendario y duplicados)
Labels: Core, FIN, API, UI, DB, Test
Description: Programación de pagos, prioridad, prevención de duplicados.
Checklist:

- [ ] DB: facturas proveedor, órdenes de pago
- [ ] API: calendario y validaciones
- [ ] UI: vista calendario y flujo de pago
- [ ] Test: regla anti-duplicado
- [ ] Docs: criterios de priorización

---
Title: [FIN] Políticas de crédito por cliente
Labels: FIN, SAL, API, UI, DB, Test
Description: Límites, bloqueo por morosidad, flujo de excepción con aprobación.
Checklist:

- [ ] DB: configuración por cliente
- [ ] API: validaciones en ventas
- [ ] UI: aviso y solicitud de excepción
- [ ] Test: bloqueo por límite
- [ ] Docs: política y umbrales

---
Title: [REP] Dashboard de liquidez y KPIs (DSO/DPO)
Labels: Core, REP, FIN, UI, API, Test
Description: KPIs de saldos, flujo de caja, DSO/DPO y morosidad.
Checklist:

- [ ] API: agregaciones y endpoints KPIs
- [ ] UI: tarjetas y gráficos
- [ ] Test: validación de cálculos
- [ ] Docs: definiciones de KPIs

---
Title: [SAL] Registro de ventas y medios de pago
Labels: Core, SAL, FIN, API, UI, DB, Test
Description: Venta con cliente, ítems, impuestos y medio de pago.
Checklist:

- [ ] DB: facturas/boletas y pagos
- [ ] API: creación y validaciones
- [ ] UI: formulario y comprobante
- [ ] Test: reglas de impuestos/medios
- [ ] Docs: flujo de venta

---
Title: [SAL] Descuentos con reglas y auditoría
Labels: SAL, API, UI, Test, Docs
Description: Tope por rol, motivo obligatorio, auditoría.
Checklist:

- [ ] API: reglas por rol
- [ ] UI: controles y avisos
- [ ] Test: límites y excepciones
- [ ] Docs: tabla de topes

---
Title: [INV] Control de stock por bodega y alertas
Labels: Core, INV, DB, API, UI, Test
Description: Entradas/salidas ajustan stock; alertas por umbral.
Checklist:

- [ ] DB: existencias por bodega
- [ ] API: movimientos y reglas
- [ ] UI: ajustes y alertas
- [ ] Test: umbrales de stock
- [ ] Docs: modelo de datos

---
Title: [INV] Trazabilidad de movimientos
Labels: INV, DB, API, Test
Description: Registro de usuario, fecha, origen/destino, motivo.
Checklist:

- [ ] DB: bitácora de movimientos
- [ ] API: endpoints de consulta
- [ ] Test: integridad de trazas
- [ ] Docs: esquema de auditoría

---
Title: [COM] Órdenes de compra y recepción
Labels: COM, INV, FIN, DB, API, UI, Test
Description: Generación de OC, recepción y actualización de stock y CxP.
Checklist:

- [ ] DB: OC, recepciones, relación con facturas proveedor
- [ ] API: crear/recibir OC
- [ ] UI: flujo de recepción
- [ ] Test: actualización stock/CxP
- [ ] Docs: ciclo de compra

---
Title: [SUC] Sucursales y asignación de usuarios
Labels: SUC, USR, DB, API, UI
Description: Registrar sedes y asignar permisos e inventario por sucursal.
Checklist:

- [ ] DB: tabla sucursales y relación usuario
- [ ] API: CRUD sucursal
- [ ] UI: selector de sucursal
- [ ] Test: restricciones por sede

---
Title: [AGE] Agenda de recursos y disponibilidad (RepUSA)
Labels: RepUSA, AGE, UI, API, Test
Description: Calendario de técnicos/boxes; bloqueos y asignaciones.
Checklist:

- [ ] DB: recursos y reservas
- [ ] API: disponibilidad
- [ ] UI: calendario y arrastrar/soltar
- [ ] Test: solapes y reglas

---
Title: [CIT] Reservas de servicios y confirmaciones (RepUSA)
Labels: RepUSA, CIT, UI, API, Test
Description: Agendar servicios, confirmar y notificar.
Checklist:

- [ ] API: crear/confirmar/cancelar citas
- [ ] UI: flujo de reserva
- [ ] Test: notificaciones

---
Title: [PRO] Recetas/BOM y órdenes de producción (Joyas)
Labels: Joyas, PRO, INV, DB, API, UI, Test
Description: Definir recetas, generar OT y consumir insumos.
Checklist:

- [ ] DB: recetas, OT, consumos
- [ ] API: crear OT y costeo
- [ ] UI: flujo de producción
- [ ] Test: costeo por unidad

---
Title: [REP] Exportación de datos (CSV)
Labels: REP, API, UI
Description: Exportar listados filtrados a CSV.
Checklist:

- [ ] API: endpoints de exportación
- [ ] UI: botón y feedback
- [ ] Test: tamaños y encoding

---
Title: [OBS] Observabilidad: logs y métricas básicas
Labels: Core, OBS, API, DB, Docs
Description: Logs estructurados, métricas de sistema y negocio, tableros.
Checklist:

- [ ] Integración de logger
- [ ] Métricas y endpoints /health
- [ ] Tablero inicial
- [ ] Docs: convenciones

---
Title: [SEC] Seguridad básica (TLS, headers, rate limit)
Labels: Core, SEC, API, Docs, Test
Description: TLS 1.2+, headers de seguridad, rate limiting por IP/tenant.
Checklist:

- [ ] Config server TLS/headers
- [ ] Rate limiter
- [ ] Test: abuso y límites
- [ ] Docs: checklist de hardening

---
Title: [QA] Estrategia de pruebas y cobertura mínima
Labels: Core, Test, Docs
Description: Configurar unitarias/integración/E2E y metas de cobertura.
Checklist:

- [ ] Pipelines CI
- [ ] Cobertura ≥70% en core
- [ ] Guía de pruebas

---
Title: [REL] Plan de releases y migraciones iniciales
Labels: Core, Docs, DB
Description: Calendario de releases, versionado y estrategia de migraciones.
Checklist:

- [ ] SemVer y ramas
- [ ] Script de migraciones iniciales
- [ ] Notas de versión
