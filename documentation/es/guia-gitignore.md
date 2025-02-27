# Guía de .gitignore

## 📝 ¿Qué es .gitignore?

Un archivo `.gitignore` indica a Git qué archivos o carpetas ignorar en un proyecto. Esto es especialmente útil para:
- Archivos de compilación
- Dependencias
- Archivos de configuración local
- Archivos del sistema
- Configuraciones personales del IDE

## 🔧 Sintaxis Básica

### Patrones Comunes
```gitignore
# Ignorar archivo específico
config.json

# Ignorar tipo de archivo
*.log

# Ignorar directorio
node_modules/
build/

# Ignorar archivos en cualquier directorio con este nombre
**/temp/
```

### Patrones Avanzados
```gitignore
# Negar patrón (incluir archivo)
*.log
!importante.log

# Coincidir con un solo carácter
archivo?.txt

# Coincidir con rango de caracteres
[0-9].txt

# Coincidir con cualquier profundidad
**/logs
```

## 📚 Ejemplos Comunes

### Proyecto Node.js
```gitignore
# Dependencias
node_modules/
npm-debug.log
yarn-debug.log
yarn-error.log

# Variables de entorno
.env
.env.local

# Salida de compilación
dist/
build/
```

### Proyecto Python
```gitignore
# Entorno virtual
venv/
env/
*.pyc
__pycache__/

# Distribución
dist/
build/
*.egg-info/
```

### Visual Studio Code
```gitignore
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
```

## 🚀 Mejores Prácticas

1. **Crear Temprano**: Agregar `.gitignore` al inicializar el repositorio
2. **Ser Específico**: Evitar patrones demasiado amplios
3. **Documentar**: Comentar patrones para claridad
4. **Usar Plantillas**: GitHub proporciona plantillas por lenguaje
5. **Mantener Actualizado**: Modificar conforme evoluciona el proyecto

## 🔍 Solución de Problemas

### Archivos ya Rastreados
```bash
# Eliminar archivo rastreado y agregar a .gitignore
git rm --cached nombre-archivo

# Eliminar directorio rastreado
git rm -r --cached directorio/
```

### Verificar Estado de Ignorados
```bash
# Verificar si un archivo está ignorado
git check-ignore -v nombre-archivo

# Listar todos los archivos ignorados
git status --ignored
```

## 📖 Recursos Adicionales
- [Plantillas .gitignore de GitHub](https://github.com/github/gitignore)
- [Documentación de Git sobre .gitignore](https://git-scm.com/docs/gitignore)