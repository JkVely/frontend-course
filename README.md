<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=27&height=180&section=header&text=Frontend%20101&fontSize=60&fontColor=ffffff&animation=fadeIn" alt="Frontend 101" />

## De cero a maquetar en producción

**Caso de estudio real: [glud.org](https://glud.org)**

[![Curso](https://img.shields.io/badge/Curso-Frontend_101-7aa2f7?style=for-the-badge&labelColor=1a1b26)](./Indice.md)
[![Sesiones](https://img.shields.io/badge/Sesiones-14_semanales-bb9af7?style=for-the-badge&labelColor=1a1b26)](./Indice.md)
[![Nivel](https://img.shields.io/badge/Nivel-Desde_cero-9ece6a?style=for-the-badge&labelColor=1a1b26)](./docs/guia-del-estudiante.md)
[![Caso de estudio](https://img.shields.io/badge/Case_glud.org-Astro_7-7dcfff?style=for-the-badge&labelColor=1a1b26)](https://glud.org)
[![Licencia](https://img.shields.io/badge/Licencia-MIT-e0af68?style=for-the-badge&labelColor=1a1b26)](./LICENSE)

</div>

> **Idea central:** escribir código frontend lo hace cualquiera (hoy hasta una IA). Este curso enseña lo que no se puede pedir prestado: **el criterio** para decidir cuántos clics cuesta llegar a algo, dónde va cada cosa, por qué se ve como se ve y por qué el código vive donde vive.

---

## Sobre el Curso

Frontend 101 es un recorrido semanal por **todas las capas de un sitio web real**, usando el sitio del GLUD ([glud.org](https://glud.org), construido en Astro + Tailwind v4) como cuerpo de disección. No hay proyectos inventados: todo lo que se estudia está desplegado en producción, con aciertos y con errores propios.

### Filosofía

| **De:** | **Hacia:** |
| --- | --- |
| Copiar código de tutoriales | Entender por qué el código está donde está |
| "Que quede bonito" | Jerarquía visual, contraste y accesibilidad medibles |
| Pedirle todo a la IA | Saber pedir, evaluar y corregir lo que devuelve |
| Frameworks primero | Fundamentos primero, frameworks después |

> **Regla pedagógica del curso:** primero se responde *por qué está así*, después se aprende *cómo se hace*. Cada concepto técnico viene acompañado de una analogía cotidiana (Minecraft, comida, ciudades) para aterrizarlo antes de tocar código.

### A quién va dirigido

A cualquier persona que haya pasado aunque sea a medias por un curso de POO. No se asume nada de HTML, CSS, JavaScript ni herramientas web: se parte desde cero. Quien ya maqueta tiene retos de nivel superior en cada sesión.

---

## Estructura del Curso

El curso son **14 sesiones semanales** (~2 horas) organizadas en 4 bloques. Cada sesión abre con una pregunta guía y cierra con un reto práctico sobre el sitio real.

| Bloque | Sesiones | Pregunta que responde |
| --- | --- | --- |
| **0. Contexto** | S0 | Qué es este sitio y cómo llega a internet |
| **1. UX/UI: el criterio** | S1 - S3 | Cómo piensa un usuario y por qué algo se ve bien |
| **2. Cimientos técnicos** | S4 - S6 | JS, TypeScript y pnpm sin misterio |
| **3. Disección técnica** | S7 - S11 | Astro, contenido, Tailwind, animaciones y performance |
| **4. Cierre** | S12 - S13 | Construir lo diseñado: blog / noticias reales |

> **Hilo conductor:** en S3 cada estudiante diseña en wireframe una sección de noticias para glud.org. En S13 esa misma sección se implementa y se envía como Merge Request real al repositorio del grupo. Se diseña primero, se construye al final.

---

## Lo que vas a lograr

<table>
<tr>
<td width="50%" valign="top">

**Al terminar el Bloque 1 (S0-S3)**

- Explicar cómo un HTML estático llega de GitLab a tu navegador
- Auditar la experiencia de usuario de un sitio midiendo clics y flujos
- Detectar problemas de contraste, jerarquía y tipografía con criterio propio
- Diseñar un wireframe justificado de una landing completa

</td>
<td width="50%" valign="top">

**Al terminar el curso completo**

- Leer y escribir HTML semántico, CSS/Tailwind y TypeScript básico
- Navegar un proyecto Astro sin perderte (pages, layouts, components)
- Animar interfaces respetando `prefers-reduced-motion`
- Interpretar Lighthouse y subir una página a verde
- Enviar tu primer Merge Request a un proyecto real

</td>
</tr>
</table>

---

## Metodología de cada sesión

1. **15 min** — La pregunta guía: el grupo propone hipótesis antes de ver código.
2. **30 min** — Disección en vivo: se destripa el componente real de glud.org en pantalla.
3. **40 min** — Hands-on: cada quien trabaja su reto sobre el sitio clonado.
4. **15 min** — Revisión social: cada uno muestra su resultado y recibe feedback del grupo.
5. **10 min** — Lectura asignada del material de la siguiente sesión.

> **Niveles por reto:** toda sesión tiene un nivel base (obligatorio, alcanzable desde cero) y un nivel reto (para quien ya vuela). Los avanzados hacen de mentores de mesa durante el hands-on.

---

## Material por sesión

Cada carpeta en [`sesiones/`](./Indice.md) contiene:

| Archivo | Para qué sirve |
| --- | --- |
| `README.md` | Teoría completa, analogías, ejemplos reales del sitio y el reto |
| Slides (`slides/`) | Apoyo visual de la sesión, navegables con flechas |
| Ejemplos (`material/ejemplos/`) | HTML estático listo para abrir en el navegador y romper |

---

## Requisitos previos

1. Computador con permisos para instalar software.
2. Cuenta en GitHub o GitLab.
3. Ganas de preguntar: nadie sale de aquí sabiendo cosas por adivinación.

> Las herramientas (Git, pnpm, Node, editor) se instalan juntos en la Sesión 0. No necesitas preparar nada antes.

---

## Impartición

> **Impartido por:** JkVely (Juan Carlos Quintero Rubiano) para el **GLUD** — Grupo GNU/Linux Universidad Distrital Francisco José de Caldas.
>
> Líder de frontend del sitio web del grupo y del proyecto EDUglud. El caso de estudio de este curso es producción real mantenida por el propio grupo: [github.com/JkVely](https://github.com/JkVely) | [gitlab.com/GLUD](https://gitlab.com/GLUD)

---

<div align="center">

**Consulta el índice completo del curso**

[![Indice](https://img.shields.io/badge/Ver-Indice_completo-bb9af7?style=for-the-badge&labelColor=1a1b26)](./Indice.md)

*El mejor framework es el que entiendes por debajo. Empieza por el fondo.*

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=27&height=120&section=footer" alt="" />

</div>
