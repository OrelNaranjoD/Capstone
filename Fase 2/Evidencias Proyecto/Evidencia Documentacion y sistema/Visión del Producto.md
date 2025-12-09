# Visión del Producto – AkiraFlex

## Vision Statement (Elevator Pitch)

### AkiraFlex es una plataforma modular de gestión empresarial que permite a PyMEs del sector comercial y manufacturero controlar su flujo de caja en tiempo real, reducir su DSO en un 20% y automatizar el 80% de sus conciliaciones bancarias, todo a través de módulos activables según sus necesidades específicas, sin incurrir en altos costos de implementación

## 1. Nombre del Proyecto

### AkiraFlex – Plataforma Modular de Gestión Empresarial

## 2. Contexto

AkiraFlex es una iniciativa interna de la empresa Akira Software, orientada al desarrollo de una solución tecnológica que permita a pequeñas y medianas empresas gestionar sus operaciones de manera eficiente, flexible y escalable. El proyecto surge a partir de la identificación de necesidades específicas en empresas del rubro comercial y manufacturero, que requieren herramientas adaptables a sus procesos sin incurrir en altos costos de implementación.

## 3. Propósito

Diseñar y desarrollar una plataforma de gestión empresarial compuesta por módulos activables, que permita abordar los principales requerimientos operativos de empresas validadoras, tales como la gestión de clientes, ventas, inventario, proyecciones financieras, y control de usuarios. La solución debe ser técnicamente robusta, con una arquitectura modular y una base de datos multiempresa que garantice seguridad, escalabilidad y mantenibilidad.

## 4. Objetivos

- Implementar una plataforma con al menos seis módulos funcionales que respondan a los requerimientos operativos de las empresas validadoras.
- Diseñar una arquitectura técnica basada en principios de modularidad, separación de responsabilidades y escalabilidad.
- Establecer un modelo de datos que permita la gestión multiempresa con control de acceso segmentado.
- Integrar un sistema de visualización de indicadores que facilite la toma de decisiones.
- Documentar el diseño técnico, decisiones arquitectónicas y flujo de trabajo para asegurar trazabilidad y continuidad.

## 5. Alcance Inicial

- Módulos contemplados: Clientes, Ventas, Inventario, Proyecciones, Usuarios, Dashboard.
- Funcionalidades: autenticación, gestión de roles y permisos, visualización de métricas, administración de datos operativos.
- Arquitectura modular con separación por capas (presentación, lógica, datos).
- Base de datos con soporte multiempresa y control de acceso por nivel organizacional.

## 6. Metodología de Trabajo

El desarrollo se realizará bajo un enfoque ágil utilizando el sistema Kanban como herramienta de gestión visual. Las tareas se organizarán en un tablero con estados definidos y etiquetas técnicas, permitiendo entregas incrementales, priorización continua y mejora progresiva del producto.

## 7. Equipo Responsable

- **Orel Naranjo Domínguez** – Líder técnico, arquitecto de software y desarrollador principal.
- Colaboradores internos y validadores externos pertenecientes a empresas del rubro comercial y manufacturero.

## 8. Recursos

- Repositorio de código con estructura modular.
- Herramientas de diseño y documentación técnica.
- Acceso a procesos y requerimientos operativos de empresas validadoras.

## 9. Riesgos Iniciales

- Complejidad en la validación con usuarios no técnicos.
- Limitaciones de tiempo para pruebas funcionales y ajustes.

## 10. Aprobación

Este documento declara formalmente el inicio del proyecto AkiraFlex bajo los lineamientos definidos. Se autoriza el desarrollo técnico conforme a los objetivos establecidos.

**Fecha de inicio:** 17 de agosto de 2025
**Responsable:** Orel Naranjo Domínguez

## 11. Propuesta de Valor (enfocada en control de dinero)

### 11.1 Dolores actuales en PyMEs

- Escasa visibilidad del flujo de caja diario, por sucursal y por responsable.
- Conciliación bancaria manual y tardía, con errores por duplicidad o referencias incompletas.
- Cuentas por cobrar sin seguimiento (DSO alto), morosidad y falta de alertas de vencimiento.
- Cuentas por pagar sin calendario ni prioridad, con riesgo de pagos duplicados o fuera de plazo (pérdida de descuentos por pronto pago).
- Caja chica sin arqueos diarios ni bitácora de responsables, generando diferencias no justificadas.
- Ventas a crédito sin políticas de límite, garantías o aprobación; descuentos no controlados.
- Gastos operativos poco clasificados (sin centro de costo), dificultando ver rentabilidad por área, cliente o producto.
- Falta de proyecciones de liquidez y de escenarios (qué pasa si baja la venta, sube el costo o se atrasa un cliente clave).
- Ausencia de trazabilidad y auditoría para cumplir controles internos y mitigar fraude.

### 11.2 Cómo AkiraFlex resuelve estos problemas

- Finanzas integrado por módulos activables: Caja y Bancos, Cuentas por Cobrar (CxC), Cuentas por Pagar (CxP), Presupuestos, Conciliación y Reportes.
- Conciliación semiautomática: importación de extractos (CSV/Excel), emparejamiento por monto/fecha/referencia y reglas configurables para acelerar el proceso.
- Arqueo y cierre de caja por sucursal/responsable con control de diferencias, evidencias y flujo de aprobación.
- CxC con aging, políticas de crédito por cliente (límites, bloqueo automático por morosidad), recordatorios y promesas de pago registradas.
- CxP con calendario de vencimientos, priorización de pagos y controles para evitar duplicidades.
- Clasificación de gastos/ingresos por centro de costo, proyecto, sucursal y módulo para ver rentabilidad y márgenes.
- Dashboards de liquidez en tiempo real: saldo de caja/bancos, flujo de caja, DSO/DPO, morosidad, próximos vencimientos y margen por venta.
- Alertas y automatizaciones: notificaciones de bajo saldo, vencimientos próximos, diferencias de arqueo y desvíos de presupuesto.
- Seguridad y cumplimiento: multiempresa y multisucursal con control de acceso por rol, auditoría de acciones y segregación de datos (RLS/tenancy) respaldada por bitácora de eventos.
- Integración operativa: ventas, compras e inventario alimentan finanzas para costeo y márgenes, evitando reprocesos y errores de digitación.

### 11.3 Indicadores de impacto (KPIs)

- DSO (Days Sales Outstanding) y tasa de recuperación de cobranza.
- DPO (Days Payable Outstanding) y aprovechamiento de descuentos por pronto pago.
- Tiempo promedio de conciliación por período y porcentaje de transacciones conciliadas automáticamente.
- Diferencias de arqueo por período y tiempo de resolución.
- Precisión del flujo de caja proyectado vs. real (desvío %).
- Margen por producto/servicio/cliente y rentabilidad por centro de costo.

### 11.4 Casos de uso iniciales (empresas validadoras)

- RepUSA (Taller automotriz)
  - Módulos aplicados: Ventas, Inventario, Compras, Finanzas (Caja/Bancos, CxC, CxP, Conciliación), Agendas, Citas, Sucursales, Reportes.
  - Flujos críticos:
    1) Orden de trabajo → consumo de repuestos → facturación → cobro → CxC/alertas.
    2) Arqueo y cierre de caja diario por sucursal/responsable.
    3) Conciliación bancaria semanal con reglas automáticas.
  - Métricas objetivo: DSO −20% en 8 semanas; ≥80% conciliación automática; diferencias de arqueo ≤1% de ventas.

- Joyas Origen (Taller artesanal)
  - Módulos aplicados: Ventas, Inventario, Producción, Compras, Finanzas (CxC, CxP, Presupuestos), Reportes.
  - Flujos críticos:
    1) Producción por receta → consumo de insumos → costeo por pieza → venta → cobro.
    2) Anticipos y control de entregas por pedido.
    3) Prioridad de pagos a proveedores según vencimiento y descuentos.
  - Métricas objetivo: DSO −15%; variación costo estándar ≤5%; margen por pieza visible en dashboard.

### 11.5 Hoja de ruta del módulo Finanzas (orientativa)

- Fase 1 – MVP (4–6 semanas): Caja y Bancos, CxC/CxP básicos, arqueo de caja, dashboard de liquidez, alertas de vencimiento, importación de extractos en CSV.
- Fase 2 – Optimización (8–10 semanas): conciliación con reglas avanzadas, centros de costo/presupuestos, políticas de crédito ampliadas y recordatorios automáticos.
- Fase 3 – Integraciones/Proyección (en adelante): integraciones locales (tributarias/pagos) y proyecciones avanzadas de flujo de caja.

## 12. Criterios de éxito del MVP (SLO/SLI)

- Disponibilidad mensual (módulos MVP): ≥99.5%.
- Rendimiento: p95 < 300 ms en KPIs de liquidez y tablero financiero (hasta 100 RPS).
- Conciliación: ≥80% de transacciones conciliadas automáticamente por reglas.
- Tenancy/Seguridad: aislamiento por RLS verificado con tests de acceso cruzado negativos.
- Resiliencia: RTO ≤ 1h, RPO ≤ 15 min (backups y restauración probada).
- Observabilidad: 100% de acciones sensibles auditadas por 180 días.
- Calidad: cobertura de pruebas ≥70% en core finanzas; cero defectos críticos en QA antes de release.

## 13. Product Vision Board

| **Elemento** | **Descripción** |
|--------------|-----------------|
| **Visión** | Plataforma modular que democratiza el control financiero para PyMEs |
| **Grupo Objetivo** | PyMEs comerciales y manufactureras (RepUSA, Joyas Origen como casos piloto) |
| **Necesidades** | Control de flujo de caja, conciliación automática, CxC/CxP eficiente, trazabilidad |
| **Producto** | Sistema multi-tenant con módulos activables: Finanzas, Ventas, Inventario, Reportes |
| **Valor de Negocio** | DSO -20%, 80% conciliación automática, visibilidad en tiempo real, ROI medible |

## 14. Enlaces y documentos relacionados

- Requisitos (RF/RNF): Documentación/Requisitos.md
- Módulos y Backlog (Trello-ready): Documentación/Backlog.md
- Políticas Kanban: Documentación/Tablero Kanban.md
- ADRs clave (Tenancy, Observabilidad, Tecnología): Documentación/ADRs/
