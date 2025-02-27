# Etiquetas y Releases en Git

## 🏷️ Entendiendo las Etiquetas

Las etiquetas son referencias que apuntan a puntos específicos en la historia de Git. Típicamente se usan para marcar versiones de lanzamiento.

## 📌 Tipos de Etiquetas

### Etiquetas Ligeras
```bash
# Crear etiqueta ligera
git tag v1.0.0

# Listar todas las etiquetas
git tag

# Mostrar información de etiqueta
git show v1.0.0
```

### Etiquetas Anotadas (Recomendado)
```bash
# Crear etiqueta anotada
git tag -a v1.0.0 -m "Versión de lanzamiento 1.0.0"

# Listar etiquetas con anotaciones
git tag -n

# Mostrar información detallada de etiqueta
git show v1.0.0
```

## 🚀 Trabajando con Etiquetas

### Crear Etiquetas
```bash
# Etiquetar commit actual
git tag -a v1.0.0 -m "Versión de lanzamiento 1.0.0"

# Etiquetar commit específico
git tag -a v0.9.0 abc123f -m "Versión beta"
```

### Compartir Etiquetas
```bash
# Subir etiqueta específica
git push origin v1.0.0

# Subir todas las etiquetas
git push origin --tags
```

### Gestionar Etiquetas
```bash
# Eliminar etiqueta local
git tag -d v1.0.0

# Eliminar etiqueta remota
git push origin --delete v1.0.0

# Cambiar a etiqueta específica
git checkout v1.0.0
```

## 📦 Releases en GitHub/GitLab

### Crear Releases
1. Ir al repositorio en GitHub/GitLab
2. Navegar a la sección "Releases"
3. Hacer clic en "Crear nuevo release"
4. Seleccionar o crear una etiqueta
5. Añadir notas de release
6. Opcionalmente adjuntar binarios

### Mejores Prácticas para Notas de Release
- Listar nuevas características
- Documentar cambios incompatibles
- Incluir instrucciones de actualización
- Dar crédito a contribuidores
- Enlazar a issues/PRs relevantes

## 🔖 Numeración de Versiones

### Versionado Semántico (MAYOR.MENOR.PARCHE)
- MAYOR: Cambios incompatibles
- MENOR: Nuevas características, compatible hacia atrás
- PARCHE: Correcciones de errores, compatible hacia atrás

Ejemplo: v2.1.3

## 📝 Mejores Prácticas

1. Siempre usar etiquetas anotadas para releases
2. Seguir versionado semántico
3. Escribir notas de release detalladas
4. Etiquetar solo commits estables
5. Mantener etiquetas sincronizadas con releases

## 🔄 Flujos de Trabajo Comunes

### Proceso de Release
```bash
# Asegurar estar en rama main
git switch main

# Obtener últimos cambios
git pull origin main

# Crear etiqueta anotada
git tag -a v1.0.0 -m "Versión de lanzamiento 1.0.0"

# Subir etiqueta
git push origin v1.0.0

# Crear release en GitHub/GitLab
# Añadir notas de release y binarios
```

### Proceso de Hotfix
```bash
# Crear rama hotfix desde etiqueta
git checkout -b hotfix-1.0.1 v1.0.0

# Hacer correcciones y commit
git commit -m "Corregir error crítico"

# Crear nueva etiqueta
git tag -a v1.0.1 -m "Release hotfix v1.0.1"

# Subir cambios y etiqueta
git push origin hotfix-1.0.1
git push origin v1.0.1
``` 