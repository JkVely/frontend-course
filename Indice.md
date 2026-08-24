<div align="center">
	<h1>Índice del Curso</h1>
	<p><strong>Frontend 101 — De cero a maquetar en producción</strong></p>
	<hr />
	<p>GLUD — Grupo GNU/Linux Universidad Distrital</p>
	<p>Caso de estudio: <a href="https://glud.org">glud.org</a></p>
	<hr />
</div>

## Documentación General

<table width="100%">
	<tr>
		<td width="50%">
			<h3><a href="docs/guia-del-estudiante.md">Guía del Estudiante</a></h3>
			<p>Cómo funciona el taller: mecánica de sesión, niveles base/reto, rúbrica de retos y flujo de trabajo con Git.</p>
		</td>
		<td width="50%">
			<h3><a href="README.md">Descripción del Curso</a></h3>
			<p>Filosofía, estructura por bloques y metodología del programa completo.</p>
		</td>
	</tr>
</table>

---

## Bloque 0 — Contexto
**Sesión 0**

<div style="background-color:#1a1b26; padding:15px; margin:10px 0; border-left:4px solid #7aa2f7;">
	<h3>S0: Qué es este sitio y cómo llega a internet <a href="sesiones/s0-contexto/README.md">(material)</a></h3>
	<h4>Pregunta guía</h4>
	<p>Escribes glud.org en el navegador. ¿Qué pasa entre ese Enter y la página pintada?</p>
	<h4>Temas</h4>
	<ul>
		<li>Anatomía de un sitio web: HTML, CSS y JS desde 30.000 pies</li>
		<li>DNS, servidor y renderizado: el viaje de una petición</li>
		<li>Sitios estáticos vs dinámicos: por qué glud.org es estático (SSG)</li>
		<li>El repositorio como fuente de verdad: ramas <code>dev</code> y <code>main</code>, deploy a producción</li>
		<li>Herramientas del taller: Git, Node, pnpm, VS Code</li>
	</ul>
	<p><strong>Reto:</strong> clonar el sitio, levantarlo local y dejar 3 dudas escritas para las siguientes sesiones.</p>
	<p><strong>Slides:</strong> <a href="slides/s0.html">s0.html</a></p>
</div>

---

## Bloque 1 — UX/UI: El Criterio
**Sesiones 1-3 · cero código**

<div style="background-color:#1a1b26; padding:15px; margin:10px 0; border-left:4px solid #9ece6a;">
	<h3>S1: Cómo piensa un usuario cuando usa tu sitio <a href="sesiones/s1-fundamentos-ux/README.md">(material)</a></h3>
	<h4>Temas</h4>
	<ul>
		<li>UX vs UI: experiencia vs interfaz, sin confundirlas nunca más</li>
		<li>Jerarquía visual: qué mira primero el ojo y por qué</li>
		<li>Arquitectura de información y sitemap: dónde vive cada cosa</li>
		<li>La regla de los 3 clics: verdad útil o mito exagerado</li>
		<li>Flujos de tarea: medir cuántos clics cuesta hacer algo real</li>
	</ul>
	<p><strong>Reto base:</strong> auditar glud.org midiendo clics hasta completar 3 tareas reales.</p>
	<p><strong>Nivel reto:</strong> proponer y justificar 3 mejoras de navegación con evidencia.</p>
	<p><strong>Slides:</strong> <a href="slides/s1.html">s1.html</a></p>
</div>

<div style="background-color:#1a1b26; padding:15px; margin:10px 0; border-left:4px solid #bb9af7;">
	<h3>S2: Por qué esto se ve bien y esto otro no <a href="sesiones/s2-diseno-ui/README.md">(material)</a></h3>
	<h4>Temas</h4>
	<ul>
		<li>Tipografía y escala: tamaños que cuentan una historia</li>
		<li>Espaciado: el silencio que hace legible el ruido</li>
		<li>Color y contraste: la regla 4.5:1 y cómo verificarla</li>
		<li>Grillas y alineación: por qué tu ojo detecta lo torcido</li>
		<li>Crítica de diseño: comparar sitios buenos contra malos</li>
	</ul>
	<p><strong>Reto base:</strong> criticar una sección real de glud.org usando los 4 criterios del día.</p>
	<p><strong>Nivel reto:</strong> rediseñar esa sección en HTML/CSS estático aplicando lo aprendido.</p>
	<p><strong>Slides:</strong> <a href="slides/s2.html">s2.html</a></p>
</div>

<div style="background-color:#1a1b26; padding:15px; margin:10px 0; border-left:4px solid #e0af68;">
	<h3>S3: Cómo se diseña una página que convierte <a href="sesiones/s3-anatomia-landing/README.md">(material)</a></h3>
	<h4>Temas</h4>
	<ul>
		<li>Anatomía de una landing: nav, hero, prueba social, features, CTA final</li>
		<li>El hero: propuesta de valor clara y UN botón principal</li>
		<li>Patrones de navegación: barra completa vs hamburguesa</li>
		<li>Estados de interacción: hover, focus, error, loading</li>
		<li>Mobile-first: diseñar primero para la pantalla pequeña</li>
	</ul>
	<p><strong>Reto base:</strong> wireframe de una sección de noticias/blog para glud.org.</p>
	<p><strong>Nivel reto:</strong> justificar cada decisión de diseño por escrito (clics, jerarquía, estados).</p>
	<p><strong>Nota:</strong> este wireframe es el insumo del proyecto final de la S13.</p>
	<p><strong>Slides:</strong> <a href="slides/s3.html">s3.html</a></p>
</div>

---

## Bloque 2 — Cimientos Técnicos
**Sesiones 4-6 · el sitio como laboratorio**

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S4: Qué es JavaScript y cómo funciona su lógica <em>(en construcción)</em></h3>
	<ul>
		<li>Variables, tipos, funciones, arrays y objetos desde DevTools sobre el sitio vivo</li>
	</ul>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S5: Por qué existe TypeScript y cómo se escribe <em>(en construcción)</em></h3>
	<ul>
		<li>JS sin tipos vs TS con contratos, leyendo los tipos reales del repositorio</li>
	</ul>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S6: Qué es pnpm y por qué no npm <em>(en construcción)</em></h3>
	<ul>
		<li>package.json, lockfile, node_modules y scripts: el ecosistema de dependencias</li>
	</ul>
</div>

---

## Bloque 3 — Disección Técnica
**Sesiones 7-11 · con lente UX**

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S7: Por qué Astro y no React o Next <em>(en construcción)</em></h3>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S8: De dónde sale la agenda y los cursos <em>(en construcción)</em></h3>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S9: Cómo se implementa el diseño con Tailwind v4 <em>(en construcción)</em></h3>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S10: Cómo se siente interactuar: animaciones <em>(en construcción)</em></h3>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S11: Cómo sabes que es bueno: Lighthouse <em>(en construcción)</em></h3>
</div>

---

## Bloque 4 — Cierre
**Sesiones 12-13**

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S12: Qué más existe: React, Three.js y el ecosistema <em>(en construcción)</em></h3>
</div>

<div style="background-color:#16161e; padding:15px; margin:10px 0; border-left:4px solid #565f89;">
	<h3>S13: Construye lo que diseñaste <em>(en construcción)</em></h3>
	<p>Implementación de la sección diseñada en S3, con flujo real: issue, rama, Merge Request a <code>dev</code>.</p>
</div>

---

## Recursos Transversales

| Recurso | Descripción |
| --- | --- |
| [Sitio en producción](https://glud.org) | El caso de estudio, siempre abierto durante las sesiones |
| [Repositorio del sitio](https://gitlab.com/GLUD/glud-web/frontend/glud-website) | Fuente de verdad de todo lo que destripamos |
| [MDN Web Docs](https://developer.mozilla.org/es/) | La enciclopedia oficial de HTML/CSS/JS |
| [web.dev](https://web.dev/) | Buenas prácticas de performance y accesibilidad |
| [Contrast Checker](https://webaim.org/resources/contrastchecker/) | Verificar ratios 4.5:1 al instante |

---

<div align="center" style="margin-top:40px;">

**GLUD — Grupo GNU/Linux Universidad Distrital**

*Frontend 101 — material de estudio libre bajo licencia MIT*

[← Volver al README](README.md)

</div>
