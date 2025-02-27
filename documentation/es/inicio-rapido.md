# Guía Rápida de Git

## Requisitos Previos
- Git instalado en tu sistema
- Conocimientos básicos de línea de comandos
- Editor de texto (VS Code recomendado)

## 🔧 Configuración Inicial

### 1. Configurar Git
```bash
# Configura tu identidad
git config --global user.name "Tu Nombre"
git config --global user.email "tu.correo@ejemplo.com"

# Configura el editor predeterminado (VS Code)
git config --global core.editor "code --wait"

# Configura los finales de línea
# Para Unix/Linux:
git config --global core.autocrlf input
# Para Windows:
git config --global core.autocrlf true
```

### 2. Iniciar un Proyecto

#### Crear un Nuevo Repositorio
```bash
# Inicializar un nuevo repositorio
git init mi-proyecto
cd mi-proyecto

# Crear archivos iniciales
echo "# Mi Proyecto" > README.md
```

#### Clonar un Repositorio Existente
```bash
git clone https://github.com/usuario/repositorio.git
```

### 3. Flujo de Trabajo Básico

```bash
# Verificar estado
git status

# Agregar archivos
git add README.md    # Un archivo
git add .            # Todos los archivos

# Confirmar cambios
git commit -m "Commit inicial"

# Subir a remoto (si usas GitHub)
git push origin main
```

## 📚 Siguientes Pasos
- Continúa con [Git Básico](git-basico.md)
- Aprende sobre [.gitignore](guia-gitignore.md)
- Explora [Flujos de Trabajo en Equipo](flujos-de-trabajo-equipo.md)

## 🆘 Problemas Comunes
- [Permiso denegado (publickey)](https://docs.github.com/es/authentication/troubleshooting-ssh)
- [Git no reconocido como comando](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Instalación-de-Git)