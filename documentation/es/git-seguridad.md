# Mejores Prácticas de Seguridad en Git

## 🔒 Autenticación y Acceso

### Claves SSH
```bash
# Generar nueva clave SSH
ssh-keygen -t ed25519 -C "tu.correo@ejemplo.com"

# Añadir clave al agente ssh
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copiar clave pública (añadir a GitHub/GitLab)
cat ~/.ssh/id_ed25519.pub
```

### Autenticación de Dos Factores
1. Habilitar 2FA en tu servicio de alojamiento Git
2. Configurar aplicación de autenticación
3. Guardar códigos de respaldo de forma segura
4. Actualizar credenciales Git localmente

## 🛡️ Seguridad del Repositorio

### Protección de Datos Sensibles
```bash
# Eliminar archivo sensible y su historial
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch RUTA_AL_ARCHIVO" \
  --prune-empty --tag-name-filter cat -- --all

# Usar .gitignore para archivos sensibles
echo "secretos.json" >> .gitignore
echo "*.key" >> .gitignore
```

### Firma de Commits
```bash
# Configurar clave GPG
git config --global user.signingkey TU_ID_CLAVE_GPG
git config --global commit.gpgsign true

# Firmar commits
git commit -S -m "Mensaje de commit firmado"

# Verificar firmas
git verify-commit HEAD
```

## 🔐 Gestión de Secretos

### Uso de Variables de Entorno
```bash
# Almacenar credenciales en el entorno
export API_KEY="tu-clave-api"

# Usar en scripts
api_key = os.getenv('API_KEY')
```

### Herramienta Git-Secret
```bash
# Inicializar git-secret
git secret init

# Añadir clave pública del usuario
git secret tell usuario@correo.com

# Ocultar archivo sensible
git secret hide

# Revelar cuando sea necesario
git secret reveal
```

## 🚫 Control de Acceso

### Reglas de Protección de Ramas
1. Requerir revisiones de pull request
2. Forzar commits firmados
3. Requerir verificaciones de estado
4. Restringir pushes forzados

### Configuración del Repositorio
1. Activar alertas de vulnerabilidades
2. Configurar actualizaciones de dependencias
3. Configurar escaneo de código
4. Habilitar escaneo de secretos

## 📝 Políticas de Seguridad

### Archivo de Política de Seguridad
```markdown
# SECURITY.md
## Reportar Problemas de Seguridad
## Versiones Soportadas
## Proceso de Actualización de Seguridad
## Mejores Prácticas de Seguridad
```

### Código de Conducta
```markdown
# CODE_OF_CONDUCT.md
## Nuestros Estándares
## Aplicación
## Alcance
## Información de Contacto
```

## 🔍 Auditoría de Seguridad

### Auditoría del Repositorio
```bash
# Buscar secretos en el historial
git log -p | grep -i "contraseña\|secreto\|clave"

# Revisar archivos grandes
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort -rn -k2 |
  head -10
```

### Auditoría de Dependencias
```bash
# Auditoría NPM
npm audit

# Dependencias Python
pip list --outdated
```

## ⚡ Lista de Verificación de Seguridad

1. [ ] Usar claves SSH para autenticación
2. [ ] Habilitar 2FA
3. [ ] Firmar commits con GPG
4. [ ] Configurar protección de ramas
5. [ ] Revisar .gitignore
6. [ ] Auditar secretos
7. [ ] Mantener dependencias actualizadas
8. [ ] Usar variables de entorno
9. [ ] Implementar política de seguridad
10. [ ] Auditorías regulares de seguridad

## 🚀 Guía de Implementación

1. Configuración del Repositorio
   ```bash
   # Inicializar repositorio seguro
   git init
   git config --global user.signingkey TU_CLAVE_GPG
   git config --global commit.gpgsign true
   ```

2. Flujo de Trabajo Diario
   ```bash
   # Antes de hacer commit
   git secrets --scan
   git diff --staged

   # Commit seguro
   git commit -S -m "Mensaje de commit seguro"
   ```

3. Mantenimiento Regular
   ```bash
   # Actualizar dependencias
   npm audit fix
   
   # Verificar secretos expuestos
   git-secrets --scan-history
   ``` 