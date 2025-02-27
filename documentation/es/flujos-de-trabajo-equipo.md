# Flujos de Trabajo en Equipo con Git

## 📊 Modelos de Flujo de Trabajo Comunes

### 1. Git Flow
Un flujo de trabajo robusto para proyectos grandes:

```bash
# Crear rama de característica
git switch -c feature/nueva-caracteristica develop

# Después de completar la característica
git switch develop
git merge feature/nueva-caracteristica
git branch -d feature/nueva-caracteristica

# Crear release
git switch -c release/1.0.0 develop
```

### 2. Flujo de GitHub
Flujo más simple enfocado en entrega continua:

```bash
# Crear rama de característica
git switch -c nombre-caracteristica main

# Subir cambios regularmente
git push -u origin nombre-caracteristica

# Crear Pull Request vía GitHub
# Después de revisión y aprobación, fusionar vía interfaz de GitHub
```

## 🤝 Mejores Prácticas de Colaboración

### Pull Requests
```bash
# Crear rama lista para PR
git switch -c feature/auth-usuarios
git push -u origin feature/auth-usuarios

# Actualizar PR con cambios de main
git switch feature/auth-usuarios
git fetch origin
git rebase origin/main
git push --force-with-lease
```

### Guías para Revisión de Código
- Mantener cambios pequeños y enfocados
- Usar mensajes de commit significativos
- Responder a todos los comentarios de revisión
- Actualizar rama con main regularmente

## 🔄 Gestión de Ramas

### Ramas Protegidas
```bash
# Reglas de protección para rama principal
- Requerir revisiones de pull request
- Requerir verificaciones de estado
- No permitir push directo
```

### Convención de Nombres para Ramas
```
feature/    # Nuevas características
bugfix/     # Corrección de errores
hotfix/     # Correcciones urgentes
release/    # Ramas de lanzamiento
docs/       # Actualizaciones de documentación
```

## 👥 Ejemplos de Colaboración en Equipo

### Desarrollo de Características
```bash
# Iniciar nueva característica
git switch -c feature/sistema-pagos
git push -u origin feature/sistema-pagos

# Colaborar con miembro del equipo
git fetch origin
git rebase origin/feature/sistema-pagos

# Crear PR cuando esté listo
git push origin feature/sistema-pagos
```

## 🔒 Seguridad y Control de Acceso

### Claves SSH
```bash
# Generar clave SSH
ssh-keygen -t ed25519 -C "tu@correo.com"

# Agregar a cuenta GitHub
cat ~/.ssh/id_ed25519.pub
# Copiar salida a claves SSH de GitHub
```

### Firma GPG
```bash
# Configurar firma GPG
git config --global commit.gpgsign true
git config --global user.signingkey TU_ID_CLAVE
```

## 📈 Integración con Gestión de Proyectos

### Seguimiento de Issues
```bash
# Rama para issue específico
git switch -c feature/issue-123

# Mensaje de commit con referencia al issue
git commit -m "Implementar formulario login #123"
```

## 🚀 Integración CI/CD

### Ejemplo de GitHub Actions
```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm test
```

## 📝 Estándares de Documentación

### Mensajes de Commit
```
tipo(alcance): descripción

- feat: Nueva característica
- fix: Corrección de error
- docs: Documentación
- style: Formato
- refactor: Reestructuración de código
```