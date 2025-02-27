# Git Básico

## 🌟 Conceptos Fundamentales

### ¿Qué es Git?
Git es un sistema de control de versiones distribuido que rastrea cambios en tu código a lo largo del tiempo.

### Los Tres Estados de Git
1. **Directorio de Trabajo**: Donde modificas archivos
2. **Área de Preparación**: Donde preparas cambios para confirmar
3. **Repositorio Git**: Donde Git almacena el historial de commits

## 📝 Comandos Esenciales

### Configuración de Git
```bash
# Configurar tu identidad
git config --global user.name "Tu Nombre"
git config --global user.email "tu.correo@ejemplo.com"

# Configurar saltos de línea (Unix)
git config --global core.autocrlf input
```

### Operaciones Básicas
```bash
# Inicializar repositorio
git init

# Verificar estado
git status
git status -s  # Formato corto

# Agregar archivos al área de preparación
git add <archivo>    # Un archivo
git add .            # Todos los archivos

# Confirmar cambios
git commit -m "Mensaje descriptivo"
git commit -a -m "Agregar y confirmar en un paso"

# Ver historial
git log
git log --oneline  # Vista compacta
```

### Trabajar con Repositorios Remotos
```bash
# Clonar repositorio
git clone <url>

# Agregar repositorio remoto
git remote add origin <url>

# Subir cambios
git push origin main

# Obtener actualizaciones
git pull origin main
```

## 🔄 Ejemplo de Flujo de Trabajo

```bash
# Crear nueva característica
git checkout -b nombre-caracteristica

# Realizar cambios y rastrearlos
git add .
git commit -m "Agregar nueva característica"

# Subir a remoto
git push origin nombre-caracteristica
```

## ⚠️ Problemas Comunes y Soluciones

### 1. Deshacer Cambios
```bash
# Descartar cambios en directorio de trabajo
git restore <archivo>

# Quitar archivos del área de preparación
git restore --staged <archivo>

# Modificar último commit
git commit --amend
```

### 2. Operaciones con Archivos
```bash
# Renombrar archivos
git mv nombre-antiguo nombre-nuevo

# Eliminar archivos
git rm nombre-archivo
```

## 📚 Siguientes Pasos
- Aprende sobre [estrategias de ramificación](flujos-de-trabajo-equipo.md)
- Explora [características avanzadas de Git](git-avanzado.md)
- Domina [patrones .gitignore](guia-gitignore.md)