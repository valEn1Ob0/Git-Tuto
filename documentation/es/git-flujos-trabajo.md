# Diagramas de Flujos de Trabajo en Git

## 🌳 Estructura Básica de Ramas

```
main           ●─────●─────●─────●─────●
                     │     │     │
feature-1            ●─────●     │
                           │     │
feature-2                  ●─────●
```

## 🔄 Flujo de Rama de Características

```
main        ●────●────●────●────●────● (v1.0)
                 │         │
feature-A        ●─────────●
                     │
feature-B            ●────●
```

## 📦 Flujo GitFlow

```
main          ●──────────────●──────────●  (v1.0)
                            │
develop     ●─●─●──────●────●──────●────●
              │      │    │      │
feature-1     ●──────●    │      │
                          │      │
feature-2                 ●──────●
```

## 🚀 Flujo de Rama de Release

```
main          ●───────────●───────●  (v1.0)
                         │       │
release-1.0             ●───●───●
                           │
hotfix                    ●
```

## 🔀 Estrategias de Fusión

### Fusión Fast-Forward
```
main     ●────●────●────●
                   │
feature           ●────●
```

### Commit de Fusión
```
main     ●────●────●────●
                   │    │
feature           ●────●
```

### Rebase
```
Antes:
main     ●────●────●
              │
feature        ●────●

Después:
main     ●────●────●
                   │
feature           ●────●
```

## 🎯 Flujo de Pull Request

```
origin/main    ●────●────●────●
                    │
local/main     ●────●
                    │
feature        ●────●────●
                    │
PR                  ●─ → ─●
```

## 🔧 Resolución de Conflictos

```
main          ●────●────●
                   │ \
feature           ●──╳──●
                     │
resuelto             ●
```

## 📈 Ejemplo de Flujo Complejo

```
main            ●──────────●──────────●  (v2.0)
                          │          │
release-2.0              ●──●───●────●
                           │   │
hotfix-2.0.1              ●   │
                              │
develop       ●─●─●──────●────●──────●
                │      │    │
feature-A       ●──────●    │
                           │
feature-B                  ●────●
```

## 🔄 Flujo de Integración Continua

```
main          ●────●────●────●  (producción)
               │    │    │
staging        ●────●────●      (pruebas)
               │    │
develop        ●────●           (desarrollo)
               │
feature        ●
```

## 🏷️ Estrategia de Tags y Releases

```
main     ●─────●─────●─────●─────● (v1.0.0)
          │     │     │     │
tags     v0.1  v0.2  v0.3  v1.0-rc1
```

## 🔁 Flujo de Fork y Sincronización

```
upstream/main    ●────●────●────●
                      │
origin/main      ●────●────●
                      │    │
local/feature         ●────●
```

## 📊 Reglas de Protección de Ramas

```
protegida     ●──────●──────●  (requiere revisión)
              │      │      │
feature-1     ●──────●      │
                           │
feature-2                  ●
```

## 🚦 Flujo de Revisión de Código

```
main               ●────────●
                          │
feature       ●────●──────●
                  │
revision-1        ●
                  │
revision-2        ●
```

## 💡 Consejos para Leer Diagramas

- ● representa un commit
- ─ representa la línea temporal de la rama
- │ representa la relación entre ramas
- → representa la dirección de la operación
- ╳ representa punto de conflicto

## 🎨 Patrones Comunes

### Ramas Temáticas
```
main     ●────●────●────●
              │    │    │
tema-A        ●────●    │
                   │    │
tema-B             ●────●
```

### Ramas de Larga Duración
```
main     ●────●────●────●  (estable)
              │
develop  ●────●────●────●  (integración)
              │    │
feature       ●────●      (temporal)
``` 