# Akira Flex Shared Library

## 👤 Usuarios

- AFS-001 - Crear interfaz User con atributos base (id, name, email, status)
- AFS-002 - Crear tipo UserStatus como enum compartido
- AFS-003 - Crear interfaz UserWithRolesDto para vistas enriquecidas
- AFS-004 - Crear tipo UserAuditEntry para trazabilidad
- AFS-005 - Documentar contrato User con ejemplos de uso

## 🏢 Empresas

- AFS-006 - Crear interfaz Company con datos fiscales y visuales
- AFS-007 - Crear tipo CompanyStatus como enum compartido
- AFS-008 - Crear interfaz CompanyConfig para zona horaria, moneda, idioma
- AFS-009 - Crear tipo CompanyPlan como enum de suscripción
- AFS-010 - Documentar contrato Company con estructura modular

## 🛂 Roles y Permisos

- AFS-011 - Crear interfaz Role con nombre, descripción y permisos
- AFS-012 - Crear interfaz Permission con scope y acción
- AFS-013 - Crear tipo PermissionScope como enum compartido
- AFS-014 - Crear tipo RoleAssignment para usuarios
- AFS-015 - Documentar contrato Role y Permission con ejemplos

## 🧾 Productos

- AFS-016 - Crear interfaz Product con atributos base
- AFS-017 - Crear tipo ProductCategory como enum
- AFS-018 - Crear tipo ProductUnit para unidad de medida
- AFS-019 - Crear interfaz ProductStockEntry para movimientos
- AFS-020 - Documentar contrato Product y sus variantes

## 👥 Clientes

- AFS-021 - Crear interfaz Client con datos personales y comerciales
- AFS-022 - Crear tipo ClientType como enum (persona, empresa)
- AFS-023 - Crear interfaz ClientContact para medios de contacto
- AFS-024 - Crear interfaz ClientAuditEntry para historial
- AFS-025 - Documentar contrato Client con estructura extendida

## 🚗 Vehículos

- AFS-026 - Crear interfaz Vehicle con marca, modelo, patente
- AFS-027 - Crear tipo VehicleType como enum
- AFS-028 - Crear interfaz VehicleOwner como relación con cliente
- AFS-029 - Crear interfaz VehicleServiceHistory
- AFS-030 - Documentar contrato Vehicle con ejemplos

## 🛠️ Órdenes de Servicio

- AFS-031 - Crear interfaz ServiceOrder con estado, cliente, vehículo
- AFS-032 - Crear tipo ServiceOrderStatus como enum
- AFS-033 - Crear interfaz ServiceTask con duración estimada
- AFS-034 - Crear interfaz ServiceOrderAuditEntry
- AFS-035 - Documentar contrato ServiceOrder y sus componentes

## 💰 Ventas

- AFS-036 - Crear interfaz Sale con productos, cliente, totales
- AFS-037 - Crear tipo SaleStatus como enum
- AFS-038 - Crear interfaz SaleItem con cantidad y precio
- AFS-039 - Crear interfaz Payment con método, monto y fecha
- AFS-040 - Documentar contrato Sale y Payment con estructura modular

## 📦 Inventario

- AFS-041 - Crear interfaz InventoryMovement con tipo, producto, cantidad
- AFS-042 - Crear tipo InventoryMovementType como enum
- AFS-043 - Crear interfaz InventoryAdjustment
- AFS-044 - Crear interfaz InventoryAuditEntry
- AFS-045 - Documentar contrato InventoryMovement con ejemplos

## 🧾 Compras

- AFS-046 - Crear interfaz PurchaseOrder con proveedor, productos, estado
- AFS-047 - Crear tipo PurchaseOrderStatus como enum
- AFS-048 - Crear interfaz PurchaseItem con cantidad y precio
- AFS-049 - Crear interfaz PurchaseAuditEntry
- AFS-050 - Documentar contrato PurchaseOrder y sus componentes

## 📊 Reportes y Métricas

- AFS-051 - Crear interfaz ReportMetric con nombre, valor, unidad
- AFS-052 - Crear tipo ReportPeriod como enum (daily, weekly, monthly)
- AFS-053 - Crear interfaz ChartDataPoint con fecha, valor y etiqueta
- AFS-054 - Crear interfaz KpiMetric con tipo, valor y tendencia
- AFS-055 - Documentar contratos para reportes visuales y exportables

## 📚 Auditoría y Trazabilidad

- AFS-056 - Crear interfaz AuditEntry con usuario, acción, fecha y entidad
- AFS-057 - Crear tipo AuditAction como enum (create, update, delete, login)
- AFS-058 - Crear interfaz ChangeLog con campo, valor anterior y nuevo
- AFS-059 - Crear interfaz EntityAuditTrail para historial completo
- AFS-060 - Documentar contratos de auditoría por entidad (User, Order, Company)

## 🌐 Configuración Regional

- AFS-061 - Crear interfaz LocaleSettings con idioma, moneda, zona horaria
- AFS-062 - Crear tipo CurrencyCode como enum (CLP, USD, EUR)
- AFS-063 - Crear tipo LanguageCode como enum (es, en, pt)
- AFS-064 - Crear interfaz RegionalFormat para fechas y números
- AFS-065 - Documentar contratos de configuración regional por empresa

## 🛡️ Validaciones Compartidas

- AFS-066 - Crear función validateEmail con expresión regular
- AFS-067 - Crear función validateRut con verificación de dígito
- AFS-068 - Crear función validatePhoneNumber con formato internacional
- AFS-069 - Crear función validateRequiredFields para objetos genéricos
- AFS-070 - Crear función validateDateRange con fechas válidas
- AFS-071 - Crear función validateEnumValue para tipos restringidos
- AFS-072 - Documentar validadores con ejemplos y casos límite

## 🔐 Constantes y Enums Técnicos

- AFS-073 - Definir constantes ORDER_STATUS, USER_STATUS, SALE_STATUS
- AFS-074 - Definir constantes PERMISSIONS, ROLES, ENTITY_TYPES
- AFS-075 - Definir constantes CRUD_ACTIONS, AUDIT_ACTIONS, MOVEMENT_TYPES
- AFS-076 - Definir constantes DEFAULT_LOCALE, SUPPORTED_LANGUAGES
- AFS-077 - Definir constantes ERROR_CODES, VALIDATION_MESSAGES
- AFS-078 - Documentar cada constante con su contexto de uso

## 📚 Documentación Técnica

- AFS-079 - Crear README técnico de la librería compartida
- AFS-080 - Documentar estructura de carpetas por dominio (user, order, company)
- AFS-081 - Documentar convenciones de nombres para interfaces, tipos y funciones
- AFS-082 - Documentar estrategia de versionado con semantic-release
- AFS-083 - Configurar changelog automático con commits convencionales
- AFS-084 - Documentar reglas de compatibilidad entre UI y API
- AFS-085 - Crear repositorio inicial del proyecto
- AFS-086 - Documentar estrategia de pruebas unitarias por módulo
- AFS-087 - Documentar ejemplos de uso para cada tipo, función y contrato
- AFS-088 - Documentar contratos críticos por entidad en archivos separados

## ⚙️ Configuración del Proyecto

- AFS-089 - Configurar estructura modular por dominio (user, order, company, etc.)
- AFS-090 - Configurar tsconfig.json con paths y tipos compartidos
- AFS-091 - Configurar eslint con reglas específicas para contratos y utilidades
- AFS-092 - Configurar prettier para formato consistente en todo el repositorio
- AFS-093 - Configurar jest para pruebas unitarias con cobertura por carpeta
- AFS-094 - Configurar vitest o tsup si se requiere bundling optimizado
- AFS-095 - Configurar commitlint y husky para validación de commits convencionales
- AFS-096 - Configurar semantic-release para versionado automático
- AFS-097 - Configurar changelog automático con agrupación por tipo de cambio
- AFS-098 - Configurar package.json con scripts para build, test, lint y release

## 🧪 Pruebas Unitarias y Validación

- AFS-099 - Implementar pruebas unitarias para todos los contratos (User, Order, etc.)
- AFS-100 - Implementar pruebas unitarias para funciones utilitarias (formatDate, validateEmail)
- AFS-101 - Implementar pruebas de consistencia entre enums y tipos
- AFS-102 - Implementar pruebas de compatibilidad entre interfaces extendidas
- AFS-103 - Implementar pruebas de validación cruzada (validateDateRange, validateEnumValue)
- AFS-104 - Configurar reporte de cobertura por módulo funcional
- AFS-105 - Documentar estrategia de pruebas por carpeta (types, utils, contracts)

## 📦 Publicación y Versionado

- AFS-106 - Configurar publicación automática en registro privado (npm, verdaccio, etc.)
- AFS-107 - Configurar etiquetas semánticas (fix, feat, refactor, docs)
- AFS-108 - Configurar control de versiones por contrato (User, Order, etc.)
- AFS-109 - Documentar reglas de compatibilidad entre versiones (breaking, minor, patch)
- AFS-110 - Documentar estrategia de actualización en consumidores (UI, API)
- AFS-111 - Crear script para verificación de contratos rotos (diff-check)
- AFS-112 - Documentar flujo de publicación y revisión por PR

## 📚 Mantenimiento y Escalabilidad

- AFS-113 - Documentar convenciones de nombres para interfaces, tipos y funciones
- AFS-114 - Documentar estructura de carpetas y agrupación por dominio
- AFS-115 - Documentar estrategia de refactorización sin romper contratos
- AFS-116 - Documentar cómo extender contratos sin afectar consumidores
- AFS-117 - Documentar cómo agregar nuevos dominios (finance, notifications, etc.)
- AFS-118 - Documentar cómo sincronizar cambios entre UI y API
- AFS-119 - Documentar cómo versionar tipos compartidos por entorno (dev, prod)
- AFS-120 - Documentar cómo auditar cambios en contratos críticos
- AFS-121 - Crear interfaz Notification con tipo, canal (email, push, in-app) y destinatario.
- AFS-122 - Crear interfaz PromotionRule con condiciones (monto mínimo, fechas, productos aplicables).
- AFS-123 - Crear interfaz DiscountCode con código, tipo (porcentaje, monto fijo) y validez.
- AFS-124 - Crear interfaz Branch con ubicación, inventario y configuraciones regionales.
- AFS-125 - Crear interfaz TaxRule con tasa, región y condiciones de aplicación.
- AFS-126 - Crear interfaz SecurityEvent para registrar intentos de acceso no autorizados o cambios críticos.
- AFS-127 - Documentar manuales de usuario en formato PDF o Markdown para cada módulo funcional.
- AFS-128 - Definir interfaces para manejar contextos multi-tenant en la librería compartida.

## 📄 Nuevas Historias de Usuario

- AFS-129 - Crear CONTRIBUTING.md con reglas de contribución
- AFS-130 - Crear rama develop para trabajar en nuevas funcionalidades
- AFS-131 - Crear flujo de trabajo para validación de cambios en develop
- AFS-138 - Readme técnico de la carpeta libs de la librería compartida

## 🏢 Gestión de tenancy

- AFS-132 – Definir interfaces base de autenticación y autorización para multi-tenancy
- AFS-133 – Definir interfaces base de tenancies
- AFS-134 – Definir interfaz de módulos funcionales
- AFS-135 – Definir tipos auxiliares para contexto y tokens
- AFS-136 – Definir enumeradores base para roles y permisos
- AFS-137 – Definir DTOs de autenticación: LoginRequestDto, LoginResponseDto, JwtPayload
- AFS-139 - Definir enumerador para ciclos de facturación a nivel plataforma.
