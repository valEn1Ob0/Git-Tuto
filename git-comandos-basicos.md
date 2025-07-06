# Comandos Básicos de Git

Aquí se listan los comandos de Git más utilizados para el manejo diario de repositorios.

```bash
git init
```
Inicializa un nuevo repositorio Git en el directorio actual. Esto crea una subcarpeta `.git` que contiene todos los archivos necesarios del repositorio.

```bash
git clone [URL]
```
Clona un repositorio existente desde una URL remota a tu máquina local. Esto descarga una copia completa del repositorio, incluyendo todo el historial de commits.

```bash
git add [archivo]
```
Agrega cambios de un archivo específico al área de preparación (staging area). El área de preparación es donde preparas los cambios antes de confirmarlos. Usa `git add .` para agregar todos los archivos modificados y nuevos en el directorio actual y subdirectorios.

```bash
git restore [archivo]
```
Descarta los cambios locales no guardados en el área de preparación para un archivo específico, revirtiendo el archivo a su estado en el último commit.

```bash
git restore --staged [archivo]
```
Deshace la adición de un archivo al área de preparación, moviendo los cambios de vuelta al área de trabajo sin descartarlos.

```bash
git status
```
Muestra el estado actual del repositorio, incluyendo los archivos modificados, en el área de preparación y sin seguimiento.

```bash
git status -s (o) --short
```
Muestra el estado del repositorio de forma concisa, usando códigos de una o dos letras para indicar el estado de cada archivo.

```bash
git commit -m "mensaje" -a
```
Guarda los cambios del área de preparación en el repositorio con un mensaje descriptivo. La opción `-a` automáticamente prepara (stage) los archivos que ya han sido rastreados antes de hacer el commit.

```bash
git commit
```
Guarda los cambios del área de preparación en el repositorio. Si no se especifica un mensaje con `-m`, se abrirá el editor de texto configurado para que escribas el mensaje del commit.

```bash
git commit -a
```
Prepara automáticamente los archivos rastreados que han sido modificados y luego guarda esos cambios en un nuevo commit. No incluye archivos nuevos no rastreados.

```bash
git restore [archivo]
```
Este comando, dependiendo del contexto, puede descartar cambios en el área de trabajo o restaurar un archivo a partir de un commit anterior. En este caso, se refiere a descartar cambios locales no staged.

```bash
git checkout [archivo]
```
Descarta los cambios locales en el área de trabajo para un archivo específico, revirtiéndolo al estado del último commit. Si el archivo no está en el área de preparación, este comando recupera la versión del archivo del último commit.

```bash
git reset --hard
```
Restablece el estado del repositorio al último commit. Esto descarta todos los cambios en el área de preparación y en el área de trabajo de forma permanente. ¡Úsalo con precaución!

```bash
git mv [archivo1] [archivo2]
```
Mueve o renombra un archivo. Git rastrea este cambio automáticamente y lo prepara para el próximo commit.

```bash
git show [archivo]
```
Muestra información detallada sobre un objeto Git, como un commit, tag o blob. Si se especifica un archivo después de un commit, muestra la versión de ese archivo en ese commit.

```bash
git diff --staged
```
Muestra las diferencias entre el área de preparación y el último commit. Esto te permite revisar los cambios que has preparado antes de confirmarlos.
