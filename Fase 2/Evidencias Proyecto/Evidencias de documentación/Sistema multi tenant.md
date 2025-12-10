# 🧩 Visión general del sistema

- Arquitectura multi-tenant con PostgreSQL y NestJS.

## Estructura del sistema

El sistema está dividido en dos niveles bien separados:

### 1. Nivel Plataforma (Schema public)

- Es el núcleo administrativo del sistema.
- Aquí se gestionan los tenants (empresas), usuarios administradores, configuración global, planes, auditoría, etc.
- Solo accesible por usuarios con rol de administrador.
- No contiene datos operativos de ninguna empresa.

### 2. Nivel Tenant (Schemas tenant_{id})

- Cada empresa tiene su propio schema aislado.
- Contiene sus propias tablas: usuarios internos, productos, ventas, etc.
- No tiene acceso a otros schemas ni puede crear nuevos.
- Toda la lógica de negocio se ejecuta dentro de su propio contexto.

## ⚙️ Flujo de trabajo

- Onboarding de empresa
- El administrador crea un nuevo tenant desde el panel o API.
- El sistema genera un nuevo schema (tenant_acme) y aplica migraciones.
- Se registra el tenant en la tabla global tenants.
- Acceso por empresa
- Cada request incluye un identificador de tenant (por header, token o subdominio).
- El sistema resuelve el schema correspondiente y enruta la operación allí.
- Las empresas operan exclusivamente dentro de su propio schema.
- Separación total de datos
- Los datos del administrador y de las empresas nunca se mezclan.
- Cada schema tiene sus propias tablas, aunque compartan estructura.
- Las migraciones y validaciones se aplican por separado.

## 🛡️ Seguridad y escalabilidad

- Guards y roles aseguran que cada usuario acceda solo a su nivel (plataforma o tenant).
- El sistema puede escalar horizontalmente, ya que cada schema es autónomo.
- La arquitectura permite migrar fácilmente a microservicios si se requiere en el futuro.

## 📚 Documentación recomendada

- Guía de creación de tenants
- Estructura de schemas y entidades
- Flujo de acceso por rol
- Estrategia de migraciones por nivel
- Validaciones y pruebas por contexto
