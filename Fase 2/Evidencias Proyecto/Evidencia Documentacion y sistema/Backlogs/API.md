# Akira Flex API

## 🔐 Autenticación y Seguridad API

- AFA-001 - Implementar endpoint de login con JWT
- AFA-002 - Implementar endpoint de logout
- AFA-003 - Implementar endpoint de refresh token
- AFA-004 - Configurar guardias de autenticación por permisos
- AFA-005 - Implementar interceptor de auditoría de acciones
- AFA-006 - Configurar CORS y headers de seguridad
- AFA-007 - Implementar validación de token en rutas protegidas
- AFA-008 - Implementar recuperación de contraseña por email
- AFA-009 - Implementar verificación de email al registrar usuario
- AFA-010 - Implementar bloqueo de cuenta tras múltiples intentos fallidos

## 👤 Gestión de Usuarios API

- AFA-011 - Crear endpoint para registrar usuario
- AFA-012 - Crear endpoint para actualizar usuario
- AFA-013 - Crear endpoint para eliminar usuario
- AFA-014 - Crear endpoint para obtener usuario por ID
- AFA-015 - Crear endpoint para listar usuarios con paginación
- AFA-016 - Implementar asignación de roles a usuario
- AFA-017 - Implementar validación de email único
- AFA-018 - Implementar búsqueda de usuarios por filtros
- AFA-019 - Implementar activación/desactivación de usuario
- AFA-020 - Registrar historial de cambios en perfil de usuario

## 🏢 Gestión de Empresas API

- AFA-021 - Crear endpoint para registrar empresa
- AFA-022 - Crear endpoint para actualizar empresa
- AFA-023 - Crear endpoint para eliminar empresa
- AFA-024 - Crear endpoint para obtener empresa por ID
- AFA-025 - Crear endpoint para listar empresas con paginación
- AFA-026 - Implementar validación de RUT/RUN único
- AFA-027 - Implementar búsqueda de empresas por filtros
- AFA-028 - Registrar datos fiscales y comerciales de empresa
- AFA-029 - Asociar empresa a usuarios administradores
- AFA-030 - Registrar logotipo y datos visuales de marca

## 🛂 Roles y Permisos API

- AFA-031 - Crear endpoint para registrar rol
- AFA-032 - Crear endpoint para actualizar rol
- AFA-033 - Crear endpoint para eliminar rol
- AFA-034 - Crear endpoint para listar roles
- AFA-035 - Crear endpoint para registrar permiso
- AFA-036 - Crear endpoint para actualizar permiso
- AFA-037 - Crear endpoint para eliminar permiso
- AFA-038 - Crear endpoint para listar permisos
- AFA-039 - Implementar asignación de permisos a rol
- AFA-040 - Implementar validación de permisos duplicados
- AFA-041 - Registrar historial de cambios en roles y permisos

## 🧾 Gestión Comercial API

- AFA-042 - Crear entidad Product
- AFA-043 - Crear endpoint para registrar producto
- AFA-044 - Crear endpoint para actualizar producto
- AFA-045 - Crear endpoint para eliminar producto
- AFA-046 - Crear endpoint para listar productos con filtros
- AFA-047 - Crear entidad Category
- AFA-048 - Crear endpoint para gestionar categorías de productos
- AFA-049 - Crear entidad Brand
- AFA-050 - Crear endpoint para gestionar marcas de productos
- AFA-051 - Crear entidad InventoryItem
- AFA-052 - Crear endpoint para registrar ingreso de inventario
- AFA-053 - Crear endpoint para registrar salida de inventario
- AFA-054 - Crear endpoint para consultar stock actual por producto
- AFA-055 - Crear entidad Supplier
- AFA-056 - Crear endpoint para gestionar proveedores
- AFA-057 - Crear entidad PurchaseOrder
- AFA-058 - Crear endpoint para registrar orden de compra
- AFA-059 - Crear endpoint para actualizar estado de orden de compra
- AFA-060 - Crear entidad Sale
- AFA-061 - Crear endpoint para registrar venta
- AFA-062 - Crear endpoint para listar ventas por fecha y cliente
- AFA-063 - Crear entidad Payment
- AFA-064 - Crear endpoint para registrar pago asociado a venta
- AFA-065 - Crear entidad Discount
- AFA-066 - Crear endpoint para aplicar descuento a venta o producto
- AFA-067 - Registrar impuestos aplicables por producto o venta
- AFA-068 - Registrar método de pago (efectivo, tarjeta, transferencia)
- AFA-069 - Registrar comprobante de pago o boleta electrónica

## 👥 Gestión de Clientes y Servicios API

- AFA-070 - Crear entidad Customer
- AFA-071 - Crear endpoint para registrar cliente
- AFA-072 - Crear endpoint para actualizar cliente
- AFA-073 - Crear endpoint para eliminar cliente
- AFA-074 - Crear endpoint para buscar cliente por nombre, RUT o teléfono
- AFA-075 - Crear entidad Vehicle (para taller automotriz)
- AFA-076 - Crear endpoint para registrar vehículo de cliente
- AFA-077 - Crear entidad ServiceOrder (orden de servicio)
- AFA-078 - Crear endpoint para registrar orden de servicio
- AFA-079 - Crear endpoint para actualizar estado de orden de servicio
- AFA-080 - Crear endpoint para listar servicios por cliente o vehículo
- AFA-081 - Crear entidad JewelryItem (para joyería)
- AFA-082 - Crear endpoint para registrar pieza de joyería personalizada
- AFA-083 - Crear endpoint para asociar pieza a cliente o venta
- AFA-084 - Registrar historial de servicios realizados por cliente
- AFA-085 - Registrar garantía asociada a producto o servicio

## 💼 Gestión Administrativa API

- AFA-086 - Crear entidad Employee
- AFA-087 - Crear endpoint para registrar empleado
- AFA-088 - Crear endpoint para actualizar datos de empleado
- AFA-089 - Crear endpoint para asignar rol y permisos a empleado
- AFA-090 - Crear entidad Shift
- AFA-091 - Crear endpoint para gestionar turnos de trabajo
- AFA-092 - Crear entidad Expense
- AFA-093 - Crear endpoint para registrar gasto operativo
- AFA-094 - Crear endpoint para listar gastos por categoría y fecha
- AFA-095 - Crear entidad CashRegister
- AFA-096 - Crear endpoint para apertura y cierre de caja
- AFA-097 - Crear endpoint para consultar movimientos de caja
- AFA-098 - Registrar préstamos internos o anticipos a empleados
- AFA-099 - Registrar ausencias y licencias laborales

## 📈 Reportes y Métricas API

- AFA-100 - Crear endpoint para reporte de ventas por día, semana y mes
- AFA-101 - Crear endpoint para reporte de productos más vendidos
- AFA-102 - Crear endpoint para reporte de servicios más solicitados
- AFA-103 - Crear endpoint para reporte de ingresos vs egresos
- AFA-104 - Crear endpoint para reporte de inventario bajo stock mínimo
- AFA-105 - Crear endpoint para reporte de clientes frecuentes
- AFA-106 - Crear endpoint para exportar reportes en formato JSON/CSV
- AFA-107 - Crear endpoint para reporte de desempeño por empleado
- AFA-108 - Crear endpoint para reporte de órdenes de servicio por estado
- AFA-109 - Crear endpoint para reporte de gastos por categoría

## 📦 Configuración Técnica API

- AFA-110 - Configurar entorno .env con variables sensibles
- AFA-111 - Configurar conexión a base de datos PostgreSQL
- AFA-112 - Configurar migraciones con TypeORM
- AFA-113 - Configurar validación global con class-validator
- AFA-114 - Configurar manejo global de errores
- AFA-115 - Configurar interceptores para respuestas estándar
- AFA-116 - Configurar DTOs y pipes para validación de entrada
- AFA-117 - Configurar Swagger para documentación de API
- AFA-118 - Configurar estructura modular de carpetas por dominio
- AFA-119 - Configurar alias de importación con tsconfig-paths
- AFA-120 - Configurar ESLint con reglas específicas para NestJS
- AFA-121 - Configurar Prettier para formato consistente
- AFA-122 - Configurar script de start y build en package.json
- AFA-123 - Instalar librería compartida y agregar carpeta 'definitions'
- AFA-124 - Configurar automatización para entorno de desarrollo
- AFA-125 - Configurar logging estructurado con Winston o Pino
- AFA-126 - Configurar manejo de excepciones con filtros personalizados
- AFA-127 - Configurar rate limiting para endpoints sensibles
- AFA-128 - Configurar compresión y optimización de respuestas HTTP

## 🔁 Integración con Librería Compartida (akira-flex-shared-lib)

- AFA-129 - Integrar interfaces y DTOs desde akira-flex-shared-lib
- AFA-130 - Integrar constantes y enums desde librería compartida
- AFA-131 - Integrar helpers de validación desde librería compartida
- AFA-132 - Validar compatibilidad de rutas y contratos con frontend
- AFA-133 - Configurar sincronización de versiones entre API y librería
- AFA-134 - Documentar dependencias técnicas entre API y librería
- AFA-135 - Implementar pruebas de integración entre API y librería compartida

## 🧪 Pruebas y Calidad API

- AFA-136 - Implementar pruebas unitarias para servicios
- AFA-137 - Implementar pruebas unitarias para controladores
- AFA-138 - Implementar pruebas unitarias para pipes y DTOs
- AFA-139 - Implementar pruebas de integración para endpoints
- AFA-140 - Configurar entorno de testing con base de datos mock
- AFA-141 - Configurar cobertura de código con Jest
- AFA-142 - Validar consistencia entre DTOs y respuestas reales
- AFA-143 - Configurar script de test en package.json
- AFA-144 - Documentar estrategia de testing por módulo funcional
- AFA-145 - Implementar pruebas de seguridad en endpoints protegidos
- AFA-146 - Implementar pruebas de rendimiento para endpoints críticos
- AFA-147 - Implementar pruebas de regresión para flujos comerciales
- AFA-148 - Automatizar ejecución de pruebas en CI/CD

## 📚 Documentación y Versionado API

- AFA-149 - Documentar endpoints en Swagger
- AFA-150 - Documentar estructura de módulos y servicios
- AFA-151 - Documentar convenciones de errores y respuestas
- AFA-152 - Documentar integración con librería compartida
- AFA-153 - Crear README técnico del proyecto
- AFA-154 - Crear CONTRIBUTING.md con reglas de contribución
- AFA-155 - Configurar semantic-release para versionado automático
- AFA-156 - Documentar reglas de SemVer para cambios en API
- AFA-157 - Configurar changelog automático
- AFA-158 - Documentar dependencias externas y configuración de entorno
- AFA-159 - Documentar estrategia de despliegue y rollback
- AFA-160 - Documentar estructura de base de datos y relaciones
- AFA-161 - Documentar convenciones de nombres en entidades y endpoints

## 🌐 Interoperabilidad y Extensibilidad API

- AFA-162 - Crear endpoint para exportar datos en formato JSON
- AFA-163 - Crear endpoint para exportar datos en formato CSV
- AFA-164 - Crear endpoint para importar datos desde archivo CSV
- AFA-165 - Crear endpoint para sincronizar datos con sistemas externos
- AFA-166 - Implementar webhook para eventos de venta y servicio
- AFA-167 - Documentar estructura de payloads para integración externa
- AFA-168 - Configurar compatibilidad con clientes móviles o POS
- AFA-169 - Definir estrategia para módulos plug-and-play en el backend
- AFA-170 - Implementar endpoint para consulta pública de productos o servicios

## 🧩 Mantenimiento y Escalabilidad API

- AFA-171 - Implementar limpieza automática de logs antiguos
- AFA-172 - Implementar archivado de órdenes finalizadas
- AFA-173 - Implementar rotación de tokens y claves sensibles
- AFA-174 - Configurar alertas para errores críticos en producción
- AFA-175 - Documentar estrategia de escalabilidad horizontal
- AFA-176 - Definir límites de paginación y carga por endpoint
- AFA-177 - Implementar cache para consultas frecuentes
- AFA-178 - Configurar backups automáticos de base de datos
- AFA-179 - Documentar estrategia de mantenimiento programado
- AFA-180 - Implementar endpoint para ver estado del sistema (health check)
- AFA-181 - Implementar endpoint para envío de notificaciones automáticas (por ejemplo, para órdenes finalizadas o pagos pendientes).
- AFA-182 - Implementar endpoint para gestionar promociones dinámicas.
- AFA-183 - Implementar endpoints para gestionar sucursales y sus relaciones con empresas.
- AFA-184 - Implementar endpoint para calcular impuestos dinámicamente según ubicación o producto.
- AFA-185 - Implementar integración con Redis o similar para caché distribuido en endpoints críticos (listados de productos, reportes).
- AFA-186 - Configurar invalidación automática de caché tras cambios en entidades (por ejemplo, actualización de stock).
- AFA-187 - Implementar filtros dinámicos con soporte para consultas avanzadas (por ejemplo, filtros combinados en listados de usuarios o ventas).
- AFA-188 - Configurar índices en la base de datos para consultas frecuentes (por ejemplo, búsquedas por cliente o producto).
- AFA-189 - Implementar vistas materializadas para reportes precalculados.
- AFA-190 - Configurar integración con bóvedas seguras (por ejemplo, AWS Secrets Manager o HashiCorp Vault) para gestionar claves sensibles.
- AFA-191 - Implementar rotación automática de claves JWT y tokens de API.
- AFA-192 - Configurar validación automática contra inyecciones SQL en todas las consultas.
- AFA-193 - Configurar protección CSRF en endpoints sensibles (por ejemplo, cambio de contraseña).
- AFA-194 - Implementar endpoint para consultar eventos de seguridad con filtros por usuario o acción.
- AFA-195 - Crear endpoint para sincronizar datos encolados desde modo offline.
- AFA-196 - Implementar integración con al menos una pasarela de pago externa para pagos en línea.
- AFA-197 - Crear endpoints genéricos para exportar/importar datos en formatos compatibles con ERP/CRM.
- AFA-198 - Implementar webhooks para sincronización bidireccional con sistemas externos.
- AFA-199 - Implementar integración con APIs de mensajería (por ejemplo, Twilio o WhatsApp Business API).
- AFA-200 - Implementar pruebas de carga para endpoints críticos (por ejemplo, ventas, reportes).
- AFA-201 - Configurar herramientas como Artillery o JMeter para pruebas de estrés.
- AFA-202 - Configurar suite de pruebas de regresión automatizadas para flujos críticos.
- AFA-203 - Implementar endpoint para inicializar datos predeterminados (por ejemplo, roles iniciales, categorías).
- AFA-204 - Configurar integración con herramientas de monitoreo para métricas de rendimiento y errores.
- AFA-205 - Implementar dashboard de monitoreo interno para administradores.
- AFA-206 - Configurar notificaciones automáticas (por ejemplo, via Slack o email) para errores críticos en producción.
- AFA-207 - Configurar esquema de base de datos multi-tenant con aislamiento por empresa.
- AFA-208 - Implementar endpoints para configurar reglas de negocio específicas por empresa.

## 📄 Nuevas Historias de Usuario API

- AFA-209 - Configuración inicial del proyecto NestJS
- AFA-210 - Configurar commitlint y husky para validación de commits convencionales
- AFA-228 - Implementar servicio de datos iniciales de la plataforma
- AFA-229 - Implementar auditoría de cambios en datos de la plataforma
- AFA-230 - Implementar autenticación a nivel de plataforma administrativa
- AFA-231 - Implementar autorización a nivel de tenant cliente
- AFA-232 - Implementar tenants en la plataforma
- AFA-252 - Implementar servicio de envío de correos electrónicos (SMTP)

## Akira Flex API – Integración con Shared Lib (Tenancy & Auth)

- AFA-211 - Implementar endpoints de autenticación usando DTOs y enums de la shared lib (LoginRequestDto, LoginResponseDto, JwtPayload, AdminRole)
- AFA-212 - Implementar endpoints de gestión de AdminUser usando interfaz de la shared lib
- AFA-213 - Implementar endpoints de gestión de tenants usando interfaz Tenant y CreateTenantDto de la shared lib
- AFA-214 - Implementar endpoints para asignar/quitar módulos funcionales usando TenantModule y ModuleFeature de la shared lib
- AFA-215 - Implementar middleware/interceptor para TenantContext usando tipo de la shared lib
- AFA-216 - Configurar generación y validación de tokens JWT usando TokenOptions de la shared lib
- AFA-217 - Registrar y consultar logs de acceso y acciones de AdminUser usando tipos/enums de la shared lib

## 🧑‍💼 Gestión de Usuarios Plataforma

- AFA-218 - Crear endpoint para registrar usuario administrador
- AFA-219 - Crear endpoint para actualizar usuario administrador
- AFA-220 - Crear endpoint para eliminar usuario administrador
- AFA-221 - Crear endpoint para obtener usuario administrador por ID
- AFA-222 - Crear endpoint para listar usuarios administradores con paginación
- AFA-223 - Crear endpoint para listar roles de plataforma disponibles
- AFA-224 - Implementar asignación de roles de plataforma a usuario
- AFA-225 - Implementar validación de email único en contexto plataforma
- AFA-226 - Implementar búsqueda de usuarios administradores por filtros
- AFA-227 - Implementar activación/desactivación de usuario administrador
- AFA-228 - Registrar historial de cambios en perfil de usuario administrador

## 🧑‍💼 Gestión de Usuarios Propietarios

- AFA-233 - Crear endpoint para registrar usuario propietario
- AFA-234 - Crear endpoint para actualizar usuario propietario
- AFA-235 - Crear endpoint para eliminar usuario propietario
- AFA-236 - Crear endpoint para obtener usuario propietario por ID
- AFA-237 - Crear endpoint para gestionar roles de tenant a usuario propietario
- AFA-238 - Implementar validación de email único en contexto propietario
- AFA-239 - Implementar búsqueda de usuarios propietarios por filtros
- AFA-240 - Implementar activación/desactivación de usuario propietario
- AFA-241 - Registrar historial de cambios en perfil de usuario propietario
- AFA-242 - Registrar usuario propietario con rol inicial owner

## 🏢 Gestión de Empresas Plataforma

- AFA-243 - Limitar creación de empresas por plan de suscripción
- AFA-244 - Crear endpoint para actualizar plan de suscripción de empresa
- AFA-245 - Crear endpoint para obtener plan de suscripción actual
- AFA-246 - Crear endpoint para listar planes de suscripción disponibles
- AFA-247 - Implementar validación de límite de usuarios por plan
- AFA-248 - Crear endpoint para renovar suscripción de empresa
- AFA-249 - Crear endpoint para cancelar suscripción de empresa
- AFA-250 - Implementar webhook para notificaciones de pago y renovación
- AFA-251 - Registrar historial de cambios en plan de suscripción de empresa

## Mejoras y Refactorizaciones

- AFA-253 - Crear interceptor para requests y responses debugging
- AFA-254 - Crear @shared para utilidades comunes antes de exportar a shared-lib
