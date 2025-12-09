# Backlog priorizado

## Fase 1: Configuración Técnica y Librería Compartida

AFS-090: Configurar tsconfig.json con paths y tipos compartidos
AFS-091: Configurar eslint con reglas específicas para contratos y utilidades
AFS-092: Configurar prettier para formato consistente en todo el repositorio
AFS-093: Configurar jest para pruebas unitarias con cobertura por carpeta
AFS-094: Configurar vitest o tsup si se requiere bundling optimizado
AFS-095: Configurar commitlint y husky para validación de commits convencionales
AFS-096: Configurar semantic-release para versionado automático
AFS-097: Configurar changelog automático con agrupación por tipo de cambio
AFS-098: Configurar package.json con scripts para build, test, lint y release

### Validaciones y Constantes Compartidas

AFS-066: Crear función validateEmail con expresión regular
AFS-067: Crear función validateRut con verificación de dígito
AFS-068: Crear función validatePhoneNumber con formato internacional
AFS-069: Crear función validateRequiredFields para objetos genéricos
AFS-070: Crear función validateDateRange con fechas válidas
AFS-071: Crear función validateEnumValue para tipos restringidos
AFS-073: Definir constantes ORDER_STATUS, USER_STATUS, SALE_STATUS
AFS-074: Definir constantes PERMISSIONS, ROLES, ENTITY_TYPES
AFS-075: Definir constantes CRUD_ACTIONS, AUDIT_ACTIONS, MOVEMENT_TYPES
AFS-076: Definir constantes DEFAULT_LOCALE, SUPPORTED_LANGUAGES
AFS-077: Definir constantes ERROR_CODES, VALIDATION_MESSAGES

### Documentación Técnica Inicial

AFS-079: Crear README técnico de la librería compartida
AFS-080: Documentar estructura de carpetas por dominio (user, order, company)
AFS-081: Documentar convenciones de nombres para interfaces, tipos y funciones
AFS-082: Documentar estrategia de versionado con semantic-release
AFS-085: Crear repositorio inicial del proyecto

### Interfaces Base y Auditoría

AFS-001: Crear interfaz User con atributos base (id, name, email, status)
AFS-002: Crear tipo UserStatus como enum compartido
AFS-006: Crear interfaz Company con datos fiscales y visuales
AFS-007: Crear tipo CompanyStatus como enum compartido
AFS-008: Crear interfaz CompanyConfig para zona horaria, moneda, idioma
AFS-009: Crear tipo CompanyPlan como enum de suscripción
AFS-011: Crear interfaz Role con nombre, descripción y permisos
AFS-012: Crear interfaz Permission con scope y acción
AFS-013: Crear tipo PermissionScope como enum compartido
AFS-014: Crear tipo RoleAssignment para usuarios
AFS-056: Crear interfaz AuditEntry con usuario, acción, fecha y entidad
AFS-057: Crear tipo AuditAction como enum (create, update, delete, login)
AFS-058: Crear interfaz ChangeLog con campo, valor anterior y nuevo
AFS-059: Crear interfaz EntityAuditTrail para historial completo
AFS-126: Crear interfaz SecurityEvent para registrar intentos de acceso no autorizados o cambios críticos

### Configuración Regional

AFS-061: Crear interfaz LocaleSettings con idioma, moneda, zona horaria
AFS-062: Crear tipo CurrencyCode como enum (CLP, USD, EUR)
AFS-063: Crear tipo LanguageCode como enum (es, en, pt)
AFS-064: Crear interfaz RegionalFormat para fechas y números

### Pruebas Unitarias Iniciales

AFS-099: Implementar pruebas unitarias para todos los contratos (User, Order, etc.)
AFS-100: Implementar pruebas unitarias para funciones utilitarias (formatDate, validateEmail)
AFS-101: Implementar pruebas de consistencia entre enums y tipos
AFS-103: Implementar pruebas de validación cruzada (validateDateRange, validateEnumValue)
AFS-104: Configurar reporte de cobertura por módulo funcional

## Fase 2: Configuración Técnica de la API y Autenticación

### Configuración Técnica API

AFA-110: Configurar entorno .env con variables sensibles
AFA-111: Configurar conexión a base de datos PostgreSQL
AFA-112: Configurar migraciones con TypeORM
AFA-113: Configurar validación global con class-validator
AFA-114: Configurar manejo global de errores
AFA-115: Configurar interceptores para respuestas estándar
AFA-116: Configurar DTOs y pipes para validación de entrada
AFA-117: Configurar Swagger para documentación de API
AFA-118: Configurar estructura modular de carpetas por dominio
AFA-119: Configurar alias de importación con tsconfig-paths
AFA-120: Configurar ESLint con reglas específicas para NestJS
AFA-121: Configurar Prettier para formato consistente
AFA-122: Configurar script de start y build en package.json
AFA-123: Configurar tsconfig.json para compatibilidad con librería compartida
AFA-124: Configurar nodemon para entorno de desarrollo
AFA-125: Configurar logging estructurado con Winston o Pino
AFA-126: Configurar manejo de excepciones con filtros personalizados
AFA-127: Configurar rate limiting para endpoints sensibles
AFA-128: Configurar compresión y optimización de respuestas HTTP

### Autenticación y Seguridad API

AFA-001: Implementar endpoint de login con JWT
AFA-002: Implementar endpoint de logout
AFA-003: Implementar endpoint de refresh token
AFA-004: Configurar guardias de autenticación por rol
AFA-005: Implementar middleware de auditoría de acciones
AFA-006: Configurar CORS y headers de seguridad
AFA-007: Implementar validación de token en rutas protegidas
AFA-008: Implementar recuperación de contraseña por email
AFA-009: Implementar verificación de email al registrar usuario
AFA-010: Implementar bloqueo de cuenta tras múltiples intentos fallidos
AFA-190: Configurar integración con bóvedas seguras (por ejemplo, AWS Secrets Manager o HashiCorp Vault)
AFA-191: Implementar rotación automática de claves JWT y tokens de API
AFA-192: Configurar validación automática contra inyecciones SQL
AFA-193: Configurar protección CSRF en endpoints sensibles
AFA-194: Implementar endpoint para consultar eventos de seguridad con filtros

### Integración con Librería Compartida

AFA-129: Integrar interfaces y DTOs desde akira-flex-shared-lib
AFA-130: Integrar constantes y enums desde librería compartida
AFA-131: Integrar helpers de validación desde librería compartida
AFA-132: Validar compatibilidad de rutas y contratos con frontend
AFA-133: Configurar sincronización de versiones entre API y librería
AFA-134: Documentar dependencias técnicas entre API y librería
AFA-135: Implementar pruebas de integración entre API y librería compartida

### Pruebas Iniciales API

AFA-136: Implementar pruebas unitarias para servicios
AFA-137: Implementar pruebas unitarias para controladores
AFA-138: Implementar pruebas unitarias para pipes y DTOs
AFA-139: Implementar pruebas de integración para endpoints
AFA-140: Configurar entorno de testing con base de datos mock
AFA-141: Configurar cobertura de código con Jest
AFA-143: Configurar script de test en package.json
AFA-145: Implementar pruebas de seguridad en endpoints protegidos

### Fase 3: Gestión de Usuarios y Empresas (API y UI)

### Gestión de Usuarios API

AFA-011: Crear endpoint para registrar usuario
AFA-012: Crear endpoint para actualizar usuario
AFA-013: Crear endpoint para eliminar usuario
AFA-014: Crear endpoint para obtener usuario por ID
AFA-015: Crear endpoint para listar usuarios con paginación
AFA-016: Implementar asignación de roles a usuario
AFA-017: Implementar validación de email único
AFA-018: Implementar búsqueda de usuarios por filtros
AFA-019: Implementar activación/desactivación de usuario
AFA-020: Registrar historial de cambios en perfil de usuario

### Gestión de Empresas API

AFA-021: Crear endpoint para registrar empresa
AFA-022: Crear endpoint para actualizar empresa
AFA-023: Crear endpoint para eliminar empresa
AFA-024: Crear endpoint para obtener empresa por ID
AFA-025: Crear endpoint para listar empresas con paginación
AFA-026: Implementar validación de RUT/RUN único
AFA-027: Implementar búsqueda de empresas por filtros
AFA-028: Registrar datos fiscales y comerciales de empresa
AFA-029: Asociar empresa a usuarios administradores
AFA-030: Registrar logotipo y datos visuales de marca
AFA-183: Implementar endpoints para gestionar sucursales y sus relaciones con empresas
AFA-207: Configurar esquema de base de datos multi-tenant con aislamiento por empresa
AFA-208: Implementar endpoints para configurar reglas de negocio específicas por empresa

### Gestión de Usuarios UI

AFU-001: Diseñar pantalla de login con validaciones reactivas
AFU-002: Implementar autenticación con JWT y refresh token
AFU-003: Implementar recuperación de contraseña por email
AFU-004: Implementar verificación de email en registro
AFU-005: Mostrar mensajes de error y bloqueo por intentos fallidos
AFU-006: Implementar guardias de ruta por rol y permisos
AFU-007: Mostrar estado de sesión y botón de logout
AFU-008: Mostrar expiración de sesión y redirección automática
AFU-009: Implementar flujo de cambio de contraseña desde perfil
AFU-010: Mostrar historial de accesos recientes del usuario
AFU-021: Diseñar vista de listado de usuarios con filtros y paginación
AFU-022: Diseñar formulario de creación y edición de usuario
AFU-023: Mostrar roles asignados y permisos activos
AFU-024: Implementar validación de email único en formulario
AFU-025: Mostrar historial de cambios en perfil de usuario
AFU-026: Mostrar avatar personalizado por usuario
AFU-027: Mostrar estado activo/inactivo y fecha de último acceso
AFU-028: Implementar búsqueda avanzada por nombre, email y rol
AFU-029: Mostrar acciones rápidas (editar, desactivar, ver historial)
AFU-030: Mostrar vista de detalle con secciones colapsables

### Gestión de Empresas UI

AFU-011: Implementar layout principal con menú lateral, encabezado y pie de página
AFU-012: Configurar rutas con lazy loading por módulo funcional
AFU-013: Implementar breadcrumb dinámico según ruta activa
AFU-014: Mostrar menú responsive en dispositivos móviles
AFU-015: Mostrar avatar, nombre y rol del usuario autenticado
AFU-016: Mostrar logotipo y nombre de empresa en encabezado
AFU-017: Implementar navegación condicional según permisos del usuario
AFU-031: Diseñar formulario de registro y edición de empresa
AFU-032: Mostrar datos fiscales, comerciales y visuales
AFU-033: Mostrar listado de empresas con filtros por estado
AFU-034: Mostrar usuarios administradores asociados a empresa
AFU-035: Mostrar logo y colores personalizados por empresa
AFU-036: Mostrar configuración regional (moneda, idioma, zona horaria)
AFU-037: Mostrar estado de suscripción y plan activo
AFU-038: Mostrar historial de cambios en datos de empresa
AFU-039: Mostrar vista de detalle con KPIs operativos
AFU-040: Implementar vista de configuración avanzada por empresa
AFU-171: Diseñar vista de sucursales con filtros y reportes específicos
AFU-187: Diseñar vista para administrar configuraciones específicas por tenant

## Fase 4: Gestión Comercial (Productos, Ventas, Inventario)

### Interfaces Comerciales (Librería)

AFS-016: Crear interfaz Product con atributos base
AFS-017: Crear tipo ProductCategory como enum
AFS-018: Crear tipo ProductUnit para unidad de medida
AFS-019: Crear interfaz ProductStockEntry para movimientos
AFS-036: Crear interfaz Sale con productos, cliente, totales
AFS-037: Crear tipo SaleStatus como enum
AFS-038: Crear interfaz SaleItem con cantidad y precio
AFS-039: Crear interfaz Payment con método, monto y fecha
AFS-041: Crear interfaz InventoryMovement con tipo, producto, cantidad
AFS-042: Crear tipo InventoryMovementType como enum
AFS-043: Crear interfaz InventoryAdjustment
AFS-044: Crear interfaz InventoryAuditEntry
AFS-125: Crear interfaz TaxRule con tasa, región y condiciones de aplicación

### Gestión Comercial API

AFA-042: Crear entidad Product
AFA-043: Crear endpoint para registrar producto
AFA-044: Crear endpoint para actualizar producto
AFA-045: Crear endpoint para eliminar producto
AFA-046: Crear endpoint para listar productos con filtros
AFA-047: Crear entidad Category
AFA-048: Crear endpoint para gestionar categorías de productos
AFA-049: Crear entidad Brand
AFA-050: Crear endpoint para gestionar marcas de productos
AFA-051: Crear entidad InventoryItem
AFA-052: Crear endpoint para registrar ingreso de inventario
AFA-053: Crear endpoint para registrar salida de inventario
AFA-054: Crear endpoint para consultar stock actual por producto
AFA-060: Crear entidad Sale
AFA-061: Crear endpoint para registrar venta
AFA-062: Crear endpoint para listar ventas por fecha y cliente
AFA-063: Crear entidad Payment
AFA-064: Crear endpoint para registrar pago asociado a venta
AFA-067: Registrar impuestos aplicables por producto o venta
AFA-068: Registrar método de pago (efectivo, tarjeta, transferencia)
AFA-069: Registrar comprobante de pago o boleta electrónica
AFA-184: Implementar endpoint para calcular impuestos dinámicamente según ubicación o producto
AFA-196: Implementar integración con al menos una pasarela de pago externa para pagos en línea

### Gestión Comercial UI

AFU-051: Diseñar vista de productos con filtros, búsqueda y paginación
AFU-052: Diseñar formulario de creación y edición de producto
AFU-053: Mostrar stock actual y alertas por bajo inventario
AFU-054: Mostrar categorías, marcas y proveedores asociados
AFU-055: Mostrar vista de detalle con historial de movimientos
AFU-056: Implementar selector de unidad de medida y tipo de producto
AFU-057: Mostrar imágenes del producto con galería interactiva
AFU-058: Mostrar precios por variante o presentación
AFU-059: Implementar vista de productos destacados o recomendados
AFU-060: Mostrar productos relacionados en vista de venta
AFU-081: Diseñar vista de ventas con filtros por fecha y cliente
AFU-082: Diseñar formulario de venta con selección de productos
AFU-083: Mostrar resumen de venta con impuestos y descuentos
AFU-084: Mostrar comprobante de pago o boleta electrónica
AFU-085: Mostrar estado de pago (pendiente, parcial, completo)
AFU-086: Implementar vista de pagos asociados a venta
AFU-087: Mostrar historial de pagos por cliente
AFU-088: Mostrar vista de caja con apertura, cierre y movimientos
AFU-089: Mostrar resumen de caja por día y usuario
AFU-090: Implementar vista de devolución o nota de crédito
AFU-094: Mostrar vista de inventario con filtros por categoría
AFU-095: Mostrar alertas por stock mínimo y vencimiento
AFU-096: Implementar vista de ajuste de inventario
AFU-097: Mostrar movimientos de entrada y salida por producto
AFU-099: Mostrar vista de inventario valorizado por fecha
AFU-172: Mostrar impuestos aplicados en formularios de venta y órdenes de servicio
AFU-180: Diseñar componente de pago en la UI con soporte para redirección a pasarelas externas

## Fase 5: Gestión de Clientes, Vehículos y Órdenes de ServicioObjetivo

### Interfaces de Clientes y Servicios (Librería)

AFS-021: Crear interfaz Client con datos personales y comerciales
AFS-022: Crear tipo ClientType como enum (persona, empresa)
AFS-023: Crear interfaz ClientContact para medios de contacto
AFS-024: Crear interfaz ClientAuditEntry para historial
AFS-026: Crear interfaz Vehicle con marca, modelo, patente
AFS-027: Crear tipo VehicleType como enum
AFS-028: Crear interfaz VehicleOwner como relación con cliente
AFS-029: Crear interfaz VehicleServiceHistory
AFS-031: Crear interfaz ServiceOrder con estado, cliente, vehículo
AFS-032: Crear tipo ServiceOrderStatus como enum
AFS-033: Crear interfaz ServiceTask con duración estimada
AFS-034: Crear interfaz ServiceOrderAuditEntry

### Gestión de Clientes y Servicios API

AFA-070: Crear entidad Customer
AFA-071: Crear endpoint para registrar cliente
AFA-072: Crear endpoint para actualizar cliente
AFA-073: Crear endpoint para eliminar cliente
AFA-074: Crear endpoint para buscar cliente por nombre, RUT o teléfono
AFA-075: Crear entidad Vehicle (para taller automotriz)
AFA-076: Crear endpoint para registrar vehículo de cliente
AFA-077: Crear entidad ServiceOrder (orden de servicio)
AFA-078: Crear endpoint para registrar orden de servicio
AFA-079: Crear endpoint para actualizar estado de orden de servicio
AFA-080: Crear endpoint para listar servicios por cliente o vehículo
AFA-084: Registrar historial de servicios realizados por cliente
AFA-085: Registrar garantía asociada a producto o servicio

### Gestión de Clientes y Servicios UI

AFU-061: Diseñar vista de clientes con búsqueda avanzada
AFU-062: Diseñar formulario de registro y edición de cliente
AFU-063: Mostrar vehículos asociados al cliente
AFU-064: Mostrar historial de compras y servicios por cliente
AFU-065: Mostrar estado de cuenta y pagos pendientes
AFU-066: Implementar vista de contacto rápido (WhatsApp, email)
AFU-067: Mostrar alertas de cumpleaños o fidelización
AFU-068: Mostrar vista de cliente frecuente con KPIs
AFU-069: Implementar vista de detalle con timeline de interacción
AFU-070: Mostrar documentos adjuntos por cliente (garantías, fichas)
AFU-071: Diseñar vista de órdenes de servicio con filtros por estado
AFU-072: Diseñar formulario de creación y edición de orden
AFU-073: Mostrar tareas asociadas con duración estimada
AFU-074: Mostrar piezas utilizadas y costos asociados
AFU-075: Mostrar estado visual (pendiente, en proceso, finalizado)
AFU-076: Implementar vista de impresión para orden de servicio
AFU-077: Mostrar historial de servicios por vehículo o cliente
AFU-078: Mostrar firma digital del cliente en cierre de orden
AFU-079: Mostrar vista de seguimiento en tiempo real
AFU-080: Implementar vista de checklist por tipo de servicio

## Fase 6: Gestión de Compras y Proveedores

### Interfaces de Compras (Librería)

AFS-046: Crear interfaz PurchaseOrder con proveedor, productos, estado
AFS-047: Crear tipo PurchaseOrderStatus como enum
AFS-048: Crear interfaz PurchaseItem con cantidad y precio
AFS-049: Crear interfaz PurchaseAuditEntry

### Gestión de Compras API

AFA-055: Crear entidad Supplier
AFA-056: Crear endpoint para gestionar proveedores
AFA-057: Crear entidad PurchaseOrder
AFA-058: Crear endpoint para registrar orden de compra
AFA-059: Crear endpoint para actualizar estado de orden de compra

### Gestión de Compras UI

AFU-091: Diseñar vista de órdenes de compra con estado y proveedor
AFU-092: Diseñar formulario de recepción de productos
AFU-093: Mostrar historial de compras por producto
AFU-098: Mostrar vista de transferencia entre sucursales
AFU-100: Implementar exportación de inventario en CSV/JSON

## Fase 7: Gestión de Roles y Auditoría

### Interfaces de Roles y Auditoría (Librería)

AFS-003: Crear interfaz UserWithRoles para vistas enriquecidas
AFS-004: Crear tipo UserAuditEntry para trazabilidad
AFS-060: Documentar contratos de auditoría por entidad (User, Order, Company)

### Gestión de Roles y Permisos API

AFA-031: Crear endpoint para registrar rol
AFA-032: Crear endpoint para actualizar rol
AFA-033: Crear endpoint para eliminar rol
AFA-034: Crear endpoint para listar roles
AFA-035: Crear endpoint para registrar permiso
AFA-036: Crear endpoint para actualizar permiso
AFA-037: Crear endpoint para eliminar permiso
AFA-038: Crear endpoint para listar permisos
AFA-039: Implementar asignación de permisos a rol
AFA-040: Implementar validación de permisos duplicados
AFA-041: Registrar historial de cambios en roles y permisos

### Gestión Administrativa API

AFA-086: Crear entidad Employee
AFA-087: Crear endpoint para registrar empleado
AFA-088: Crear endpoint para actualizar datos de empleado
AFA-089: Crear endpoint para asignar rol y permisos a empleado
AFA-090: Crear entidad Shift
AFA-091: Crear endpoint para gestionar turnos de trabajo
AFA-092: Crear entidad Expense
AFA-093: Crear endpoint para registrar gasto operativo
AFA-094: Crear endpoint para listar gastos por categoría y fecha
AFA-095: Crear entidad CashRegister
AFA-096: Crear endpoint para apertura y cierre de caja
AFA-097: Crear endpoint para consultar movimientos de caja
AFA-098: Registrar préstamos internos o anticipos a empleados
AFA-099: Registrar ausencias y licencias laborales

### Gestión de Roles y Permisos UI

AFU-041: Diseñar vista de roles con listado y acciones
AFU-042: Diseñar formulario de creación y edición de rol
AFU-043: Mostrar permisos asignados por rol
AFU-044: Implementar selector de permisos con agrupación funcional
AFU-045: Mostrar historial de cambios en roles y permisos
AFU-046: Mostrar vista de detalle con usuarios asociados al rol
AFU-047: Implementar vista de permisos por módulo funcional
AFU-048: Mostrar vista de auditoría de cambios en roles
AFU-049: Implementar duplicación de roles existentes
AFU-050: Mostrar advertencia al eliminar roles en uso
AFU-175: Implementar vistas personalizadas del dashboard según el rol del usuario
AFU-176: Configurar menús dinámicos que muestren solo opciones relevantes según permisos

## Fase 8: Reportes y Notificaciones

### Interfaces de Reportes y Notificaciones (Librería)

AFS-051: Crear interfaz ReportMetric con nombre, valor, unidad
AFS-052: Crear tipo ReportPeriod como enum (daily, weekly, monthly)
AFS-053: Crear interfaz ChartDataPoint con fecha, valor y etiqueta
AFS-054: Crear interfaz KpiMetric con tipo, valor y tendencia
AFS-121: Crear interfaz Notification con tipo, canal (email, push, in-app) y destinatario

### Reportes y Métricas API

AFA-100: Crear endpoint para reporte de ventas por día, semana y mes
AFA-101: Crear endpoint para reporte de productos más vendidos
AFA-102: Crear endpoint para reporte de servicios más solicitados
AFA-103: Crear endpoint para reporte de ingresos vs egresos
AFA-104: Crear endpoint para reporte de inventario bajo stock mínimo
AFA-105: Crear endpoint para reporte de clientes frecuentes
AFA-106: Crear endpoint para exportar reportes en formato JSON/CSV
AFA-107: Crear endpoint para reporte de desempeño por empleado
AFA-108: Crear endpoint para reporte de órdenes de servicio por estado
AFA-109: Crear endpoint para reporte de gastos por categoría
AFA-181: Implementar endpoint para envío de notificaciones automáticas
AFA-187: Implementar filtros dinámicos con soporte para consultas avanzadas
AFA-188: Configurar índices en la base de datos para consultas frecuentes
AFA-189: Implementar vistas materializadas para reportes precalculados

### Reportes y Dashboards UI

AFU-111: Diseñar dashboard principal con KPIs operativos
AFU-112: Mostrar gráfico de ventas por día, semana y mes
AFU-113: Mostrar gráfico de productos más vendidos
AFU-114: Mostrar gráfico de servicios más solicitados
AFU-115: Mostrar gráfico de ingresos vs egresos
AFU-116: Mostrar ranking de clientes frecuentes
AFU-117: Mostrar estado de órdenes de servicio por categoría
AFU-118: Mostrar desempeño por empleado en vista de reportes
AFU-119: Implementar exportación de reportes en JSON/CSV
AFU-120: Mostrar vista de impresión para reportes
AFU-159: Mostrar notificaciones en tiempo real (toast, snackbar)
AFU-169: Diseñar componente de notificaciones en tiempo real con opciones de interacción
AFU-173: Diseñar componente de filtros avanzados con soporte para condiciones anidadas

## Fase 9: Promociones, Integraciones Externas y Escalabilidad

### Interfaces de Promociones (Librería)

AFS-122: Crear interfaz PromotionRule con condiciones (monto mínimo, fechas, productos aplicables)
AFS-123: Crear interfaz DiscountCode con código, tipo (porcentaje, monto fijo) y validez

### Promociones e Integraciones API

AFA-065: Crear entidad Discount
AFA-066: Crear endpoint para aplicar descuento a venta o producto
AFA-182: Implementar endpoint para gestionar promociones dinámicas
AFA-162: Crear endpoint para exportar datos en formato JSON
AFA-163: Crear endpoint para exportar datos en formato CSV
AFA-164: Crear endpoint para importar datos desde archivo CSV
AFA-165: Crear endpoint para sincronizar datos con sistemas externos
AFA-166: Implementar webhook para eventos de venta y servicio
AFA-168: Configurar compatibilidad con clientes móviles o POS
AFA-197: Crear endpoints genéricos para exportar/importar datos en formatos compatibles con ERP/CRM
AFA-198: Implementar webhooks para sincronización bidireccional con sistemas externos
AFA-199: Implementar integración con APIs de mensajería (por ejemplo, Twilio o WhatsApp Business API)
AFA-185: Implementar integración con Redis para caché distribuido
AFA-186: Configurar invalidación automática de caché
AFA-177: Implementar cache para consultas frecuentes

### Promociones e Integraciones UI

AFU-170: Diseñar vista para configurar y aplicar promociones
AFU-181: Diseñar componente de mensajería para enviar notificaciones directas a clientes
AFU-177: Implementar modo offline para operaciones críticas con sincronización automática
AFU-178: Configurar la UI como Progressive Web App (PWA)
AFU-179: Optimizar componentes visuales para pantallas pequeñas

## Fase 10: Pruebas Avanzadas, Documentación y Mantenimiento

### Documentación (Librería, API, UI)

AFS-005: Documentar contrato User con ejemplos de uso
AFS-010: Documentar contrato Company con estructura modular
AFS-015: Documentar contrato Role y Permission con ejemplos
AFS-020: Documentar contrato Product y sus variantes
AFS-025: Documentar contrato Client con estructura extendida
AFS-030: Documentar contrato Vehicle con ejemplos
AFS-035: Documentar contrato ServiceOrder y sus componentes
AFS-040: Documentar contrato Sale y Payment con estructura modular
AFS-045: Documentar contrato InventoryMovement con ejemplos
AFS-050: Documentar contrato PurchaseOrder y sus componentes
AFS-055: Documentar contratos para reportes visuales y exportables
AFS-065: Documentar contratos de configuración regional por empresa
AFS-072: Documentar validadores con ejemplos y casos límite
AFS-078: Documentar cada constante con su contexto de uso
AFS-086: Documentar estrategia de pruebas unitarias por módulo
AFS-087: Documentar ejemplos de uso para cada tipo, función y contrato
AFS-088: Documentar contratos críticos por entidad en archivos separados
AFS-109: Documentar reglas de compatibilidad entre versiones
AFS-110: Documentar estrategia de actualización en consumidores
AFS-112: Documentar flujo de publicación y revisión por PR
AFS-113: Documentar convenciones de nombres para interfaces, tipos y funciones
AFS-114: Documentar estructura de carpetas y agrupación por dominio
AFS-115: Documentar estrategia de refactorización sin romper contratos
AFS-116: Documentar cómo extender contratos sin afectar consumidores
AFS-117: Documentar cómo agregar nuevos dominios
AFS-118: Documentar cómo sincronizar cambios entre UI y API
AFS-119: Documentar cómo versionar tipos compartidos por entorno
AFS-120: Documentar cómo auditar cambios en contratos críticos
AFS-127: Documentar manuales de usuario en formato PDF o Markdown
AFA-149: Documentar endpoints en Swagger
AFA-150: Documentar estructura de módulos y servicios
AFA-151: Documentar convenciones de errores y respuestas
AFA-152: Documentar integración con librería compartida
AFA-153: Crear README técnico del proyecto
AFA-154: Crear CONTRIBUTING.md con reglas de contribución
AFA-155: Configurar semantic-release para versionado automático
AFA-156: Documentar reglas de SemVer para cambios en API
AFA-157: Configurar changelog automático con semantic-release
AFA-158: Documentar dependencias externas y configuración de entorno
AFA-159: Documentar estrategia de despliegue y rollback
AFA-160: Documentar estructura de base de datos y relaciones
AFA-161: Documentar convenciones de nombres en entidades y endpoints
AFA-167: Documentar estructura de payloads para integración externa
AFU-149: Crear README técnico del proyecto UI
AFU-150: Documentar estructura de módulos y componentes
AFU-151: Documentar integración con librería compartida
AFU-152: Crear CONTRIBUTING.md con reglas de contribución
AFU-153: Configurar semantic-release para versionado automático
AFU-154: Documentar reglas de SemVer para cambios visuales
AFU-155: Configurar changelog automático con commits convencionales
AFU-156: Documentar convenciones de nombres y estructura de carpetas
AFU-157: Documentar estrategia de branching y etiquetado
AFU-158: Documentar flujos de CI/CD para frontend
AFU-185: Crear guías interactivas en la UI para nuevos usuarios
AFU-186: Diseñar flujo de onboarding en la UI con pasos guiados

### Pruebas Avanzadas

AFS-102: Implementar pruebas de compatibilidad entre interfaces extendidas
AFS-105: Documentar estrategia de pruebas por carpeta
AFA-142: Validar consistencia entre DTOs y respuestas reales
AFA-144: Documentar estrategia de testing por módulo funcional
AFA-146: Implementar pruebas de rendimiento para endpoints críticos
AFA-147: Implementar pruebas de regresión para flujos comerciales
AFA-148: Automatizar ejecución de pruebas en CI/CD
AFA-200: Implementar pruebas de carga para endpoints críticos
AFA-201: Configurar herramientas como Artillery o JMeter para pruebas de estrés
AFA-202: Configurar suite de pruebas de regresión automatizadas
AFU-139: Implementar pruebas unitarias para componentes visuales
AFU-140: Implementar pruebas unitarias para formularios
AFU-141: Implementar pruebas de integración para navegación
AFU-142: Implementar pruebas de interacción con Cypress
AFU-143: Configurar entorno de testing con mocks y fixtures
AFU-144: Configurar cobertura de código con Jest
AFU-145: Automatizar pruebas en CI/CD
AFU-146: Documentar estrategia de testing por módulo
AFU-147: Implementar pruebas de accesibilidad automatizadas
AFU-148: Mostrar reporte visual de cobertura por componente
AFU-182: Realizar pruebas de usabilidad con usuarios finales
AFU-183: Implementar pruebas A/B para layouts o componentes clave
AFU-184: Configurar pruebas visuales automatizadas con herramientas como Percy o BackstopJS

### Mantenimiento y Escalabilidad

AFS-106: Configurar publicación automática en registro privado
AFS-107: Configurar etiquetas semánticas (fix, feat, refactor, docs)
AFS-108: Configurar control de versiones por contrato
AFS-111: Crear script para verificación de contratos rotos (diff-check)
AFA-171: Implementar limpieza automática de logs antiguos
AFA-172: Implementar archivado de órdenes finalizadas
AFA-173: Implementar rotación de tokens y claves sensibles
AFA-174: Configurar alertas para errores críticos en producción
AFA-175: Documentar estrategia de escalabilidad horizontal
AFA-176: Definir límites de paginación y carga por endpoint
AFA-178: Configurar backups automáticos de base de datos
AFA-179: Documentar estrategia de mantenimiento programado
AFA-180: Implementar endpoint para ver estado del sistema (health check)
AFA-204: Configurar integración con herramientas de monitoreo
AFA-205: Implementar dashboard de monitoreo interno para administradores
AFA-206: Configurar notificaciones automáticas para errores críticos

## Fase 11: Componentes Avanzados y FinalizaciónObjetivo

### Componentes Visuales y UX

AFU-101: Implementar formularios reusables con validaciones reactivas
AFU-102: Mostrar mensajes de error y ayuda contextual
AFU-103: Implementar campos condicionales según tipo de entidad
AFU-104: Implementar selector de fecha con restricciones
AFU-105: Implementar selector de archivos con vista previa
AFU-106: Mostrar modal de confirmación antes de eliminar
AFU-107: Mostrar feedback visual en acciones exitosas o fallidas
AFU-108: Mostrar loading en botones durante operaciones
AFU-109: Implementar edición en línea en tablas
AFU-110: Mostrar tooltips explicativos en íconos y botones
AFU-121: Implementar selector de idioma con persistencia
AFU-122: Integrar claves de traducción desde librería compartida
AFU-123: Mostrar valores formateados según configuración regional
AFU-124: Mostrar moneda, fecha y hora según país de empresa
AFU-125: Mostrar textos traducibles en todos los componentes
AFU-126: Implementar fallback visual para claves faltantes
AFU-127: Mostrar selector de zona horaria en configuración
AFU-128: Mostrar mensajes de error traducidos por código
AFU-129: Implementar navegación por teclado en formularios y tablas
AFU-130: Implementar roles ARIA en componentes clave
AFU-131: Mostrar tooltips explicativos en íconos y botones
AFU-132: Implementar modo oscuro y selector de tema visual
AFU-133: Mostrar mensajes de ayuda contextual en formularios
AFU-134: Implementar accesibilidad para lectores de pantalla
AFU-135: Mostrar animaciones suaves en transiciones de vista
AFU-136: Mostrar loading global en navegación entre módulos
AFU-137: Mostrar contraste visual adecuado en todos los temas
AFU-138: Mostrar vista simplificada para usuarios con baja visión
AFU-160: Implementar vista de calendario para turnos o servicios
AFU-161: Mostrar vista de timeline para órdenes o eventos
AFU-162: Implementar vista de kanban para estados de servicio
AFU-163: Mostrar vista de mapa para ubicaciones de clientes o servicios
AFU-164: Implementar edición en línea en tablas
AFU-165: Mostrar vista de impresión para boletas o reportes
AFU-166: Implementar vista de checklist por tipo de servicio
AFU-167: Mostrar vista de seguimiento en tiempo real
AFU-168: Mostrar vista de auditoría visual por entidad
AFU-174: Implementar sanitización de entradas en formularios para prevenir XSS
