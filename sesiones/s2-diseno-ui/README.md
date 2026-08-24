# S2 — ¿Por qué esto se ve bien y esto otro no?

> **Pregunta guía:** hay secciones web que te relajan la vista y otras que te cansan sin que sepas decir por qué. Antes de leer: abre dos sitios cualesquiera y mira cada uno 10 segundos. ¿Cuál te pareció más "limpio"? Ahora intenta JUSTIFICARLO sin usar las palabras "bonito", "feo" ni "limpio". Ese es exactamente el músculo que entrenamos hoy: convertir sensaciones en criterios medibles.

---

## Objetivos de la sesión

Al terminar vas a poder:

1. Evaluar tipografía con criterio: familias, escala y line-height.
2. Reconocer un sistema de espaciado y detectar el espaciado aleatorio.
3. Medir contraste de color con la regla WCAG AA (4.5:1) usando herramienta, no el ojo.
4. Explicar por qué la alineación a grilla se siente aunque no se vea.
5. Aplicar un método de crítica de diseño reproducible sobre cualquier sección.

> Como ayer: cero código. Hoy entrenamos el ojo con casos reales, incluidos los defectos del propio sitio del grupo.

---

## 1. Tipografía y escala: los tamaños cuentan una historia

Reglas base para no fallar:

1. **Máximo 2 familias:** una display para títulos, una de cuerpo para lectura. Tres fuentes ya parece bazar.
2. **Escala con ratio constante:** los tamaños no son aleatorios; crecen por un multiplicador fijo. Punto de partida práctico: escala 1.25 ("major third"): 16 → 20 → 25 → 31 → 39px...
3. **Line-height según tamaño:** cuerpo cómodo (1.5–1.8), títulos apretados (1.1). El texto grande necesita menos aire entre líneas que el pequeño.

### Analogía de comida

La carta del restaurante: nombre del plato GRANDE, descripción PEQUEÑA. Funciona porque los tamaños codifican jerarquía: primero escaneo qué hay, luego leo el detalle de lo que me interesó. Si todo tuviera el mismo tamaño, la carta sería una lista inútil de texto plano.

### El caso real: glud.org

El sitio usa exactamente la pareja clásica display + cuerpo: **Exo 2 Variable** para títulos (geométrica, futurista, coherente con la identidad neón del grupo) y **Fira Sans** para párrafos (humanista, muy legible en pantalla). Dos familias, cada una con su trabajo. Además precarga ambas como woff2 subseteadas — decisión técnica que retomamos en S11.

---

## 2. Espaciado como sistema

El espaciado no es "dejar aire": es información. La ley de proximidad dice que lo cercano parece relacionado y lo lejano parece independiente. Por eso:

1. Usa múltiplos constantes: 4px u 8px (8, 16, 24, 32, 48...). Nada de 7, 13 o 22px arbitrarios.
2. El espacio AGRUPA: título pegado a su párrafo = pertenecen juntos.
3. El espacio SEPARA: mucho aire alrededor de un botón = acción principal.
4. Espaciado inconsistente = jerarquía rota, aunque nadie pueda nombrar por qué.

### Analogía de Minecraft

Abre cualquier inventario del juego: todos los slots tienen padding idéntico, siempre. Ese ritmo constante es lo que te permite encontrar tu pico en medio segundo sin leer nada. Imagina un inventario donde cada slot tiene un margen distinto: funcionaría, pero encontrarías todo más lento y no sabrías explicar la causa. Esa es la diferencia entre espaciado-sistema y espaciado-aleatorio.

---

## 3. Color y contraste: la única regla medible de esta sesión

La accesibilidad WCAG define niveles objetivos:

| Contenido | Ratio mínimo AA |
| --- | --- |
| Texto normal | 4.5 : 1 |
| Texto grande (18pt+, o 14pt bold+) | 3 : 1 |

El contraste se MIDE con herramienta ([WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)), nunca a ojo: el ojo se adapta y engaña.

Casos REALES medidos de glud.org (los usaremos en clase):

| Combinación | Ratio aprox. | Veredicto |
| --- | --- | --- |
| Cian neón `#1affff` sobre fondo oscuro | ≈ 14:1 | Excelente: sobra margen |
| Gris soporte `#8e95a1` sobre fondo `#1c1e1e` | ≈ 5.5:1 | Pasa AA, pero con margen fino |
| Blanco al 80% de opacidad | variable | Patrón frágil: hay que medir caso por caso |
| Colores hardcodeados fuera de paleta (sección evento) | varios | Deuda de diseño: rompe el sistema de tokens |

Dos avisos adicionales del mundo real:

1. Los brillos glow (`text-shadow`) difuminan el borde de las letras: aunque el ratio matemático pase, la legibilidad PERCIBIDA baja. Contraste medido ≠ percepción.
2. Un color puede pasar sobre un fondo y fallar sobre otro: mide SIEMPRE la combinación final, no el color solo.

### Analogía de comida

Arroz blanco servido en plato blanco: existe, pero no lo ves. El mismo arroz en plato negro: idéntico sabor, presencia total. El contenido era el mismo; cambió el contraste del contexto. Y leer sin contraste suficiente es cocinar en la cueva sin antorcha: técnicamente posible, miserablemente lento.

---

## 4. Grillas y alineación: lo torcido se siente

El ojo humano detecta desalineaciones al instante, aunque la mente no las nombre. Todo debe colgar de un sistema: columnas consistentes, bordes compartidos, baseline estable.

1. Define columnas y respétalas: elementos alineados comparten bordes verticales.
2. Consistencia > variedad: tres tarjetas iguales comunican orden; tres tarjetas distintas comunican descuido.
3. Grid y Flexbox llegan después en el curso (S9): hoy solo necesitas el CONCEPTO de que existe un sistema invisible detrás de toda página que "se ve ordenada".

### Analogía de Minecraft

El inventario ES una grilla perfecta: 9 columnas, celdas iguales, todo alineado a milímetro virtual. Y las góndolas del supermercado funcionan igual: productos alineados comunican orden y confianza; estantes caóticos comunican abandono. Nadie confía en comprar leche de un estante torcido.

---

## 5. Método de crítica: de la sensación al veredicto

El método reproducible que usaremos toda la sesión (y todo el semestre):

1. Mira la sección 10 segundos sin analizar. Anota la primera impresión.
2. Evalúa los 4 criterios de hoy uno por uno: tipografía, espaciado, contraste, alineación.
3. MIDE el contraste con la herramienta. Nunca declares "bajo contraste" sin número.
4. Propón UN cambio concreto por criterio (no "mejorar", sino "subir el gris X a #Y").
5. Compara contra un sitio que hagas bien en el mismo criterio: la referencia calibra tu juicio.

En clase hacemos la demo completa con dos archivos del repo: [hero-malo.html](../../material/ejemplos/hero-malo.html) y [hero-bueno.html](../../material/ejemplos/hero-bueno.html) — la MISMA información con decisiones de diseño opuestas. Ábrelos lado a lado antes de venir: intenta listar 6 diferencias y traerlas clasificadas por criterio.

---

## Reto de la sesión: crítica con evidencia

### Nivel base (obligatorio)

Elige UNA sección real de glud.org (footer, sponsors o la sección del evento SLUD) y entrega su crítica completa:

1. Primera impresión en una frase.
2. Evaluación criterio por criterio (tipografía, espaciado, contraste, alineación).
3. Ratios de contraste MEDIDOS de al menos 3 combinaciones texto/fondo de esa sección (captura del checker o números anotados).
4. Un cambio concreto propuesto por cada criterio.

### Nivel reto (stretch)

Rediseña esa misma sección en un archivo HTML/CSS estático suelto, sin frameworks (doble clic y se abre), aplicando tus propias correcciones. Entrega además una tabla antes/después con los ratios mejorados. Este ejercicio es el ensayo general del proyecto final: mismo formato de entrega, mismo estándar.

---

## Checklist de salida

- [ ] Justifico una decisión tipográfica citando familia display vs familia de cuerpo.
- [ ] Distingo espaciado-sistema de espaciado-aleatorio viendo una captura.
- [ ] Mido contraste con herramienta y sé cuándo aplica 4.5:1 vs 3:1.
- [ ] Sé por qué el glow puede arruinar un contraste que matemáticamente pasa.
- [ ] Crítica una sección completa usando el método de 6 pasos, con números incluidos.
- [ ] Mis propuestas dicen valores concretos ("subir a #Y"), no adjetivos ("más claro").

---

## Recursos extra

- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) — la herramienta oficial de este curso para contrastes.
- [Google Fonts Knowledge](https://fonts.google.com/knowledge) — teoría tipográfica aplicada, corta y visual.
- [Von Restorff Effect (Laws of UX)](https://lawsofux.com/von-restorff-effect/) — por qué lo que resalta domina la jerarquía.
- [Practical Typography](https://practicaltypography.com/) — el libro práctico de tipografía; lee los capítulos cortos.

---

<div align="center">

[← Indice](../../Indice.md) · [← Anterior: S1 Fundamentos UX](../s1-fundamentos-ux/README.md) · [Siguiente: S3 Anatomía landing →](../s3-anatomia-landing/README.md)

</div>
