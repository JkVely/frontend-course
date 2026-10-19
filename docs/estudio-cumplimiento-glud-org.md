# Estudio de cumplimiento — glud.org vs Frontend 101

> **keyword:** estudio del caso

**Fecha:** 19 de octubre de 2026
**Objeto:** medir cuánto del sitio en producción (glud.org, repo `glud-web/frontend/glud-website`) cumple realmente lo que el curso enseña en S0-S5.
**Fuentes:** checklist de 50 criterios extraídos del material (S0-S5, con referencia archivo:línea), auditoría del repo con evidencia archivo:línea, revisión en vivo de las 11 URLs del sitemap, y mediciones propias de contraste WCAG 2.1 sobre la paleta real.

---

## 1. Resumen ejecutivo

**Veredicto global: el sitio cumple aproximadamente el 80-85% de lo que el curso enseña, y sus fallas son casi exactamente las deudas que el propio material documenta.** No hay contradicción grave entre curso y producción: donde el sitio falla, el material ya lo venía señalando como deuda conocida (foco visible, árboles gemelos, glow). Lo más valioso del ejercicio: tres cosas que producción hace y el curso aún no cubre, y tres casos donde producción contradice sutilmente al material — material perfecto para las sesiones S6-S13 que están en construcción.

Fortalezas principales:

1. **Accesibilidad de componentes por encima del nivel del curso:** hamburguesa con `aria-expanded`/`aria-controls`, focus trap, Escape y drag (HeaderMobile.astro:21-23, header-animations.ts), clones del marquee con `aria-hidden` y `tabindex=-1`, tabs con `role=tablist`, `<dialog>` con `aria-labelledby`. Las 20 imágenes del sitio tienen `alt`.
2. **SEO on-page completo y único por página:** title, description, canonical, OG, Twitter, JSON-LD de Organization, robots.txt y sitemap correctos (Base.astro:15-85).
3. **TypeScript real:** 8 módulos `.ts` en producción y todo el contenido vive en datos tipados (`src/data/*.ts`), no en JSON suelto.

Deudas principales (todas con evidencia):

1. **Foco de teclado:** sin `:focus-visible` en nav, footer ni tarjetas de events/cursos; sin skip link en Base.astro.
2. **Estructura de headings:** doble h1 en la home (LandingDesktop.astro:114, LandingMobile.astro:72), saltos h1→h3 en `/content`, `/events` y `/actividades`, y títulos con texto pegado ("NuestraHistoria", "Subgruposy Proyectos").
3. **Contraste:** 2 de 16 pares medidos fallan AA (chip de organizador 2.79:1; texto oscuro sobre el extremo morado del gradiente 3.09:1).
4. **Higiene y riesgo:** `tailwind.config.js` muerto (Tailwind v4 no lo carga sin `@config`), `header-scroll.ts` sin usar, sitemap manual que omite las páginas dinámicas, interpolación HTML sin escapar en `send-email.ts:143-145`, y service worker cache-first que puede servir HTML viejo tras un deploy.

---

## 2. Cumplimiento por sesión

Leyenda: CUMPLE / PARCIAL / NO CUMPLE / NO VERIFICABLE (requiere navegador o ejecución).

### S0 — Qué es este sitio y cómo llega a internet

| Criterio (referencia del material) | Veredicto | Evidencia |
| --- | --- | --- |
| Las 3 capas separadas con significado (s0:23-27) | CUMPLE | HTML semántico verificado en vivo (header/main/section/footer, aria); CSS por componente; JS en módulos |
| Estático SSG justificado (s0:100-109) | PARCIAL | 13 de 15 rutas prerenderizadas, pero `output: 'server'` con adapter Node (astro.config.mjs:8-11): 404 y `/api/send-email` corren en runtime. Es híbrido, no SSG puro como dice el material (s0:38-44) |
| Repo fuente de verdad, dev→main con MR (s0:117-129) | CUMPLE | git log: commits semánticos, merge commits, main 3 archivos detrás de dev (bento de videos aún sin salir) |
| JS propio mínimo ~8 KB (s0:37) | PARCIAL | El JS propio es chico (scripts inline minificados + 8 módulos), pero animejs y swiper viajan en landing y slud. La cifra del material habla de "propio": aclarar en S6+ |
| Network y Elements como auditoría (s0:152-156) | CUMPLE | Verificable en vivo: estilos inline por página (inlineStylesheets always), fuentes woff2 preloaded, imágenes lazy con width/height |

### S1 — Cómo piensa un usuario

| Criterio | Veredicto | Evidencia |
| --- | --- | --- |
| Nombres de nav descriptivos, no ingeniosos (s1:74) | CUMPLE | Cursos, Contenido, Eventos, Proyectos, Acerca de (nav y mapa del footer) |
| Agrupar por intención del usuario (s1:70-74) | CUMPLE | Inscribirse a curso → `/cursos` → CTA a LimeSurvey; contactar → `/contact` con formulario; agenda → `/actividades` con tabs por día |
| Todo alcanzable desde home (s1:70-71) | PARCIAL | `/certificates` y `/SludSponsors` no aparecen en nav ni en el mapa del footer; verificar si alguna página los enlaza (posible página huérfana de IA) |
| Tareas reales en pocos clics (s1:106-114) | CUMPLE | Verificado en vivo: fecha/lugar de SLUD (1 clic), correo oficial (0 clics, footer), inscripción a curso (2 clics) |
| Contenido urgente sin clics en home (s1:123) | PARCIAL | La home es hero + sponsors; SLUD vive a 1 clic por nav. Menos crítico hoy: la SLUD 2026 ya pasó (18-21 de agosto) |

### S2 — Por qué esto se ve bien

| Criterio | Veredicto | Evidencia |
| --- | --- | --- |
| Máximo 2 familias con roles (s2:25) | CUMPLE | Exo 2 Variable (display) + Fira Sans (cuerpo), global.css:35-51 |
| woff2, subset, preload, swap (s2:35) | CUMPLE | Preload de exo2 y firasans-bold (Base.astro:83-84), `font-display: swap`. Detalle: firasans-regular no se pre-carga |
| Contraste AA medido con herramienta (s2:59-63) | CUMPLE CON EXCEPCIONES | 14 de 16 pares medidos pasan (blanco 13.75:1, cian 12.88:1, gris 5.34:1). Fallan: chip de organizador 2.79:1 y texto oscuro sobre el morado del gradiente 3.09:1 |
| Combinación final texto+fondo con opacidades (s2:71) | CUMPLE (medición propia) | Blanco al 80% = 9.23:1 hoy; el material ya lo marca como patrón frágil |
| Tokens, sin hardcodeos (s2:72) | PARCIAL | Paleta en `:root` (global.css:8-31), pero `tailwind.config.js` está muerto (v4 exige `@config`), hay hex sueltos en los 17 CSS de componentes y 15 `!important` |
| El glow baja legibilidad (s2:76-77) | DEUDA DOCUMENTADA | El sitio usa text-shadow/glow en casi todo; los ratios pasan, el material ya advierte el patrón |

### S3 — Cómo se diseña una página que convierte

| Criterio | Veredicto | Evidencia |
| --- | --- | --- |
| Anatomía de 6 secciones (s3:26-46) | PARCIAL | Nav, hero, prueba social (sponsors) y footer presentes; no hay sección de features ni CTA final diferenciados en la home |
| Hero con propuesta de valor y CTA jerarquizado (s3:34, 68) | CUMPLE | Un primario relleno + un secundario bordeado, exactamente el caso que cita el material |
| Hamburguesa bien hecha (s3:89-97) | CUMPLE SOBRESALIENTE | Bottom-sheet, targets grandes, `aria-expanded`/`aria-controls`, focus trap, Escape, drag (header-animations.ts) |
| 7 estados de interacción (s3:109-117) | PARCIAL | Hover muy completo (header, footer, tarjetas, botones); focus solo en 6 componentes; error presente en el formulario (`aria-invalid`); loading/error genéricos sin sistema |
| Foco visible en todo el sitio (s3:119) | NO CUMPLE | 0 matches en header.css y Footer.astro; nav y footer usan el outline por defecto |
| Mobile-first sin duplicar árboles (s3:129-139) | PARCIAL | Árboles gemelos landing-desktop/landing-mobile y header desktop/mobile: la deuda que el material documenta (s3:139) está en producción |

### S4 — Qué es JavaScript y cómo funciona su lógica

| Criterio | Veredicto | Evidencia |
| --- | --- | --- |
| Cada script con propósito justificado (s4:200-207) | CUMPLE | 10 funcionalidades reales: hamburguesa, copiar correo (Footer.astro:170-180), header al scroll (Base.astro:196-322), tabs, countdowns, certificados PDF (import dinámico de jsPDF), fallback de thumbnails, widget en vivo |
| Menú con clases y aria (s4:204) | CUMPLE | header-animations.ts alterna clases y actualiza `aria-expanded` |
| Copiar correo con clipboard (s4:205) | CUMPLE | `navigator.clipboard.writeText` + tooltip |
| Nav activa por scroll (s4:206) | CUMPLE | Script del header con rAF y mousemove |
| `===`, manejo de null, preventDefault (slides s4) | CUMPLE | Los módulos `.ts` se compilan con chequeo de Astro; 3 scripts `is:inline` sin procesar (revisar en el taller) |
| Consola sin errores | NO VERIFICABLE | Requiere navegador: queda como verificación del taller |

### S5 — Por qué existe TypeScript

| Criterio | Veredicto | Evidencia |
| --- | --- | --- |
| TS real en producción (s5:25-33) | CUMPLE | 8 módulos `.ts` (header-animations, landing-animations, aboutus-animations, aboutus-section, content-section, certificates-generator, header-scroll) + genéricos `querySelectorAll<HTMLImageElement>` en VideoThumbnail |
| Interfaces como contratos de datos (s5:115-130) | CUMPLE | Todo el contenido vive en `src/data/*.ts` tipado (activities, events, projects, slud-history, sponsors, sponsorship, videos) |
| strict y null-safety (s5:50-62, 170-185) | NO VERIFICABLE | No hay tsconfig propio visible; Astro aplica su chequeo. Revisar en S6 |
| Contra-ejemplo nuevo para el curso | HALLAZGO | send-email.ts:143-145 interpola `userName`/`eventTitle` sin escapar en el HTML del correo: el caso real perfecto de por qué validar y tipar la entrada (insumo para S6+) |

### Proceso (guía del estudiante)

| Criterio | Veredicto | Evidencia |
| --- | --- | --- |
| MRs pequeños a dev, nunca directo a main (guía:66-76) | CUMPLE | Historial de origin/dev y origin/main: solo merges desde dev |
| CI antes de merge | CUMPLE | .gitlab-ci.yml con corepack pnpm + build; netlify.toml con headers de seguridad (CSP, HSTS) |

---

## 3. Lo que el sitio hace y el curso aún no enseña

Material listo para las sesiones en construcción:

1. **OG, Twitter cards y JSON-LD** (Base.astro:47-85): cabe en S11 o en una ampliación de S0/S3.
2. **Focus trap y accesibilidad de componentes** (header-animations.ts): supera lo que pide S3; es el ejemplo perfecto para el nivel reto.
3. **Adapter Node + Docker + CI** (astro.config.mjs, Dockerfile, .gitlab-ci.yml): contradice el "es estático" de S0; explicar el híbrido en S7 (Astro) o S8.
4. **Service worker y PWA** (public/sw.js, registrado solo en producción): nadie lo menciona en S0-S5.
5. **Escapado y validación de entrada en el API** (send-email.ts): insumo directo de S5/S6.

---

## 4. Casos donde producción contradice al material

1. **"glud.org es estático" (s0:38-44):** la configuración es `output: 'server'` con adapter Node standalone; 404 y el API corren en un servidor. Las páginas que ve el usuario sí son prerenderizadas, pero el despliegue es híbrido. Corregir el material o convertir la explicación en ventaja didáctica.
2. **"~8 KB de JS propio" (s0:37):** cierto para el código propio, engañoso como cifra total: animejs y swiper se cargan en landing y slud. Precisar en el material ("propio vs total") o medirlo en el reto de S0.
3. **"Tokens, no hardcodeos" (s2:72):** `tailwind.config.js` no está cargado por Tailwind v4 (sin `@config`/`@theme` en ningún archivo): la configuración declarada ahí está muerta y la paleta vive duplicada en `:root`. El curso enseña el estándar correcto; producción todavía no lo aplica.

---

## 5. Calificación por bloque

| Bloque | Cumplimiento | Comentario |
| --- | --- | --- |
| S0 Contexto | 85% | Sólido; aclarar el híbrido SSG/SSR |
| S1 UX | 80% | Navegación clara; 2 páginas huérfanas de navegación |
| S2 UI | 80% | Tipografía y contraste sobresalientes; tokens sin adoptar |
| S3 Landing/estados | 70% | La brecha más grande: foco y estados incompletos |
| S4 JS | 90% | Todo lo enseñado existe y funciona en producción |
| S5 TS | 85% | TS real; falta tsconfig visible y hay 1 contra-ejemplo |
| Proceso git/CI | 95% | Flujo respetado tal como lo enseña la guía |

**Lectura pedagógica:** el sitio sirve exactamente para lo que fue diseñado como cuerpo de disección: tiene aciertos que valen como ejemplo y deudas concretas que valen como reto. La recomendación es no "arreglar" el material para que el sitio quede perfecto: mantener las deudas visibles y convertirlas en los retos de S6-S13 y del taller del 20 de octubre.

---

## 6. Lo que este estudio no pudo verificar

Por honestidad metodológica, queda pendiente (requiere navegador o ejecución):

1. Puntaje Lighthouse real por página (el objetivo del grupo es 100/100/100/100).
2. Peso total de página y número de peticiones por ruta (reto de S0).
3. Comportamiento en runtime del formulario (envío E2E) y del service worker tras un deploy.
4. Estado del countdown y del widget "próximo evento" ahora que la SLUD 2026 ya pasó.
5. Si `/certificates` y `/SludSponsors` reciben enlaces desde alguna página (huérfanas de IA).
