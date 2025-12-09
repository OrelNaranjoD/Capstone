# Requisitos Funcionales y No Funcionales – AkiraFlex

> Propósito: definir qué debe hacer el sistema (RF) y cómo debe comportarse (RNF) de forma medible, trazable y alineada a Kanban.

## Alcance y convenciones

- Identificadores: RF-[DOM]-[n] y RNF-[CAT]-[n] (ej.: RF-FIN-001, RNF-SEC-001).
- Prioridad: MoSCoW (MUST/SHOULD/COULD/WON’T en MVP).
- Estado: Proposed | In Progress | Done (sincronizado con Kanban).
- Criterios de aceptación: formato Given/When/Then.
- Trazabilidad: cada requisito se vincula con tarjetas del `Tablero Kanban.md`, ADRs y, cuando aplique, OpenAPI.

## Requisitos funcionales (RF)

### Finanzas (FIN)

- RF-FIN-001 – Arqueo y cierre de caja (MUST)
  - Descripción: permitir arqueo diario por sucursal/responsable con registro de diferencias y evidencias.
  - Criterios:
    - Given movimientos del día; When se cierra caja; Then se genera acta, se calculan diferencias y se bloquean nuevas operaciones hasta reapertura.
  - Dependencias: Usuarios/Roles, Sucursales.

- RF-FIN-002 – Conciliación bancaria por CSV (MUST)
  - Descripción: importar extractos (CSV/Excel) y conciliar por reglas de monto/fecha/referencia.
  - Criterios:
    - Given un archivo válido; When se procesa; Then ≥80% de transacciones quedan conciliadas automáticamente y el resto en cola manual con sugerencias.

- RF-FIN-003 – Cuentas por Cobrar con aging y alertas (MUST)
  - Descripción: aging de cartera, recordatorios y promesas de pago.
  - Criterios:
    - Given facturas vencidas; When se ejecuta el job diario; Then se envían alertas por segmento (0–30/31–60/61+ días) a responsables.

- RF-FIN-004 – Cuentas por Pagar con calendario (SHOULD)
  - Descripción: calendario de vencimientos, priorización y prevención de pagos duplicados.
  - Criterios:
    - Given facturas registradas; When se programa pago; Then se valida duplicidad y se genera orden de pago con aprobaciones requeridas.

- RF-FIN-005 – Políticas de crédito por cliente (SHOULD)
  - Descripción: límites por cliente, bloqueo automático por morosidad.
  - Criterios:
    - Given cliente sobre límite o en mora; When se intenta nueva venta a crédito; Then el sistema bloquea y ofrece flujo de excepción con aprobación.

### Ventas (SAL)

- RF-SAL-001 – Registro de ventas y medios de pago (MUST)
  - Criterios: venta debe asociar cliente, ítems, impuestos, medio de pago y comprobante.

- RF-SAL-002 – Descuentos con reglas (SHOULD)
  - Criterios: aplicar solo si rol y tope permitido; auditar quién, cuánto y por qué.

### Inventario (INV)

- RF-INV-001 – Control de stock por bodega (MUST)
  - Criterios: entradas/salidas ajustan stock; alertas por umbral mínimo.

- RF-INV-002 – Trazabilidad de movimientos (SHOULD)
  - Criterios: cada movimiento registra usuario, fecha, origen y destino.

### Usuarios y Seguridad (USR)

- RF-USR-001 – Autenticación y gestión de usuarios (MUST)
  - Criterios: registro/invitación, recuperación, bloqueo por intentos.

- RF-USR-002 – Roles y permisos por módulo (MUST)
  - Criterios: matriz de permisos controla vistas/acciones; probado en UI y API.

### Reportes y Dashboards (REP)

- RF-REP-001 – KPIs de liquidez (MUST)
  - Criterios: mostrar saldos de caja/bancos, flujo de caja, DSO/DPO y morosidad por rango.

### Configuración y Suscripciones (CFG)

- RF-CFG-001 – Activación de módulos por plan (MUST)
  - Criterios: solo módulos activos aparecen en UI y API; auditoría de cambios.

## Requisitos no funcionales (RNF)

### Disponibilidad y resiliencia (AVA)

- RNF-AVA-001 – Disponibilidad 99.5% mensual (MUST)
  - SLI/SLO: uptime ≥ 99.5% en servicios del MVP.
- RNF-AVA-002 – RTO/RPO (MUST)
  - RTO ≤ 1h; RPO ≤ 15 min; backups nocturnos y prueba de restore trimestral.

### Rendimiento y escalabilidad (PER)

- RNF-PER-001 – Latencia API (MUST)
  - p95 < 300 ms en endpoints de KPIs y operaciones CRUD clave hasta 100 RPS.
- RNF-PER-002 – Conciliación batch (SHOULD)
  - Procesar 5k líneas CSV en < 2 min con reglas de matching activas.
- RNF-PER-003 – Escalabilidad horizontal (SHOULD)
  - Servicios stateless; colas/eventos para picos.

### Seguridad y cumplimiento (SEC)

- RNF-SEC-001 – Aislamiento multi-tenant (MUST)
  - RLS en PostgreSQL; pruebas negativas de acceso cruzado automatizadas.
- RNF-SEC-002 – Encriptación (MUST)
  - TLS 1.2+ en tránsito; cifrado at-rest en volúmenes/DB.
- RNF-SEC-003 – Tokens y sesiones (MUST)
  - JWT con claims de user/role/tenant/estado; expiración configurable; opción 2FA.
- RNF-SEC-004 – Auditoría (MUST)
  - 100% de acciones sensibles logueadas con correlación (traceId, userId, tenantId) por ≥180 días.

### Observabilidad y operaciones (OBS)

- RNF-OBS-001 – Logging y métricas (MUST)
  - Logs estructurados; métricas de sistema y de negocio; tableros de salud.
- RNF-OBS-002 – Alertas (SHOULD)
  - Alertas por errores, latencia, colas, baja liquidez (reglas de dominio).

### Mantenibilidad y calidad (MTN)

- RNF-MTN-001 – Cobertura y estática (SHOULD)
  - ≥70% cobertura en core; linters/formatters obligatorios en CI.
- RNF-MTN-002 – ADRs y documentación (SHOULD)
  - ADRs para tenancy, DB, mensajería y autenticación; OpenAPI versionado.

### Usabilidad y accesibilidad (UX)

- RNF-UX-001 – Responsividad (MUST)
  - UI usable en desktop/tablet/móvil; layouts adaptativos.
- RNF-UX-002 – Accesibilidad (SHOULD)
  - Buenas prácticas WCAG AA en componentes clave.

### Compatibilidad (COMP)

- RNF-COMP-001 – Navegadores (SHOULD)
  - Chrome/Edge/Firefox versiones soportadas LTS; fallback progresivo.

## Métricas y verificación

- Cada RF incluye criterios Given/When/Then probados en QA.
- Cada RNF define SLI/SLO y se verifica con tests/monitoreo.
- DoD: pruebas automáticas verdes, seguridad básica pasada, documentación actualizada y trazas en Kanban.

## Trazabilidad

- Kanban: cada RF/RNF enlaza a una tarjeta y commit.
- Arquitectura: referencia a ADRs y diagramas C4.
- API: endpoints descritos en OpenAPI por módulo del MVP.
