# Plan de mejora — glud-website

> **keyword:** plan acotado

**Fecha:** 19 de octubre de 2026
**Alcance:** solo reparar y pulir lo que ya existe en producción. Cero funcionalidades nuevas. Basado en el estudio de cumplimiento del mismo día (evidencia archivo:línea en cada ítem).
**Flujo:** cada ítem = 1 issue → 1 rama `fix/` o `feat/` → 1 MR pequeño a `dev`. Un issue a la vez, MRs cortos y revisables. Labels del tablero: `a11y`, `fix`, `design`, `perf`, `infra`.

---

## 1. Qué NO vamos a hacer (y por qué)

Esta lista es tan importante como la anterior: evita que el plan se infle.

1. **Blog / sección de noticias:** no hay contenido y no hay flujo de publicación. El componente ya existe comentado "por falta de blogs" (ContentSection.astro:9,36). La sección de noticias es el proyecto final del curso (S3 → S13): cuando las estudiantes produzcan el primer contenido real, se descomenta. Hasta entonces, fuera del plan.
2. **Newsletter, buscador, dark/light, i18n:** no hay necesidad demostrada ni contenido que los alimente.
3. **Migrar contenido a Markdown/collections:** el contenido vive tipado en `src/data/*.ts` y funciona; migrar es trabajo cosmico sin beneficio actual. Se evalúa solo si S8 lo exige.
4. **Infra completa de calidad (tests, ESLint, Prettier, Husky):** se pospone hasta que el equipo de mantenedores crezca. Ahora mismo el cuello de botella es contenido y a11y, no tooling.
5. **Analytics:** con Cloudflare Insights ya basta para las decisiones de este plan.

---

## 2. P0 — Esta semana (el taller del 20 de octubre ejecuta 1-5)

Accesibilidad y estructura: máximo impacto por usuario, esfuerzo mínimo, todo medible.

| # | Ítem | Dónde | Evidencia | Verificación de cierre |
| --- | --- | --- | --- | --- |
| 1 | Foco visible global (`:focus-visible` con cian del tema) | hoja global de estilos | sin foco en nav/footer/tarjetas (0 matches en header.css, Footer.astro); deuda ya documentada en S3:119 | Tab recorre todo el sitio con indicador visible; los 6 componentes que ya lo definen no se rompen |
| 2 | Skip link "Saltar al contenido" | Base.astro | 0 resultados de skip en src | Primera tabulación salta a `main`; invisible hasta recibir foco |
| 3 | Headings: quitar saltos h1→h3 | ContentVideos.astro:26, EventsSection.astro:51, Actividades.astro:102 | verificado en vivo en las 3 páginas | Script de consola de headings sin saltos |
| 4 | Un solo h1 en la home | LandingDesktop.astro:114, LandingMobile.astro:72 | 2 h1 verificados en vivo | `document.querySelectorAll('h1').length === 1` sin cambiar la apariencia en ningún breakpoint |
| 5 | Texto pegado en títulos por spans sin espacio | home, aboutus, projects, slud | "COMUNIDADGNU/LINUX", "NuestraHistoria", "Subgruposy Proyectos", "SLUDSemana Linux" verificados en vivo | Copiar el título desde el navegador conserva los espacios |
| 6 | Contraste: chip de organizador a `var(--purple-bright)` | Activities (chip) | 2.79:1, falla AA; con el token queda 6.56:1 | WebAIM antes/después en el MR |
| 7 | Contraste: extremo morado del gradiente a `var(--purple-bright)` | botones primarios de actividades y events, pestaña activa | 3.09:1 en el peor caso; con el token queda 7.27:1 | WebAIM sobre el extremo morado; el lado cian no cambia |

Nota: los ítems 6-7 usan un token que ya existe en la paleta; no se inventan colores.

---

## 3. P1 — Higiene técnica (próximas 2 semanas, un MR por ítem)

Barato, sin riesgo de usuario, deja el código igual al estándar que el curso enseña.

1. **Eliminar `tailwind.config.js` muerto o migrar a `@theme`:** Tailwind v4 no lo carga (sin `@config` en todo src). Decisión sugerida: mover los tokens de `:root` (global.css:8-31) a un bloque `@theme` y borrar el config. Label: `design`.
2. **Borrar código muerto:** `header/header-scroll.ts` (0 imports) y decidir el futuro de `ContentBlog.astro` (mantener comentado con un issue que lo enlace al proyecto del curso). Label: `chore`.
3. **Sitemap completo:** añadir `site` a astro.config y las URLs `/slud/{year}/actividades` al sitemap manual (o adoptar `@astrojs/sitemap` cuando S7 lo cubra). Evidencia: el sitemap actual tiene 11 URLs y omite las dinámicas. Label: `seo`.
4. **`prerender` en 404.astro:** es la única página servida por el runtime además del API; volverla estática como las demás. Label: `perf`.
5. **Fotos de instructores correctas:** coursesData.ts:15 y 24 usan la foto de Juan Carlos para Juan Diego Grajales y Sol Daniela Cely. Contenido real afectando personas reales: prioritario aunque sea P1. Label: `content`.

---

## 4. P2 — Riesgos (este mes, con más cuidado)

Requieren revisión porque tocan comportamiento, no apariencia.

1. **Escapar la interpolación HTML en el correo** (send-email.ts:143-145) y añadir honeypot anti-spam al formulario (sin rate-limit todavía; ese va aparte cuando haya infra). Label: `fix`, prioridad de seguridad.
2. **Service worker: network-first para navegaciones HTML** (sw.js:33-52, hoy cache-first también para HTML): evita servir contenido viejo tras cada deploy. Mantener cache-first solo para assets. Label: `fix`.
3. **`prefers-reduced-motion` en las animaciones animejs** (landing-animations.ts, header-animations.ts, aboutus-animations.ts: 0 matches) y guard para `scroll-behavior: smooth` (Base.astro:38). Solo 6 CSS lo respetan hoy; los JS no. Label: `a11y`.

---

## 5. P3 — Contenido y verificación (cuando aplique)

1. **Estado post-SLUD:** verificar countdown y widget "próximo evento" (la SLUD terminó el 21 de agosto; ¿qué muestran hoy?). Decidir: actualizar a la próxima edición o archivar. Requiere navegador: primer punto de la lista pendiente del estudio.
2. **Páginas huérfanas de IA:** decidir entrada de navegación para `/certificates` y `/SludSponsors` (o confirmar que están bien como páginas de campaña enlazadas desde donde corresponde).
3. **Refresco de `/content`:** los videos más viejos son de la era Debian 10 (2019). No se toca hasta tener material nuevo que publicar; el propio curso y los cursos GNUBIES son la fuente natural. Hilo directo con el proyecto S13.

---

## 6. Orden sugerido para no chocar

1. Taller del 20 (ítems P0 1-7): dos lanes, dos MRs, archivos distintos por diseño.
2. Semana siguiente: P1 en MRs separados (5, 2, 4, 3, 1 en ese orden: primero lo de contenido y lo trivial).
3. P2 uno por semana, con revisión extra por tocar comportamiento.
4. P3 con el equipo completo, decides tú.

**Criterio de cierre de cada ítem:** build verde en CI + verificación concreta de su tabla + MR mergeado a `dev` (main solo por MR posterior, como siempre). El plan está cerrado cuando P0 y P1 estén en producción, no antes.
