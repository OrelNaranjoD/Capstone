# 🧭 Guía de flujo de trabajo y publicación

Esta guía describe cómo colaborar en el repositorio de forma ordenada, sin crear ramas por tarea, utilizando commits semánticos en inglés y controlando las publicaciones desde la rama main.

## 🔧 Estructura de ramas

- **develop**: rama de trabajo compartida. Aquí se realizan todos los commits y se integran las tareas.
- **main**: rama protegida. Solo se actualiza mediante merge desde develop y se utiliza para publicar nuevas versiones.

## 🔁 Flujo operativo

### 1. Trabajo diario en develop

- Todo el equipo trabaja directamente sobre la rama develop.
- Cada commit debe seguir la convención semántica en inglés, incluyendo el identificador de la tarea (por ejemplo, AFS-101).
- Ejemplos válidos:
  - `feat(AFS-101): add user DTO`
  - `fix(AFS-102): validate email format`
  - `refactor(AFS-103): simplify response handler`
- No se crean ramas por tarea. El seguimiento se realiza desde el tablero Kanban y se refleja en los commits.

### 2. Publicación de una nueva versión

- Cuando se decide publicar una versión estable:
  - Se realiza un merge manual de develop hacia main.
  - Se ejecuta el workflow Publish mediante workflow_dispatch.
  - Se selecciona el tipo de versión a publicar:
    - **patch**: para correcciones menores o ajustes internos
    - **minor**: para nuevas funcionalidades sin romper compatibilidad
    - **major**: para cambios que rompen la API o el comportamiento esperado

### 3. Manejo de errores o rollback

- Si la versión publicada presenta problemas:
  - Se corrige el error directamente en develop.
  - Se vuelve a hacer merge desde develop hacia main.
  - Se ejecuta nuevamente el workflow, esta vez con un tipo de versión mayor (minor o major) para forzar una nueva publicación y evitar conflictos con el tag anterior.

  - Requiere revisión antes de hacer merge.
  - Solo se actualiza mediante PR desde develop.
- Mantén sincronizadas las ramas:
  - Después de cada publicación, asegúrate de que develop incluya los cambios de main.
- Usa `npm run changelog` antes de publicar:

---

```sh
# Cambiar a la rama develop
git checkout develop

# Actualizar develop con los últimos cambios remotos
git pull origin develop

# Agregar todos los cambios y hacer commit semántico
git add .
git commit -m "feat(AFS-101): add user DTO"

# Subir los cambios a develop
git push origin develop

# Hacer merge manual de develop a main para publicar
git checkout main
git pull origin main
git merge develop

# Subir los cambios a main
git push origin main

# Volver a develop y sincronizar con main si es necesario
git checkout develop
git pull origin main

# Ver el historial de commits
git log --oneline --decorate --graph --all
```
