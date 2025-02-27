# Git Avanzado

## 🔄 Gestión Avanzada de Ramas

### Estrategias de Ramificación
```bash
# Crear y cambiar a rama de características
git switch -c feature/autenticacion-usuario

# Rebase de rama de características sobre main
git switch feature/autenticacion-usuario
git rebase main

# Rebase interactivo para limpiar historial
git rebase -i HEAD~3
```

## 🎯 Operaciones Avanzadas

### Guardado Temporal (Stash)
```bash
# Guardar cambios del directorio de trabajo
git stash save "WIP: implementando formulario login"

# Listar stashes
git stash list

# Aplicar y eliminar stash
git stash pop

# Aplicar sin eliminar
git stash apply stash@{0}
```

### Cherry-pick
```bash
# Aplicar commit específico a rama actual
git cherry-pick abc123f

# Cherry-pick sin confirmar
git cherry-pick -n abc123f
```

### Reflog - Herramienta de Recuperación
```bash
# Ver historial de reflog
git reflog

# Recuperar rama eliminada
git checkout -b rama-recuperada HEAD@{2}
```

## 🔍 Gestión Avanzada del Historial

### Reescribir Historial
```bash
# Modificar último commit
git commit --amend --no-edit

# Combinar últimos 3 commits
git reset --soft HEAD~3
git commit -m "Implementación de característica combinada"
```

### Bisect - Búsqueda de Errores
```bash
# Iniciar bisect
git bisect start
git bisect bad  # Versión actual es mala
git bisect good v1.0.0  # Última versión buena conocida

# Git realizará checkout automáticamente
# Marcar cada versión
git bisect good  # o
git bisect bad

# Finalizar bisect
git bisect reset
```

## 🔒 Seguridad y Archivos Grandes

### Git LFS (Large File Storage)
```bash
# Instalar Git LFS
git lfs install

# Rastrear archivos grandes
git lfs track "*.psd"
git add .gitattributes
```

### Firma de Commits con GPG
```bash
# Configurar llave GPG
git config --global user.signingkey <tu-id-llave>

# Firmar commits
git commit -S -m "Mensaje de commit firmado"
```

## 🚀 Ejemplo Real: Implementación de Característica

```bash
# Iniciar nueva característica
git switch -c feature/pasarela-pago

# Realizar cambios y confirmar
git add .
git commit -m "Agregar integración de pasarela de pago"

# Actualizar con cambios de main
git fetch origin
git rebase origin/main

# Combinar commits antes de fusionar
git rebase -i HEAD~3

# Subir a remoto
git push origin feature/pasarela-pago --force-with-lease
```

## 📚 Mejores Prácticas
- Usar siempre `--force-with-lease` en lugar de `--force`
- Mantener commits atómicos y enfocados
- Escribir mensajes de commit significativos
- Usar convenciones de nomenclatura para ramas
- Sincronizar regularmente con la rama principal
- Utilizar Git hooks para control de calidad