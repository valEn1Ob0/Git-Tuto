# Git Básico

## 📋 Tabla de Contenidos
1. [Conceptos Fundamentales](#conceptos-fundamentales)
2. [Comandos Esenciales](#comandos-esenciales)
3. [Trabajar con Repositorios Remotos](#trabajar-con-repositorios-remotos)
4. [Ejemplo de Flujo de Trabajo](#ejemplo-de-flujo-de-trabajo)
5. [Comandos Modernos de Git](#comandos-modernos-de-git)
6. [Manejo de Conflictos](#manejo-de-conflictos)
7. [Problemas Comunes y Soluciones](#problemas-comunes-y-soluciones)
8. [Siguientes Pasos](#siguientes-pasos)

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

## 🔄 Comandos Modernos de Git

### Switch y Restore (Git 2.23+)
```bash
# Cambiar ramas (reemplaza git checkout)
git switch main
git switch -c nueva-caracteristica  # Crear y cambiar

# Restaurar archivos (reemplaza git checkout -- <archivo>)
git restore <archivo>  # Descartar cambios en directorio de trabajo
git restore --staged <archivo>  # Quitar archivos del área de preparación
git restore --source=HEAD~1 <archivo>  # Restaurar desde commit específico
```

## 🔀 Manejo de Conflictos

### Entendiendo los Conflictos
Cuando Git no puede fusionar cambios automáticamente, verás:
- `<<<<<<<` HEAD (cambios actuales)
- `=======` divisor
- `>>>>>>>` nombre-rama (cambios entrantes)

### Resolviendo Conflictos
```bash
# 1. Identificar archivos con conflictos
git status

# 2. Abrir y editar archivos con conflictos
# Eliminar marcadores de conflicto y mantener cambios deseados

# 3. Marcar como resuelto
git add <archivo-resuelto>

# 4. Completar la fusión
git commit -m "Resolver conflictos de fusión"
```

### Prevenir Conflictos
```bash
# Actualizar tu rama antes de hacer cambios
git pull origin main

# Verificar conflictos potenciales antes de fusionar
git fetch origin
git diff main origin/main
```

### Abortar una Fusión
```bash
# Si quieres empezar de nuevo
git merge --abort
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
- Practica [resolución de conflictos](git-conflictos.md)