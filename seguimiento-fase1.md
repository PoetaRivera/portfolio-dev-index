# Seguimiento Fase 1

## Sesion: 2026-04-08

### Tarea completada: Evaluacion + Implementacion de mejoras

---

## Mejoras implementadas (2026-04-08)

### [ALTA] #1 — Admin mode protegido con password
- Ahora requiere clave al entrar via `?admin`
- Hash SHA-256 via Web Crypto API (no plaintext en codigo)
- Sesion persiste con `sessionStorage` (dura hasta cerrar navegador)
- Clave por defecto: `admin` — **cambiar antes de produccion**
- Ver instrucciones en `paraEditarLeeEsto.txt`

### [ALTA] #2 — Categorias explicitas en proyectos
- Agregado campo `categorias: ["app", "frontend"]` a los 15 proyectos
- Filtros ahora usan `p.categorias.includes(...)` en vez de heuristica de texto
- Eliminados falsos positivos en filtros de Frontend/Backend

### [ALTA] #3 — Estado de proyectos con badge visual
- Agregado campo `estado: "activo" | "archivado" | "wip"` a cada proyecto
- Badge con indicador de color: verde (activo), gris (archivado), amarillo parpadeante (wip)

### [MEDIA] #4 — Meta tags OG y descripcion SEO
- Agregado `og:title`, `og:description`, `og:type`, `og:url`
- Agregado `twitter:card`, `twitter:title`, `twitter:description`
- Agregado `meta name="description"`

### [MEDIA] #5 — Favicon SVG inline
- Favicon con iniciales "PR" en azul sobre fondo oscuro
- No requiere archivo externo, embebido en `<head>`

### [MEDIA] #6 — Contador de proyectos
- Muestra "Mostrando X de Y proyectos" debajo de los controles
- Se actualiza al filtrar/buscar/ocultar

### Correcciones adicionales
- Corregido typo `hhttps://` → `https://` en URL demo de "Portfolio Dev"
- Corregido typo "algortimo" → "algoritmo" en descripcion de Asistente Poetico Legacy

---

## Estado del repositorio
- Cambios listos para commit y deploy
- Branch: main

---

## Mejoras implementadas (2026-04-20)

### [ALTA] #7 — Sticky controls con backdrop blur
- Envuelto en `.controls-bar` full-width con `background: var(--controls-bg)` y `backdrop-filter: blur(12px)`
- `top: 0` (antes era `top: 20px`), ya no hay sangrado de cards al hacer scroll

### [ALTA] #8 — Filtro Backend restaurado con categorías corregidas
- "Gestor de Comentarios" corregido a `categorias: ["backend"]` (era frontend, es puro backend)
- Proyectos fullstack quedan en `["app", "frontend"]` — cubiertos por el filtro "Apps Desplegadas"
- El filtro Backend queda para proyectos puramente de servidor

### [ALTA] #9 — XSS via onclick corregido
- Eliminados `onclick="toggleHide('${p.nombre}')"` e `onclick="deleteProject(...)"` del HTML dinámico
- Ahora usa `data-action` + `data-nombre` con event delegation en el grid

### [MEDIA] #10 — Ordenamiento de proyectos
- Select con opciones: Orden original / Nombre A–Z / Activos primero
- Ordenamiento en memoria sin afectar el array original

### [MEDIA] #11 — Dark/Light mode toggle
- Botón sol/luna en la barra de controles
- Persiste preferencia en localStorage
- Variables CSS completas para tema claro (`[data-theme="light"]`)
- Status badges con colores de contraste ajustados para modo claro

### [MEDIA] #12 — SEO: canonical + og:image + twitter:image
- `<link rel="canonical" href="...">` agregado
- `og:image` y `twitter:image` apuntando a `/og.png` (pendiente: subir el archivo imagen)
- `twitter:card` cambiado a `summary_large_image`

## Proximos pasos opcionales (baja prioridad)
- [ ] Subir og.png real a Vercel para completar previews sociales
- [ ] Ordenamiento drag-and-drop de proyectos
- [ ] Separar CSS y JS en archivos propios
- [ ] Foto de perfil real en lugar de iniciales "PR"
