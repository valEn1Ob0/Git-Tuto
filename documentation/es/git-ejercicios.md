# Ejercicios Interactivos y Resolución de Problemas en Git

## 🎯 Ejercicios Básicos

### Ejercicio 1: Configuración Inicial
```bash
# Crear nuevo directorio e inicializarlo
mkdir practica-git
cd practica-git
git init

# Tarea 1: Configurar tu identidad
# Solución:
git config --global user.name "Tu Nombre"
git config --global user.email "tu.correo@ejemplo.com"

# Verificar:
git config --get user.name
git config --get user.email
```

### Ejercicio 2: Flujo de Trabajo Básico
```bash
# Tarea: Crear y rastrear un nuevo archivo
echo "# Mi Proyecto" > README.md
git status  # Verificar estado
git add README.md
git commit -m "Commit inicial"

# Verificar:
git log --oneline
```

### Ejercicio 3: Ramificación
```bash
# Tarea: Crear y cambiar entre ramas
git switch -c caracteristica-1
echo "Nueva característica" >> README.md
git add README.md
git commit -m "Agregar nueva característica"

# Volver a main
git switch main

# Verificar:
git branch --list
```

## 🔍 Escenarios de Resolución de Problemas

### Escenario 1: Commit Accidental
```bash
# Problema: Commit en rama equivocada
git log --oneline  # Notar el hash del commit
git switch -c rama-correcta
git cherry-pick <hash-commit>
git switch rama-anterior
git reset --hard HEAD~1

# Verificar:
git log --all --graph --oneline
```

### Escenario 2: Cambios Perdidos
```bash
# Problema: Cambios no confirmados perdidos
git reflog  # Encontrar último estado bueno conocido
git checkout -b recuperacion HEAD@{1}

# Alternativa: Recuperar del stash
git stash list
git stash apply stash@{0}
```

### Escenario 3: Conflictos de Fusión
```bash
# Preparar escenario de conflicto
git switch main
echo "Cambio en main" > archivo.txt
git add archivo.txt
git commit -m "Cambio en main"

git switch caracteristica
echo "Cambio en característica" > archivo.txt
git add archivo.txt
git commit -m "Cambio en característica"

# Crear conflicto
git switch main
git merge caracteristica

# Resolver conflicto
# Editar archivo.txt manualmente
git add archivo.txt
git commit -m "Resolver conflicto de fusión"
```

## 🏋️ Ejercicios Avanzados

### Ejercicio 1: Reescribir Historia
```bash
# Tarea: Combinar últimos 3 commits
git reset --soft HEAD~3
git commit -m "Implementación de característica combinada"

# Alternativa usando rebase
git rebase -i HEAD~3
# En editor: pick primer commit, squash otros
```

### Ejercicio 2: Flujo de Rama de Característica
```bash
# Tarea: Implementar flujo completo de característica
git switch -c feature/auth-usuario
echo "Autenticación de usuario" > auth.js
git add auth.js
git commit -m "Agregar autenticación de usuario"

# Actualizar main
git switch main
echo "Actualización main" > main.js
git add main.js
git commit -m "Actualizar main"

# Rebase rama de característica
git switch feature/auth-usuario
git rebase main

# Crear PR (simulación)
git push origin feature/auth-usuario
```

## 🎮 Escenarios Interactivos

### Escenario 1: Proceso de Revisión de Código
```bash
# Preparación
git switch -c feature/nueva-api
echo "Implementación API" > api.js
git add api.js
git commit -m "Implementar nueva API"

# Simulación de retroalimentación
echo "Corregir comentarios de revisión" >> api.js
git add api.js
git commit --amend --no-edit

# Subir cambios
git push origin feature/nueva-api --force-with-lease
```

### Escenario 2: Preparación de Release
```bash
# Crear rama de release
git switch -c release/1.0
git tag -a v1.0.0-rc1 -m "Candidato de release 1"

# Simulación de hotfix
git switch -c hotfix/correccion-seguridad
echo "Parche de seguridad" > seguridad.js
git add seguridad.js
git commit -m "Corregir vulnerabilidad de seguridad"

# Fusionar hotfix
git switch release/1.0
git merge hotfix/correccion-seguridad
git tag -a v1.0.0-rc2 -m "Candidato de release 2"
```

## 🚨 Resolución de Errores Comunes

### Error 1: HEAD Separado
```bash
# Simulación del problema
git checkout v1.0.0

# Solución
git switch -c nueva-rama
# o
git switch main
```

### Error 2: Push Rechazado
```bash
# Simulación del problema
git push origin main

# Solución
git fetch origin
git rebase origin/main
git push origin main
```

### Error 3: Abortar Fusión
```bash
# Durante fusión con conflictos
git merge --abort

# Comenzar de nuevo
git fetch origin
git reset --hard origin/main
```

## 📝 Proyectos de Práctica

### Proyecto 1: Colaboración en Equipo
1. Hacer fork de un repositorio
2. Crear rama de característica
3. Implementar cambios
4. Enviar pull request
5. Revisar y atender retroalimentación
6. Fusionar cambios

### Proyecto 2: Gestión de Releases
1. Crear rama de release
2. Etiquetar versiones
3. Manejar hotfixes
4. Fusionar de vuelta a desarrollo
5. Actualizar números de versión

## ✅ Pasos de Verificación

Para cada ejercicio:
1. Revisar git status
2. Revisar git log
3. Verificar estructura de ramas
4. Confirmar contenido de archivos
5. Validar mensajes de commit 

## 🎯 Ejercicios Avanzados Adicionales

### Ejercicio 4: Recuperación con Git Reflog
```bash
# Preparación: Crear y perder trabajo
git switch -c caracteristica
echo "Trabajo importante" > importante.txt
git add importante.txt
git commit -m "Cambios importantes"
git switch main
git branch -D caracteristica  # Eliminar rama accidentalmente

# Tarea: Recuperar la rama eliminada
# Solución:
git reflog  # Encontrar el hash del commit
git switch -c caracteristica-recuperada <hash>

# Verificar:
cat importante.txt
```

### Ejercicio 5: Rebase Interactivo
```bash
# Preparación: Crear múltiples commits
for i in {1..5}; do
    echo "Cambio $i" >> archivo.txt
    git add archivo.txt
    git commit -m "Cambio $i"
done

# Tarea: Reorganizar commits
git rebase -i HEAD~5

# Operaciones a probar:
# - Combinar commits relacionados
# - Reescribir mensajes de commit
# - Eliminar commits innecesarios
# - Reordenar commits
```

### Ejercicio 6: Gestión de Submódulos
```bash
# Tarea: Añadir y actualizar submódulos
git submodule add https://github.com/ejemplo/lib externa/lib
git submodule update --init --recursive

# Hacer cambios en submódulo
cd externa/lib
git switch -c caracteristica-personalizada
echo "Cambio personalizado" > personalizado.txt
git add personalizado.txt
git commit -m "Añadir característica personalizada"

# Actualizar proyecto principal
cd ../..
git add externa/lib
git commit -m "Actualizar submódulo"
```

## 🔄 Nuevos Escenarios del Mundo Real

### Escenario 4: Git Bisect con Pruebas
```bash
# Preparación: Crear script de prueba
cat > prueba.sh << 'EOF'
#!/bin/bash
grep -q "error" archivo.txt && exit 1 || exit 0
EOF
chmod +x prueba.sh

# Usar bisect con prueba automatizada
git bisect start
git bisect bad HEAD
git bisect good v1.0
git bisect run ./prueba.sh

# Analizar resultados
git bisect log
git bisect reset
```

### Escenario 5: Gestión de Archivos Grandes
```bash
# Preparación: Rastrear archivos grandes con Git LFS
git lfs install
git lfs track "*.psd"
git lfs track "*.zip"
git add .gitattributes

# Añadir y confirmar archivos grandes
git add archivo-grande.psd
git commit -m "Añadir recursos de diseño"

# Verificar rastreo LFS
git lfs ls-files
```

### Escenario 6: Gestión de Múltiples Remotos
```bash
# Configurar múltiples remotos
git remote add upstream https://github.com/original/repo.git
git remote add staging https://github.com/staging/repo.git

# Sincronizar con múltiples remotos
git fetch --all
git switch main
git merge upstream/main
git push origin main
git push staging main
```

## 🛠️ Ejercicios Avanzados de Git Hooks

### Ejercicio 7: Hooks Git Personalizados
```bash
# Crear hook pre-commit
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/bash
archivos=$(git diff --cached --name-only --diff-filter=ACM | grep '\.js$')
if [ -n "$archivos" ]; then
    npm run lint $archivos
    if [ $? -ne 0 ]; then
        echo "¡Falló el linting! Corrige los errores antes de hacer commit."
        exit 1
    fi
fi
EOF
chmod +x .git/hooks/pre-commit

# Probar el hook
echo "console.log('prueba')" > prueba.js
git add prueba.js
git commit -m "Probar hook"
```

### Ejercicio 8: Atributos Git
```bash
# Configurar estrategia de diff personalizada
cat > .gitattributes << 'EOF'
*.json diff=json
*.md diff=markdown
EOF

# Crear controlador de diff personalizado
git config diff.json.textconv "python -m json.tool"

# Probar con archivo JSON
echo '{"clave": "valor"}' > config.json
git add config.json
git diff --cached
```

## 🎮 Escenarios de Colaboración en Equipo

### Escenario 7: Flujo de Revisión de Código
```bash
# Preparar rama de característica
git switch -c caracteristica/nueva-api
echo "Código API" > api.js
git add api.js
git commit -m "Implementación inicial de API"

# Simular retroalimentación de revisión
git switch -c revision-comentarios
echo "Cambios de revisión" >> api.js
git add api.js
git commit -m "Atender comentarios de revisión"

# Incorporar retroalimentación
git switch caracteristica/nueva-api
git merge revision-comentarios
git push origin caracteristica/nueva-api
```

### Escenario 8: Gestión de Release
```bash
# Crear rama de release
git switch -c release/2.0 main
echo "2.0.0" > VERSION
git add VERSION
git commit -m "Actualizar versión a 2.0.0"

# Crear candidato de release
git tag -a v2.0.0-rc1 -m "Candidato de release 1"
git push origin v2.0.0-rc1

# Simular hotfix
git switch -c hotfix/seguridad main
echo "Corrección de seguridad" > seguridad.patch
git add seguridad.patch
git commit -m "Corrección crítica de seguridad"

# Cherry-pick al release
git switch release/2.0
git cherry-pick hotfix/seguridad
git tag -a v2.0.1 -m "Release de parche de seguridad"
```

## ✨ Ejercicios de Integración de Flujos de Trabajo

### Ejercicio 9: Integración CI/CD
```bash
# Configurar flujo de trabajo de GitHub Actions
mkdir -p .github/workflows
cat > .github/workflows/ci.yml << 'EOF'
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm test
EOF

git add .github/workflows/ci.yml
git commit -m "Añadir flujo de trabajo CI"
```

### Ejercicio 10: Implementación de Git Flow
```bash
# Inicializar Git Flow
git flow init

# Desarrollo de característica
git flow feature start nueva-caracteristica
echo "Código de característica" > caracteristica.js
git add caracteristica.js
git commit -m "Implementar nueva característica"
git flow feature finish nueva-caracteristica

# Proceso de release
git flow release start 1.0.0
echo "1.0.0" > VERSION
git add VERSION
git commit -m "Actualizar versión"
git flow release finish 1.0.0
``` 