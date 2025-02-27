# Hooks y Automatización en Git

## 🎣 Entendiendo los Git Hooks

Los Git hooks son scripts que Git ejecuta antes o después de eventos como: commit, push y receive.

## 📂 Ubicación de los Hooks

```bash
# Directorio de hooks locales
.git/hooks/

# Hooks compartidos del proyecto
.git-templates/hooks/
```

## 🔄 Hooks Disponibles

### Hooks Pre-Commit
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Ejecutar linter
npm run lint

# Ejecutar pruebas
npm test

# Verificar declaraciones de depuración
if grep -r "debugger\|console.log" ./src/; then
  echo "Error: Se encontraron declaraciones de depuración"
  exit 1
fi
```

### Hooks Commit-Msg
```bash
#!/bin/sh
# .git/hooks/commit-msg

# Forzar commits convencionales
commit_msg=$(cat "$1")
if ! echo "$commit_msg" | grep -qE "^(feat|fix|docs|style|refactor|test|chore):"; then
  echo "Error: El mensaje debe seguir el formato de commits convencionales"
  exit 1
fi
```

### Hooks Pre-Push
```bash
#!/bin/sh
# .git/hooks/pre-push

# Ejecutar suite completa de pruebas
npm run test:full

# Verificar build
npm run build
```

## 🛠️ Casos de Uso Comunes

### Verificaciones de Calidad de Código
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Verificar formato de código
prettier --check "src/**/*.{js,ts,jsx,tsx}"

# Ejecutar ESLint
eslint "src/**/*.{js,ts,jsx,tsx}"

# Verificar tipos de TypeScript
tsc --noEmit
```

### Verificaciones de Seguridad
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Verificar secretos
git secrets --scan

# Ejecutar auditoría de seguridad
npm audit

# Verificar dependencias
snyk test
```

### Pruebas Automatizadas
```bash
#!/bin/sh
# .git/hooks/pre-push

# Ejecutar pruebas unitarias
jest

# Ejecutar pruebas de integración
cypress run

# Verificar cobertura
jest --coverage --coverageThreshold='{"global":{"branches":80}}'
```

## 📦 Configuración de Hooks para Todo el Proyecto

### Usando Plantillas Git
```bash
# Crear directorio de plantillas
git config --global init.templateDir '~/.git-templates'
mkdir -p ~/.git-templates/hooks

# Añadir hooks a la plantilla
cp pre-commit ~/.git-templates/hooks/
chmod +x ~/.git-templates/hooks/pre-commit

# Inicializar nuevo repositorio con plantillas
git init
```

### Usando Husky (Node.js)
```bash
# Instalar husky
npm install husky --save-dev

# Configurar package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "npm test",
      "pre-push": "npm run build"
    }
  }
}
```

## 🔧 Técnicas Avanzadas de Hooks

### Saltar Hooks
```bash
# Saltar hooks pre-commit
git commit --no-verify -m "Corrección de emergencia"

# Saltar hooks pre-push
git push --no-verify
```

### Compartir Hooks con el Equipo
```bash
# Crear directorio de hooks en el proyecto
mkdir .hooks

# Configurar Git para usar ruta personalizada de hooks
git config core.hooksPath .hooks

# Añadir hooks al control de versiones
git add .hooks
```

## 📝 Mejores Prácticas

1. Mantener hooks rápidos y enfocados
2. Proporcionar mecanismos para saltarlos en emergencias
3. Documentar requisitos de los hooks
4. Versionar hooks compartidos
5. Usar códigos de salida apropiados

## 🚀 Ejemplos de Implementación

### Hook para Commits Convencionales
```bash
#!/bin/sh
# .git/hooks/commit-msg

commit_msg_file=$1
commit_msg=$(cat "$commit_msg_file")

# Patrón de commit convencional
pattern="^(feat|fix|docs|style|refactor|test|chore)(\(.+\))?: .{1,50}"

if ! echo "$commit_msg" | grep -qE "$pattern"; then
  echo "Error: Formato de mensaje de commit inválido."
  echo "Debe seguir: tipo(alcance): mensaje"
  echo "Tipos: feat, fix, docs, style, refactor, test, chore"
  exit 1
fi
```

### Hook de Calidad de Código
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Obtener archivos preparados
files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.jsx\?$')

# Salir si no hay archivos JS
[ -z "$files" ] && exit 0

# Ejecutar prettier
echo "$files" | xargs prettier --write

# Ejecutar eslint
echo "$files" | xargs eslint --fix

# Volver a añadir los archivos modificados
echo "$files" | xargs git add

exit 0
```

### Hook para Nombres de Rama
```bash
#!/bin/sh
# .git/hooks/pre-commit

branch_name=$(git symbolic-ref --short HEAD)
valid_pattern="^(feature|bugfix|hotfix|release)/.+"

if ! echo "$branch_name" | grep -qE "$valid_pattern"; then
  echo "Error: Nombre de rama inválido"
  echo "Debe seguir: tipo/descripcion"
  echo "Tipos: feature, bugfix, hotfix, release"
  exit 1
fi
``` 