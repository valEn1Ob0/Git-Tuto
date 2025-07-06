# Buenas Prácticas en Git

Adoptar buenas prácticas al usar Git es fundamental para mantener un historial de proyecto limpio, facilitar la colaboración en equipo y asegurar la integridad del código. Aquí se detallan algunas recomendaciones clave:

## Configuraciones Iniciales y Archivos Ignorados

1.  **Configurar `user.name` y `user.email`:**
    - **Por qué:** Identifica claramente quién realizó cada commit. Esto es crucial para la trazabilidad y la colaboración, permitiendo saber quién hizo qué cambio y cuándo.
    - **Cómo:** Usa `git config --global user.name "Tu Nombre"` y `git config --global user.email "tu.email@ejemplo.com"`.

2.  **Agregar un archivo `.gitignore`:**
    - **Por qué:** Evita que Git rastree archivos innecesarios o sensibles (como archivos de compilación, logs, dependencias de paquetes, credenciales). Mantener estos archivos fuera del repositorio reduce su tamaño y evita conflictos innecesarios.
    - **Qué hace:** Lista patrones de nombres de archivos y directorios que Git debe ignorar. Puedes tener `.gitignore` a nivel de repositorio y un archivo global de exclusión.

## Commits Significativos y Frecuentes

3.  **Escribir Mensajes de Commit Claros y Descriptivos:**
    - **Por qué:** Un buen mensaje de commit explica *por qué* se hizo un cambio, no solo *qué* cambió. Facilita la revisión del historial, la depuración y la comprensión del proyecto.
    - **Cómo:** Un formato común es una línea de resumen concisa (menos de 50 caracteres) seguida de una línea en blanco y luego un cuerpo más detallado si es necesario. Usa el imperativo en el resumen (ej: "Agregar funcionalidad de login").

4.  **Realizar Commits Pequeños y Frecuentes:**
    - **Por qué:** Cada commit debe representar una unidad lógica de trabajo. Commits pequeños son más fáciles de revisar, revertir o cherry-pick. Hacer commits frecuentes te permite guardar tu trabajo de forma segura y tener puntos de restauración a menudo.
    - **Qué implica:** En lugar de hacer un único commit grande al final del día, haz commits a medida que completas pequeñas tareas o implementas partes de una funcionalidad.

## Gestión de Ramas y Flujos de Trabajo

5.  **Usar Ramas para Nuevas Funcionalidades o Correcciones:**
    - **Por qué:** Las ramas te permiten trabajar en nuevas características o corregir errores de forma aislada de la rama principal (como `main` o `master`). Esto evita inestabilidad en la versión principal del proyecto y facilita el trabajo paralelo.
    - **Qué implica:** Crea una nueva rama para cada tarea (`git switch -c nombre-de-la-rama`), trabaja en ella y fusiónala de vuelta a la rama principal una vez completada y probada.

6.  **Usar `kebab-case` para Nombres de Ramas:**
    - **Por qué:** Es una convención de nomenclatura común y legible para nombres de ramas que contienen múltiples palabras (ej: `feature/nueva-funcionalidad`, `fix/bug-reportado`).
    - **Cómo:** Separa las palabras con guiones bajos (`-`).

7.  **Probar las Ramas Antes de Fusionar a la Rama Principal:**
    - **Por qué:** Asegura que los cambios en una rama sean estables y no introduzcan errores en la rama principal. Esto puede implicar ejecutar pruebas automatizadas o realizar pruebas manuales.
    - **Qué implica:** Antes de fusionar, asegúrate de que la rama esté actualizada con la rama principal (`git pull origin main`) y que todas las pruebas pasen.

8.  **Elegir Estrategias de Fusión Adecuadas:**
    - **Por qué:** La elección entre `merge` (por defecto) y `rebase` afecta la estructura del historial de tu proyecto. `merge` preserva el historial original y crea un commit de fusión, mientras que `rebase` reescribe el historial para crear una línea más lineal.
    - **Qué implica:** Usa `merge` para fusiones simples o cuando trabajas en ramas compartidas donde no quieres reescribir el historial de otros. Usa `rebase` para limpiar tu historial local antes de compartir cambios o para mantener un historial lineal en ramas de características.

9.  **Conocer y Considerar Modelos de Flujo de Trabajo (GitFlow, GitHub Flow):**
    - **Por qué:** Estos modelos proporcionan un conjunto de reglas y recomendaciones sobre cómo usar ramas y fusiones para gestionar proyectos de manera efectiva, especialmente en equipos.
    - **Qué implican:** Definen ramas específicas para desarrollo, lanzamiento, correcciones urgentes, etc., y cómo interactúan entre sí. Elegir un flujo de trabajo ayuda a estandarizar el proceso en un equipo.

## Manejo Avanzado del Historial y Herramientas Útiles

10. **Mantener el Historial Limpio con `rebase` y `squash`:**
    - **Por qué:** Permite combinar múltiples commits pequeños en uno solo (`squash`), reordenar commits, editar mensajes de commits antiguos o eliminar commits. Esto resulta en un historial más conciso y fácil de entender.
    - **Qué implican:** Se realiza con `git rebase -i [commit-ish]`. Úsalo con precaución en ramas que ya han sido compartidas, ya que reescribe el historial.

11. **Usar `git stash` para Guardar Cambios Temporales:**
    - **Por qué:** Te permite guardar rápidamente los cambios en tu área de trabajo y área de preparación cuando necesitas cambiar a otra rama o trabajar en algo urgente sin tener que hacer un commit a medio terminar.
    - **Qué hace:** Guarda tus cambios en una pila de stashes. Puedes recuperarlos más tarde con `git stash apply` o `git stash pop`.

12. **Usar `git cherry-pick` para Seleccionar Commits Individuales:**
    - **Por qué:** Aplica los cambios introducidos por uno o más commits existentes de cualquier rama a tu rama actual. Es útil para traer correcciones específicas de una rama a otra sin fusionar toda la rama.
    - **Qué hace:** Crea un nuevo commit en tu rama actual con los mismos cambios del commit seleccionado.

13. **Usar `git bisect` para Encontrar el Origen de Errores:**
    - **Por qué:** Automatiza la búsqueda binaria en el historial de commits para encontrar el commit exacto que introdujo un error. Es mucho más eficiente que revisar commits manualmente uno por uno.
    - **Qué hace:** Divides tu historial en dos, pruebas un commit intermedio y le dices a Git si el error está presente ("malo") o no ("bueno"). Git repite el proceso hasta encontrar el commit culpable.

14. **Aprovechar `git hooks`:**
    - **Por qué:** Permiten automatizar tareas en diferentes puntos del ciclo de vida de Git (ej: antes de un commit, después de recibir un push). Puedes usarlos para ejecutar linters, pruebas, formateadores de código, etc.
    - **Qué son:** Son scripts personalizados que se encuentran en el directorio `.git/hooks` de tu repositorio.

15. **Considerar el Uso de Submódulos de Git:**
    - **Por qué:** Permiten incluir otro repositorio Git como un subdirectorio dentro de tu repositorio principal. Es útil para gestionar dependencias externas o componentes separados que se desarrollan de forma independiente.
    - **Qué implican:** Requieren comandos adicionales (`git submodule add`, `git submodule update`, `git submodule init`) para clonar y actualizar los contenidos del submódulo.
