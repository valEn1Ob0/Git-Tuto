# Comandos Avanzados de Git

Aquí se presentan comandos de Git para operaciones más complejas y manejo del historial.

```bash
git log
```
Muestra el historial de commits del repositorio. Puedes usar varias opciones para formatear la salida (`--oneline`, `--graph`, `--all`, etc.).

```bash
git log --oneline
```
Muestra un resumen conciso del historial de commits, mostrando cada commit en una sola línea con su hash abreviado y el mensaje del commit.

```bash
git diff [commit1] [commit2]
```
Muestra las diferencias en los archivos entre dos commits específicos. Es útil para ver qué cambió entre dos puntos en el historial. Necesitas los hashes de los commits.

```bash
git diff --name-only [commit1] [commit2]
```
Muestra solo los nombres de los archivos que fueron modificados entre dos commits específicos.

```bash
git diff --word-diff [commit1] [commit2]
```
Muestra las diferencias entre dos commits, resaltando los cambios palabra por palabra en lugar de línea por línea.

```bash
git commit --amend
```
Permite modificar el commit más reciente. Puedes añadir cambios que olvidaste incluir o editar el mensaje del commit. Esto reescribe el historial, creando un nuevo hash para el commit.

```bash
git rebase -i head~[commits hacia atras]
```
Inicia una sesión interactiva de rebase para los últimos N commits (donde N es el número de commits hacia atrás). Permite reordenar, editar, combinar (squash) o eliminar commits.

Durante una sesión interactiva de rebase (`git rebase -i`), puedes usar la opción `squash` o `fixup` para combinar varios commits en uno solo. `squash` te permite editar el mensaje del commit resultante, mientras que `fixup` usa el mensaje del commit principal.

```bash
git rebase --continue
```
Continúa el proceso de rebase después de haber resuelto conflictos o completado una acción interactiva (como editar un commit).

```bash
git reset --soft [hash]
```
Mueve el HEAD a un commit específico, pero mantiene los cambios de los commits posteriores en el área de preparación (staging area). El área de trabajo permanece sin cambios.

```bash
git reset --soft head~[commits hacia atras]
```
Mueve el HEAD hacia atrás N commits, manteniendo los cambios de esos commits en el área de preparación. Los cambios que ya estaban en el área de preparación antes del reset se mantienen.

```bash
git reset --mixed [hash]
```
Mueve el HEAD a un commit específico y restablece el área de preparación para que coincida con ese commit, pero mantiene los cambios en el área de trabajo. Este es el modo por defecto de `git reset`.

```bash
git reset --hard [hash]
```
Mueve el HEAD a un commit específico y descarta todos los cambios en el área de preparación y en el área de trabajo. Esto elimina permanentemente los cambios posteriores al commit especificado. ¡Úsalo con extrema precaución!

```bash
git branch
```
Lista todas las ramas locales en el repositorio actual. La rama activa se marca con un asterisco (*).

```bash
git branch [nombre de la rama]
```
Crea una nueva rama con el nombre especificado, apuntando al commit actual. No cambia a la nueva rama.

```bash
git switch [nombre de la rama]
```
Cambia del branch actual al branch especificado. Actualiza los archivos en el área de trabajo para que coincidan con la instantánea del commit al que apunta la rama de destino.

```bash
git switch -c [nombre de la rama]
```
Crea una nueva rama con el nombre especificado y luego cambia automáticamente a esa rama.

```bash
git branch -d [nombre de la rama]
```
Elimina la rama local especificada. Git te impedirá eliminar una rama si tiene cambios sin fusionar, a menos que uses `-D` (mayúscula) para forzar la eliminación.

```bash
git branch -m [nombre de la rama viejo] [nombre de la rama nuevo]
```
Renombra una rama local de un nombre a otro.

```bash
git branch -m [nombre de la rama nuevo]
```
Renombra la rama actual a un nuevo nombre.

```bash
git merge [nombre de la rama]
```
Fusiona los cambios de la rama especificada en la rama actual. Esto crea un nuevo commit de fusión si hay divergencia en el historial.

```bash
git ls-tree -r --name-only [hash]
```
Muestra recursivamente los nombres de todos los archivos y directorios contenidos en un árbol de commit específico.

```bash
git reflog
```
Muestra un registro de todas las acciones recientes en las referencias (HEAD, ramas, tags), incluyendo commits que ya no son referenciados por ninguna rama. Es útil para recuperar commits perdidos.

```bash
git remote add origin [URL]
```
Agrega una nueva conexión a un repositorio remoto. `origin` es el nombre corto convencional para el repositorio remoto principal. [URL] es la dirección del repositorio remoto (HTTP, SSH, etc.).

```bash
git remote show [nombre-remoto]
```
Muestra información detallada sobre un repositorio remoto específico, incluyendo las ramas remotas y su mapeo a las ramas locales.

```bash
git push origin [rama actual]
```
Envía los commits de la rama local actual al repositorio remoto llamado `origin`. Si la rama no existe en el remoto, la crea.

```bash
git push -u origin [rama actual]
```
Envía los commits de la rama local actual al repositorio remoto `origin` y establece la rama remota como upstream de la rama local. Esto permite usar `git pull` y `git push` sin especificar el remoto y la rama en el futuro.

```bash
git push origin --delete [nombre-de-la-rama]
```
Elimina una rama del repositorio remoto especificado.

```bash
git pull
```
Descarga los cambios del repositorio remoto (fetch) y luego los fusiona automáticamente (merge) en la rama local actual.

```bash
git fetch
```
Descarga los objetos y referencias del repositorio remoto al repositorio local. Los cambios se almacenan en ramas remotas (ej: `origin/main`) y no se fusionan automáticamente con tus ramas locales. Debes fusionarlos manualmente después si lo deseas.

```bash
git stash
```
Guarda temporalmente los cambios que tienes en tu área de trabajo y área de preparación sin hacer un commit. Es útil cuando necesitas cambiar de rama rápidamente sin querer confirmar cambios a medio hacer. Puedes aplicar los cambios guardados más tarde con `git stash apply` o `git stash pop`.

```bash
git cherry-pick [hash-commit]
```
Aplica los cambios introducidos por un commit existente de otra rama a tu rama actual. Esto crea un nuevo commit con los mismos cambios pero con un hash diferente.

```bash
git tag [nombre-tag] [hash-commit]
```
Crea una etiqueta (tag) para marcar un punto específico en el historial, generalmente para versiones de lanzamiento (ej: `v1.0`). Puedes etiquetar el commit actual si omites el hash del commit.

```bash
git tag --list
```
Lista todas las etiquetas (tags) en el repositorio.

```bash
git revert [hash-commit]
```
Deshace los cambios introducidos por un commit específico creando un *nuevo* commit que revierte esos cambios. A diferencia de `git reset`, `git revert` no reescribe el historial, lo que lo hace seguro para usar en ramas compartidas.

```bash
git bisect [subcomando]
```
Ayuda a encontrar el commit que introdujo un error mediante una búsqueda binaria automatizada en el historial de commits. Marcas commits como "buenos" o "malos" y Git te guía para encontrar el punto de cambio.

```bash
git clean [opciones]
```
Elimina archivos no rastreados del directorio de trabajo. Es útil para limpiar el directorio de archivos generados o temporales. Usa opciones como `-n` (dry run) para ver qué se eliminaría sin ejecutar la acción, y `-f` para forzar la eliminación.

```bash
git submodule add [URL] [ruta]
```
Agrega un submódulo (otro repositorio Git) como subdirectorio en tu repositorio actual. Es útil para incluir dependencias externas o componentes separados.

```bash
git submodule update
```
Clona los submódulos listados en `.gitmodules` que aún no están clonados y actualiza todos los submódulos registrados para que apunten al commit especificado en el repositorio principal.

```bash
git submodule init
```
Inicializa los submódulos registrados en `.gitmodules`. Esto solo registra los submódulos; necesitas `git submodule update` para clonar y actualizar sus contenidos.

```bash
git merge --abort
```
Aborta un conflicto de fusión en curso y restablece el estado del repositorio al punto anterior a la fusión.

```bash
git reset --hard ORIG_HEAD
```
Deshace una fusión (merge) que ya se ha completado, siempre y cuando no hayas hecho commits posteriores. `ORIG_HEAD` apunta al HEAD antes de la operación de fusión.

```bash
git revert -m 1 [hash-commit-fusion]
```
Deshace un commit de fusión creando un nuevo commit que revierte los cambios introducidos por la fusión. La opción `-m 1` especifica que se revierta a la versión del lado del primer padre (tu rama antes de la fusión). Es la forma recomendada de deshacer fusiones en historiales compartidos.
