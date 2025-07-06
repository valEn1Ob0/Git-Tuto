# Configuraciones Básicas de Git

Aquí se detallan las configuraciones esenciales para empezar a usar Git.

- `--local`: Las configuraciones con parámetros locales aplican únicamente al repositorio actual. Estas configuraciones se almacenan en el archivo `.git/config` dentro del repositorio.
- `--global`: Las configuraciones con parámetros globales aplican para todos los repositorios del usuario actual en el sistema. Se almacenan en el archivo `~/.gitconfig`.
- `--system`: Las configuraciones con parámetros de sistema aplican para todos los usuarios y repositorios del sistema actual. Se almacenan en el archivo `/etc/gitconfig` (o similar, dependiendo del sistema operativo).

```bash
git config --global user.name "Nombre"
```
Establece el nombre de usuario que se asociará a tus commits a nivel global. Es importante configurarlo para identificar quién realizó cada cambio.

```bash
git config --global user.email "tu.email@ejemplo.com"
```
Establece la dirección de correo electrónico que se asociará a tus commits a nivel global. Al igual que el nombre, es crucial para la identificación del autor.

```bash
git config --global core.editor "vim"
```
Define el editor de texto que Git usará cuando necesite que ingreses un mensaje (por ejemplo, para commits sin la opción `-m` o para rebase interactivo). Puedes cambiar `"vim"` por tu editor preferido (como `"code --wait"` para VS Code).

```bash
git config --global core.autocrlf input
```
Configura cómo Git maneja los finales de línea al hacer commit y checkout. `input` es recomendado en sistemas Unix/macOS para evitar problemas de compatibilidad con archivos creados en Windows. En Windows, `git config --global core.autocrlf true` suele ser la opción adecuada.

```bash
git config --global core.abbrev 5
```
Establece la longitud mínima del hash abreviado de los commits que Git mostrará. Un valor de 5 es un ejemplo; Git usará más caracteres si es necesario para asegurar la unicidad del hash.

```bash
git config --global color.ui auto
```
Habilita la salida a color en la terminal para los comandos de Git. Esto mejora la legibilidad del estado, diffs, logs, etc.

```bash
git config --global alias.[nombre-alias] [comando-git]
```
Crea un alias (atajo) para un comando de Git. Por ejemplo, `git config --global alias.co checkout` te permitiría usar `git co` en lugar de `git checkout`.

```bash
git config --global init.defaultBranch main
```
Establece el nombre de la rama principal por defecto (`main` en este caso) al inicializar nuevos repositorios con `git init`. Anteriormente, el nombre por defecto era `master`.

```bash
git config --global pull.rebase true
```
Configura `git pull` para que use `git rebase` en lugar de `git merge` por defecto. Esto ayuda a mantener un historial de commits más lineal y limpio.

```bash
git config --global core.excludesfile ~/.gitignore_global
```
Especifica una ruta a un archivo global de `.gitignore`. Las reglas en este archivo se aplicarán a todos tus repositorios locales, útil para ignorar archivos de sistema operativo o de editor en todos tus proyectos.

```bash
git config --global credential.helper store
```
Configura Git para almacenar tus credenciales (nombre de usuario y contraseña) en disco para evitar tener que ingresarlas repetidamente al interactuar con repositorios remotos (como al hacer `push` o `pull`). Ten en cuenta las implicaciones de seguridad de almacenar credenciales en texto plano.

```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```
Crea un alias `lg` para un formato de `git log` más visual y conciso, mostrando el historial con colores, un gráfico de ramas, hash abreviado, referencia de rama/tag, mensaje del commit, fecha relativa y autor.

```bash
git config --global push.default simple
```
Configura el comportamiento por defecto de `git push`. `simple` es recomendado; solo hace push de la rama actual al remoto que está configurado como upstream, pero solo si los nombres de las ramas coinciden. Esto ayuda a evitar pushes accidentales a otras ramas.

```bash
git config --global core.pager "less -F -X"
```
Configura el paginador utilizado por Git para mostrar salidas largas (como `git log` o `git diff`). `less -F -X` es una configuración común que sale automáticamente si la salida cabe en una pantalla y evita limpiar la pantalla al salir.

```bash
git config --global diff.tool [nombre-herramienta]
```
Configura la herramienta de comparación visual (diff) externa que Git usará. Puedes configurar varias herramientas y seleccionarlas con `git difftool --tool=[nombre-herramienta]`. Ejemplos: `vscode`, `meld`, `kdiff3`.

```bash
git config --global merge.tool [nombre-herramienta]
```
Configura la herramienta de resolución de conflictos de fusión (merge) externa que Git usará. Similar a `diff.tool`, puedes configurar varias y seleccionarlas con `git mergetool --tool=[nombre-herramienta]`. Ejemplos: `vscode`, `meld`, `kdiff3`.

```bash
git config --global commit.gpgsign true
```
Configura Git para firmar automáticamente tus commits con una clave GPG. Esto ayuda a verificar la identidad del autor del commit. Necesitas tener GPG instalado y configurado con una clave.

```bash
git config --global user.signingkey [ID-clave-GPG]
```
Especifica la clave GPG que se utilizará para firmar los commits si `commit.gpgsign` está habilitado.

```bash
git config --global fetch.prune true
```
Configura `git fetch` para que elimine automáticamente las ramas de seguimiento remoto que ya no existen en el repositorio remoto. Esto ayuda a mantener tu lista de ramas remotas limpia y actualizada.

```bash
git config --global rerere.enabled true
```
Habilita `rerere` (reuse recorded resolution). Git recordará cómo resolviste un conflicto de fusión específico y aplicará automáticamente la misma resolución si el mismo conflicto ocurre de nuevo en el futuro. Muy útil si trabajas en ramas de larga duración o con fusiones frecuentes.

```bash
git config --list
```
Muestra todas las configuraciones de Git que están activas para el repositorio actual, incluyendo las configuraciones locales, globales y del sistema. Puedes usar `--local`, `--global` o `--system` para ver solo las configuraciones de un nivel específico.
