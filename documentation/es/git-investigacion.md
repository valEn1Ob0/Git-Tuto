# Guía de Investigación del Historial de Git

## 🔍 Comandos Básicos de Historial

### Git Blame
```bash
# Blame básico
git blame archivo.txt

# Ignorar cambios de espacios en blanco
git blame -w archivo.txt

# Mostrar rango específico de líneas
git blame -L 10,20 archivo.txt

# Mostrar detalles del commit
git blame -l archivo.txt

# Detectar líneas movidas o copiadas
git blame -M archivo.txt
```

### Git Log
```bash
# Ver historial del archivo
git log --follow archivo.txt

# Mostrar parches
git log -p archivo.txt

# Mostrar estadísticas
git log --stat archivo.txt

# Mostrar gráfico
git log --graph --oneline --all
```

## 🕵️ Técnicas Avanzadas de Investigación

### Encontrar Cambios
```bash
# Buscar en mensajes de commit
git log --grep="corrección de error"

# Buscar cambios en código
git log -S"nombre_funcion"

# Buscar patrones regex
git log -G"patron.*"

# Encontrar commits de autor
git log --author="Juan"
```

### Investigar Líneas
```bash
# Mostrar evolución de línea
git blame -w -C -C -C archivo.txt

# Encontrar commit original de líneas
git blame -w --reverse INICIO..FIN archivo.txt

# Rastrear movimientos de líneas entre archivos
git log --follow -p archivo.txt
```

## 📊 Arqueología de Código

### Encontrar Introducción de Errores
```bash
# Usar bisect para encontrar problemas
git bisect start
git bisect bad HEAD
git bisect good v1.0
git bisect run test.sh
```

### Investigar Cambios
```bash
# Mostrar detalles del commit
git show hash_commit

# Comparar versiones de archivo
git diff commit1..commit2 archivo.txt

# Encontrar archivos renombrados
git log --follow --name-status archivo.txt
```

## 🔎 Análisis Avanzado de Historial

### Análisis de Rango de Commits
```bash
# Ver rango de commits
git log commit1..commit2

# Comparar ramas
git log main..feature

# Mostrar historial de fusiones
git log --merges
```

### Historial de Archivo
```bash
# Mostrar creación de archivo
git log --diff-filter=A -- archivo.txt

# Mostrar eliminación de archivo
git log --diff-filter=D -- archivo.txt

# Mostrar modificaciones de archivo
git log --diff-filter=M -- archivo.txt
```

## 🛠️ Herramientas de Investigación

### Git Pickaxe
```bash
# Encontrar introducción de cadena
git log -S"cadena" --patch

# Encontrar cambios de patrón regex
git log -G"patron" --patch

# Buscar en archivos específicos
git log -S"cadena" -- "*.js"
```

### Ignorar Revisiones en Blame
```bash
# Crear .git-blame-ignore-revs
echo "hash_commit" > .git-blame-ignore-revs

# Usar archivo de ignorar
git blame --ignore-revs-file .git-blame-ignore-revs
```

## 📈 Análisis Estadístico

### Estadísticas de Contribución
```bash
# Estadísticas de autor
git shortlog -sn

# Conteo de commits por autor
git log --author="nombre" --oneline | wc -l

# Estadísticas de cambios en archivos
git log --stat --author="nombre"
```

### Evolución del Código
```bash
# Rastrear cambios de tamaño de archivo
git log --stat --oneline archivo.txt

# Mostrar ciclo de vida del archivo
git log --follow --stat archivo.txt
```

## 🔧 Escenarios Prácticos de Investigación

### Escenario 1: Investigación de Error
```bash
# 1. Encontrar cambios relevantes
git log -S"cadena_relacionada_error"

# 2. Revisar commit específico
git show hash_commit

# 3. Analizar historial de archivo
git blame -w -C archivo.txt
```

### Escenario 2: Historial de Característica
```bash
# 1. Encontrar introducción de característica
git log --grep="nombre característica"

# 2. Rastrear cambios de archivo
git log --follow -p archivo_caracteristica.txt

# 3. Revisar commits relacionados
git show hash_commit
```

## 📝 Mejores Prácticas

1. Usar términos de búsqueda específicos
2. Combinar múltiples comandos
3. Verificar hallazgos
4. Documentar proceso de investigación
5. Usar flags apropiados

## 🚀 Consejos Avanzados

### Optimización de Rendimiento
```bash
# Usar clonación superficial
git clone --depth 1 url_repositorio

# Usar clonación parcial
git clone --filter=blob:none url_repositorio

# Usar checkout disperso
git sparse-checkout set directorio/
```

### Consultas Complejas
```bash
# Múltiples condiciones
git log --grep="característica" --author="Juan" --since="1 week ago"

# Formatos personalizados
git log --pretty=format:"%h - %an, %ar : %s"
```

## 🎯 Referencia Rápida

### Comandos Comunes de Investigación
```bash
git blame              # Historial línea por línea
git log               # Historial de commits
git show              # Detalles de commit
git diff              # Comparar cambios
git bisect            # Búsqueda binaria
git shortlog          # Resumen de autor
git log --follow      # Historial de archivo
git log -S            # Búsqueda de contenido
git log -G            # Búsqueda de patrón
```

## 🔬 Técnicas Avanzadas de Investigación

### Análisis de Notas Git
```bash
# Agregar nota a un commit
git notes add -m "Nota de investigación: Posible fuente del error" commit_hash

# Mostrar notas con commits
git log --show-notes

# Buscar en las notas
git log --notes-all | grep "error"

# Enviar notas al remoto
git push origin refs/notes/*
```

### Búsqueda Binaria con Script Personalizado
```bash
# Crear script de prueba
cat > test.sh << 'EOF'
#!/bin/bash
# Lógica de prueba personalizada
if grep -q "ERROR" log.txt; then
    exit 1  # Commit malo
else
    exit 0  # Commit bueno
fi
EOF
chmod +x test.sh

# Ejecutar bisect automatizado
git bisect start HEAD v1.0
git bisect run ./test.sh
```

### Investigación Basada en Tiempo
```bash
# Encontrar cambios en rango de tiempo
git log --since="2 weeks ago" --until="1 week ago"

# Encontrar commits en fechas específicas
git log --before="2023-01-01" --after="2022-12-31"

# Mostrar detalles de marca de tiempo
git log --date=iso-strict
```

## 📊 Análisis de Métricas Avanzadas

### Análisis de Rotación de Código
```bash
# Rastrear cambios de archivos en el tiempo
git log --numstat --pretty="%H" | awk '
NF==3 {plus+=$1; minus+=$2} 
END {print "Agregado: "plus"\nEliminado: "minus"\nRotación: "plus+minus}'

# Encontrar archivos más modificados
git log --pretty=format: --name-only | sort | uniq -c | sort -rg | head -10
```

### Análisis de Contribución de Autores
```bash
# Analizar patrones de autores
git shortlog -sn --no-merges

# Mostrar tiempos de actividad de autores
git log --format='%ad' --date=iso | cut -d ' ' -f 2 | sort | uniq -c

# Encontrar instancias de programación en pareja
git log --pretty=format:"%an, %cn" | sort | uniq -c | sort -nr
```

### Análisis de Impacto
```bash
# Encontrar cambios de alto impacto
git log --pretty=format: --name-only | sort | uniq -c | sort -rg

# Identificar commits riesgosos
git log --pretty=format:"%h - %an, %ar : %s" --diff-filter=M --stat
```

## 🔍 Herramientas de Inspección Profunda

### Análisis de Contenido de Commits
```bash
# Encontrar patrones específicos de código
git log -p | grep -A 5 -B 5 "TODO"

# Rastrear cambios en funciones
git log -L :nombre_funcion:archivo.js

# Encontrar código duplicado
git log -S"patron_duplicado" --pickaxe-all
```

### Análisis de Ramas
```bash
# Encontrar ramas no fusionadas
git branch --no-merged main

# Mostrar jerarquía de ramas
git show-branch --all

# Encontrar commits huérfanos
git fsck --lost-found
```

### Análisis de Fusiones
```bash
# Mostrar historial de fusiones
git log --merges --first-parent main

# Encontrar patrón de archivos conflictivos
git log --cc -m --diff-filter=C

# Analizar frecuencia de fusiones
git log --merges --format=format:"%cd" --date=short | uniq -c
```

## 🛠️ Herramientas de Investigación Personalizadas

### Formatos de Log Personalizados
```bash
# Crear formato de log personalizado
git config --global alias.investigacion \
    "log --pretty=format:'%C(yellow)%h%Creset %C(blue)%ad%Creset %s %C(red)%d%Creset %C(green)%an%Creset' --date=short"

# Usar formato personalizado
git investigacion
```

### Scripts de Investigación
```bash
# Crear ayudante de investigación
cat > git-investigar << 'EOF'
#!/bin/bash
# Buscar en commits y mostrar contexto
git log -p -S"$1" --pickaxe-all
# Mostrar ramas relacionadas
git branch --contains $(git log -S"$1" --pretty=format:"%H" | head -1)
EOF
chmod +x git-investigar
```

### Herramientas de Diff Personalizadas
```bash
# Configurar herramienta de diff personalizada
git config --global diff.tool personalizada
git config --global difftool.personalizada.cmd 'diff-highlight "$LOCAL" "$REMOTE"'

# Usar con investigación
git difftool commit1..commit2
```

## 📈 Análisis de Rendimiento

### Análisis de Tamaño del Repositorio
```bash
# Encontrar archivos grandes
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort -rn -k2 |
  head -10

# Analizar archivos pack
git verify-pack -v .git/objects/pack/*.idx |
  sort -k 3 -n |
  tail -10
```

### Rendimiento de Clonación
```bash
# Analizar rendimiento de fetch
GIT_TRACE=1 git fetch origin

# Verificar estadísticas de pack
git count-objects -vH

# Optimizar repositorio
git gc --aggressive --prune=now
```

## 🎯 Flujos de Trabajo de Investigación

### Flujo de Trabajo de Investigación de Errores
```bash
# 1. Encontrar commits potenciales
git log -S"patron_error" --since="1 month ago"

# 2. Crear rama de investigación
git switch -c investigacion/error-123

# 3. Analizar cambios
git log -p --since="1 month ago" -- **/archivos_relevantes/*

# 4. Probar commits específicos
git checkout -b prueba/error-123 commit_sospechoso
```

### Flujo de Trabajo de Regresión de Rendimiento
```bash
# 1. Crear prueba de rendimiento
cat > prueba-rendimiento.sh << 'EOF'
#!/bin/bash
time ./app benchmark
EOF
chmod +x prueba-rendimiento.sh

# 2. Ejecutar bisect con prueba de rendimiento
git bisect start HEAD ultimo_commit_bueno
git bisect run ./prueba-rendimiento.sh

# 3. Analizar resultados
git bisect log > investigacion-rendimiento.log
```

### Flujo de Trabajo de Auditoría de Seguridad
```bash
# 1. Buscar datos sensibles
git log -p | grep -i "contraseña\|secreto\|clave"

# 2. Verificar permisos de archivos
git ls-files --stage | grep "100755"

# 3. Revisar cambios de autenticación
git log -p -- **/auth/** **/seguridad/**

# 4. Generar reporte de seguridad
git log --since="1 month ago" --grep="seguridad" --pretty=format:"%h - %s" > auditoria-seguridad.log
``` 