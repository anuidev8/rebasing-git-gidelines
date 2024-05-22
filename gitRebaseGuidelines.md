# Guía: Rebasar una Rama de Funcionalidad antes de Fusionar en la Rama de Desarrollo

## Objetivo

Mantener un historial limpio y lineal en la rama de desarrollo al incorporar cambios de una rama de funcionalidad.

## Pasos

1. **Actualizar la rama de desarrollo:**

   - Cambiar a la rama de desarrollo:
     ```
     git checkout desarrollo
     ```
   - Obtener los últimos cambios de la rama de desarrollo remota:
     ```
     git pull origin desarrollo
     ```

2. **Cambiar a la rama de funcionalidad:**

   - Cambiar a la rama de funcionalidad (por ejemplo, funcionalidad/agregar-busqueda):
     ```
     git checkout funcionalidad/agregar-busqueda
     ```

3. **Rebasar la rama de funcionalidad sobre la rama de desarrollo:**

   - Ejecutar el comando de rebase:
     ```
     git rebase desarrollo
     ```
     Git comenzará a aplicar los commits de la rama de funcionalidad sobre el último commit de la rama de desarrollo.

4. **Resolver conflictos (si los hay):**

   - Si hay conflictos durante el proceso de rebase, Git se pausará y te pedirá que los resuelvas.
   - Abre los archivos conflictivos y realiza los cambios necesarios para resolver los conflictos.
   - Añade los archivos resueltos al área de preparación (stage) usando `git add`.
   - Continúa el proceso de rebase ejecutando:
     ```
     git rebase --continue
     ```
   - Repite este paso para cada commit que tenga conflictos.

5. **Forzar el push de la rama de funcionalidad rebasada:**

   - Una vez que el rebase se haya completado, la rama de funcionalidad estará actualizada con los últimos cambios de la rama de desarrollo.
   - Fuerza el push de la rama de funcionalidad rebasada al repositorio remoto:
     ```
     git push -f origin funcionalidad/agregar-busqueda
     ```
     Recuerda usar la bandera `-f` para forzar el push, ya que el historial de commits de la rama de funcionalidad ha sido reescrito.

6. **Crear un pull request:**
   - Crea un pull request desde la rama de funcionalidad (`funcionalidad/agregar-busqueda`) hacia la rama de desarrollo.
   - Revisa los cambios y asegúrate de que todo esté en orden.
   - Fusiona el pull request en la rama de desarrollo.

## Ejemplo

Supongamos que tienes una rama de funcionalidad llamada `funcionalidad/agregar-busqueda` con los siguientes commits:

- (funcionalidad/agregar-busqueda) Commit 3: Mejoras en la búsqueda
- (funcionalidad/agregar-busqueda) Commit 2: Implementación inicial de la búsqueda
- (funcionalidad/agregar-busqueda) Commit 1: Configuración inicial

Mientras tanto, la rama de desarrollo tiene nuevos commits realizados por otros miembros del equipo:

- (desarrollo) Commit F: Corrección de errores
- (desarrollo) Commit E: Nueva funcionalidad

Después de rebasar la rama de funcionalidad sobre la rama de desarrollo, el historial se verá así:

- (funcionalidad/agregar-busqueda) Commit 3': Mejoras en la búsqueda
- (funcionalidad/agregar-busqueda) Commit 2': Implementación inicial de la búsqueda
- (funcionalidad/agregar-busqueda) Commit 1': Configuración inicial
- (desarrollo) Commit F: Corrección de errores
- (desarrollo) Commit E: Nueva funcionalidad

Ahora puedes fusionar la rama de funcionalidad rebasada en la rama de desarrollo mediante un pull request, manteniendo un historial lineal y claro.
