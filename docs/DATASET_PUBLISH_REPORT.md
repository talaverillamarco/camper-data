# DATASET_PUBLISH_REPORT — DATASET-PUBLISH-001

## Metadatos de publicación

| Campo | Valor |
|---|---|
| Fecha de publicación | 2026-07-08T18:17:12+02:00 |
| Commit publicado | `eb6bf58` — feat: publish full Spain dataset v1 (16 regions, 3563 POIs) |
| Repositorio | https://github.com/talaverillamarco/camper-data |
| Rama | `main` (sincronizada con `origin/main`) |
| GitHub Pages base URL | https://talaverillamarco.github.io/camper-data/ |

## Versiones del dataset

| Campo | Valor |
|---|---|
| schemaVersion | 1 |
| dataVersion | 2026.07.05 |
| Número de regiones | 16 |
| Número total de POIs | 3563 |

## Documentación de referencia

| Archivo | Estado |
|---|---|
| docs/PROJECT.md | No encontrado en el repositorio |
| docs/ROADMAP.md | No encontrado en el repositorio |
| docs/DATA_PROVENANCE_POLICY.md | No encontrado en el repositorio |

## Estructura del dataset publicado

El dataset actual en `main` usa **layout plano** (JSON en la raíz del repositorio).
No existe `output_v2/` ni carpeta `regions/` en el workspace.

### Archivos publicados

- `spain_index.json`
- `andalucia.json`
- `aragon.json`
- `asturias.json`
- `baleares.json`
- `cantabria.json`
- `castilla_leon.json`
- `castilla_mancha.json`
- `cataluna.json`
- `ceuta.json`
- `extremadura.json`
- `galicia.json`
- `madrid.json`
- `murcia.json`
- `navarra.json`
- `pais_vasco.json`
- `valencia.json`

`spain_index.json` referencia las regiones con URLs relativas en raíz (p. ej. `"url": "madrid.json"`), no bajo `regions/`.

## Comprobaciones previas a la publicación

| Comprobación | Resultado |
|---|---|
| Existe `spain_index.json` | OK |
| Existe carpeta `regions/` | **FALLO** — no presente en el workspace |
| Todas las regiones del índice existen localmente | OK (16/16 archivos en raíz) |
| JSON locales válidos (muestra) | OK — `spain_index.json`, `madrid.json`, `castilla_mancha.json`, `andalucia.json`, `galicia.json` |
| Builder modificado | No — no hay builder en este repositorio |
| Contenido JSON modificado | No — sin cambios en el working tree de dataset |
| `schemaVersion` / `dataVersion` modificados | No |

## Acción de publicación

No fue necesario un nuevo push de dataset: `main` ya estaba publicado en GitHub en el commit `eb6bf58`.
GitHub Pages sirve directamente desde la rama `main`.

## URLs verificadas (post-publicación)

### URLs requeridas por DATASET-PUBLISH-001 (`regions/`)

| URL | HTTP | Content-Type | JSON válido | Redirecciones |
|---|---|---|---|---|
| https://talaverillamarco.github.io/camper-data/spain_index.json | 200 | application/json; charset=utf-8 | Sí | Ninguna |
| https://talaverillamarco.github.io/camper-data/regions/madrid.json | 404 | text/html; charset=utf-8 | No | Ninguna |
| https://talaverillamarco.github.io/camper-data/regions/castilla_mancha.json | 404 | text/html; charset=utf-8 | No | Ninguna |
| https://talaverillamarco.github.io/camper-data/regions/andalucia.json | 404 | text/html; charset=utf-8 | No | Ninguna |
| https://talaverillamarco.github.io/camper-data/regions/galicia.json | 404 | text/html; charset=utf-8 | No | Ninguna |

### URLs efectivas según layout publicado (raíz)

| URL | HTTP | Content-Type | JSON válido | Redirecciones |
|---|---|---|---|---|
| https://talaverillamarco.github.io/camper-data/madrid.json | 200 | application/json; charset=utf-8 | Sí | Ninguna |
| https://talaverillamarco.github.io/camper-data/castilla_mancha.json | 200 | application/json; charset=utf-8 | Sí | Ninguna |
| https://talaverillamarco.github.io/camper-data/andalucia.json | 200 | application/json; charset=utf-8 | Sí | Ninguna |
| https://talaverillamarco.github.io/camper-data/galicia.json | 200 | application/json; charset=utf-8 | Sí | Ninguna |

## Resultado global

| Criterio | Estado |
|---|---|
| Dataset publicado en GitHub Pages (layout actual) | **OK** |
| `spain_index.json` accesible | **OK** |
| Regiones bajo `regions/` accesibles | **FALLO** (404) — layout no implementado |
| Regiones en raíz accesibles | **OK** |
| Sin redirecciones inesperadas | **OK** |
| DATASET-PUBLISH-001 completado al 100% | **PARCIAL** — bloqueado por ausencia de `regions/` en el dataset actual |

## Notas

- El dataset publicado corresponde a la versión v1 restaurada previamente (3563 POIs, 16 regiones).
- Para cumplir las URLs `regions/*.json` sin regenerar ni alterar el contenido de los JSON, haría falta disponer de `output_v2/` con estructura `regions/` o replicar esa estructura desde el builder en un paso de publicación dedicado (fuera del alcance de esta ejecución).
