# Tablero Kanban – AkiraFlex

> Este tablero organiza entregables técnicos del proyecto AkiraFlex (arquitectura, desarrollo y documentación). Está pensado para gestión ágil con foco en modularidad y trazabilidad.

## Estructura del tablero

- Backlog: ideas y funcionalidades futuras aún no priorizadas.
- To Do: tareas listas para comenzar, agrupadas por dominio.
- In Progress: tareas en desarrollo.
- Blocked: tareas pausadas por dependencias o problemas.
- QA: tareas pendientes de validación o pruebas.
- Done: tareas completadas y validadas.
- Parking Lot: funcionalidades diferidas o fuera del alcance del MVP.

## Etiquetas técnicas

- Gateway: integraciones entre módulos o servicios externos.
- DB: modelado, consultas y reglas en base de datos.
- API: endpoints, controladores y lógica de negocio.
- UI: interfaces de usuario y experiencia visual.
- Core: lógica central reutilizable del sistema.
- Test: pruebas unitarias, de integración o funcionales.
- Docs: documentación técnica, arquitectónica y funcional.

## Reglas de flujo

### Por hacer (To Do)

- Máximo 3 tareas por dominio.
- Límite total del tablero: 9 tareas.
- Las tareas deben estar bien definidas y listas para ejecutarse.

### En progreso (In Progress)

- Máximo 2–3 tareas por desarrollador.
- Máximo 5–6 tareas activas en total.
- Las tareas bloqueadas deben moverse a la lista Blocked.

### QA

- Las tareas deben incluir criterios de prueba o validación.
- Revisión por pares o autoevaluación antes de pasar a Done.

## Convenciones de nombres

- Títulos y descripciones de tareas en inglés.
- Nombres claros y orientados a acción (ej.: "Create role table", "Implement RLS for tenant isolation").
- Evitar títulos vagos como "Fix bug" o "Update stuff".

## Notas adicionales

- El tablero refleja entregables técnicos reales de AkiraFlex.
- Las tareas siguen principios SOLID y están diseñadas de forma modular.
- La documentación técnica se incluye en cada repositorio por separado.
- Cada tarea debe estar vinculada a su respectivo commit en Git.

## Actualizaciones

- Este documento se actualiza conforme evoluciona el tablero.
- Para decisiones arquitectónicas y criterios del proyecto, revisar la nota fija de criterios metodológicos.
