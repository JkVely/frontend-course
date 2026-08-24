# S3 — ¿Cómo se diseña una página que convierte?

> **Pregunta guía:** has entrado a cientos de sitios web. En algunos supiste al instante qué hacer siguiente; en otros te sentiste perdido y cerraste la pestaña. Antes de leer: piensa en **un sitio donde te perdiste** y en **uno donde no**. ¿Qué era diferente? Trae tu respuesta: la vamos a nombrar técnicamente hoy.

---

## Objetivos de la sesión

Al terminar vas a poder:

1. Nombrar las secciones estándar de una landing page y qué trabajo hace cada una.
2. Diseñar (o criticar) un hero: propuesta de valor clara y una sola acción principal.
3. Elegir entre navegación completa y menú hamburguesa con argumentos, no con moda.
4. Definir los estados de interacción de cualquier componente que diseñes.
5. Aplicar mobile-first: diseñar primero lo pequeño, expandir después.
6. Producir un wireframe justificado de una sección nueva para glud.org.

> **Aviso importante:** el wireframe que produces hoy NO es un ejercicio desechable. Es el insumo directo del proyecto final (S13), donde esa misma sección se implementa y se envía como Merge Request real al repositorio del grupo. Diseña como si fuera a producción, porque lo va a estar.

---

## 1. La anatomía de una landing page

Una landing (página de aterrizaje) bien construida responde las preguntas del usuario **en orden**, de arriba hacia abajo:

```
+------------------------------------------+
|  NAV: logo + enlaces + CTA pequeño       | <- ¿Quién eres y dónde navego?
+------------------------------------------+
|                                          |
|  HERO:                                   | <- ¿Qué me ofreces?
|  - Titulo grande con propuesta de valor  |
|  - Un parrafo de apoyo                   | <- ¿Por qué me debería importar?
|  - CTA principal (+ secundario opcional) | <- ¿Que hago ahora?
|                                          |
+------------------------------------------+
|  PRUEBA SOCIAL: logos, numeros, testimonios | <- ¿Quien mas confía?
+------------------------------------------+
|  FEATURES: beneficios concretos          | <- ¿Que gano exactamente?
|  [tarjeta] [tarjeta] [tarjeta]           |
+------------------------------------------+
|  CTA FINAL: repite la accion principal   | <- Ultima llamada
+------------------------------------------+
|  FOOTER: enlaces, contacto, legal        | <- Lo que busco cuando ya decidi
+------------------------------------------+
```

### Analogía de comida

Una landing es la **fachada y la carta de un restaurante**:

- La **nav** es la entrada: ves el nombre, el letrero, y sabes por dónde moverte.
- El **hero** es el plato destacado del día escrito en grande en la pizarra: si ese texto no te antoja, no entras.
- La **prueba social** son las mesas llenas visibles desde la calle: "si hay gente, debe ser bueno".
- Las **features** son la descripción de ingredientes: el detalle que convence al que ya estaba interesado.
- El **CTA final** es el mesero que vuelve a preguntar justo cuando terminabas de decidir.

### El caso real: glud.org

Abre [glud.org](https://glud.org) y verifica la anatomía en vivo. Fíjate cómo el hero cumple casi todo el libro:

1. Un badge superior ("Comunidad GNU/Linux") que contextualiza.
2. Un título gigante con identidad visual fuerte (cian neón sobre oscuro).
3. Un párrafo que explica qué es el grupo y a quién sirve.
4. Dos botones: uno primario relleno y uno secundario solo bordeado.
5. Tres estadísticas debajo (los números también venden).

**Discusión en clase:** el sitio tiene dos botones, y la regla clásica dice "un solo CTA". ¿Está violando su propia regla? Spoiler: no. La regla real es **una sola acción primaria**. El botón secundario (bordeado, menos peso visual) atiende a quien ya sabe programar y quiere algo distinto al visitante curioso. Jerarquía sí, dogmatismo no.

---

## 2. El hero: los primeros 5 segundos

El usuario decide quedarse o irse en segundos. El hero es la única parte del diseño que TODOS ven, así que concentra ahí la claridad:

1. **Propuesta de valor:** en una frase, qué es esto y para quién es.
2. **Un verbo de acción:** el botón dice qué pasa al presionarlo ("Únete", "Ver agenda", "Aprender más"). Nunca "Enviar", nunca "Click aquí".
3. **Un solo foco visual:** si todo grita, nada escucha.

### Analogía de Minecraft

El hero es la **hotbar** del juego: máximo 9 slots, siempre visibles, siempre iguales. Podrían ser 27 slots (todo el inventario), pero entonces encontrar tu espada en medio de una pelea sería imposible. La restricción ES el diseño. Tu hero igual: pocas cosas, perfectas, visibles.

---

## 3. Navegación: barra completa vs hamburguesa

| Patrón | Ventaja | Costo |
| --- | --- | --- |
| Barra completa | Todo visible, un clic a cualquier lado | Ocupa espacio horizontal |
| Hamburguesa | Compacta, limpia | Oculta las opciones (fuera de vista, fuera de mente) |

La regla práctica: en desktop, barra completa casi siempre. En móvil, la hamburguesa es aceptable **si** el menú que revela está bien hecho (targets grandes, cierre obvio, no atrapa al usuario).

### El caso real: glud.org

El sitio usa ambos patrones según el ancho de pantalla: barra completa con enlaces grandes en desktop, y en móvil una hamburguesa que abre un panel inferior tipo hoja deslizable, con enlaces de buen tamaño táctil y un botón accesible (`aria-label`, `aria-expanded`). Es un ejemplo local de que la hamburguesa puede hacerse bien. Lo destripamos técnico en S7; hoy nos queda el patrón.

### Analogía de comida

La hamburguesa es el **menú del día escrito en una pizarra dentro de la cocina**: ahorra pared, pero si el cliente no sabe que existe, pide lo único que vio afuera. Cada cosa que escondes detrás de un clic reduce la probabilidad de que sea encontrada. Por eso los restaurantes ponen la pizarra donde todos la vean.

---

## 4. Estados de interacción: el diseño que nadie nota

Todo elemento interactivo vive en varios estados, y cada uno necesita diseño explícito:

| Estado | Cuando ocurre | Qué comunica |
| --- | --- | --- |
| Reposo (default) | Nadie toca nada | Esto es interactivo |
| Hover | El cursor encima | Estás apuntando a esto |
| Focus | Se llega con Tab / teclado | Estoy aquí parado (crítico para accesibilidad) |
| Active | Se está presionando | Recibí tu clic |
| Loading | Esperando respuesta | Está trabajando, espera |
| Error | Algo falló | Esto salió mal y por qué |
| Disabled | No disponible | No puedes usar esto ahora |

> **El pecado confeso de glud.org:** el sitio cuida sus hovers (subrayados animados, brillos) pero **no define ningún estado `:focus-visible`** propio: quien navega solo con teclado depende del contorno por defecto del navegador, que se pierde fácil sobre fondo oscuro con neón. Es un error real, documentado, y será reto de arreglo en sesiones futuras. Moraleja: hasta el admin peca, y documentarlo nos enseña a todos.

### Analogía de comida

Los estados son la **temperatura del plato al tocarlo**: tibio comunica "recién servido" (hover), humeante comunica "está listo, cómelo" (active), y un plato frío en mesa comunica "algo pasó aquí" (error). Si el mesero no reacciona a nada (sin hover ni feedback), el cliente duda de que alguien lo esté atendiendo.

---

## 5. Mobile-first: primero el refugio, después el castillo

Diseñar mobile-first significa empezar por la pantalla pequeña (donde cabe poco y sobra nada) y luego expandir hacia pantallas grandes:

1. En móvil caben pocas cosas: obliga a priorizar. Si algo no cabe en móvil, quizá no era tan importante.
2. Expandir siempre es más fácil que recortar: agregar columnas a una grilla duele menos que quitar secciones completas.
3. La mayoría del tráfico real de sitios universitarios llega desde el celular.

### Analogía de Minecraft

Nadie empieza su primera noche construyendo un castillo de cuarzo. Empiezas con un refugio de tierra que cumpla lo esencial (no morir), y sobre esa base segura construyes después la fortaleza. El refugio ES tu diseño móvil: funcional, mínimo, honesto. El castillo es el desktop, donde sobra espacio para decoración.

> **Dato del sitio real:** glud.org mantiene versiones desktop y mobile separadas de varias secciones (las clases `landing-desktop` y `landing-mobile` existen como árboles gemelos en el HTML). Funciona, pero paga un precio: contenido duplicado que se mantiene dos veces y errores nuevos en dos lugares. En S7 discutimos alternativas más sanas (responsive con un solo árbol). Hoy guárdate la pregunta: ¿cómo harías tú una sola estructura que sirva para ambos tamaños?

---

## 6. Wireframes: el plano antes de los bloques

Un wireframe es el boceto estructural de una página: cajas, textos placeholder, jerarquía. Sin colores, sin tipografías bonitas, sin imágenes reales. Solo respuestas a tres preguntas: **qué va, dónde va y por qué ahí**.

Herramientas válidas para este curso:

1. Papel y lápiz (el mejor: cero fricción, cero excuses).
2. Excalidraw (gratis, online, dibujo suelto).
3. Figma (gratis en plan personal, más formal).

### Analogía de Minecraft

El wireframe es el **plano que trazas con bloques de lana antes de levantar la construcción definitiva**: defines dimensiones, ubicación de puertas y ventanas gastando materiales baratos. Si el plano está mal, cambias lana, no piedra. En S13 vas a construir con piedra (código real); hoy todo es lana.

---

## Reto de la sesión: diseñar la sección de noticias/blog de glud.org

El grupo necesita publicar noticias, convocatorias y posts del blog. Hoy diseñas esa sección; en S13 la implementas de verdad.

### Nivel base (obligatorio)

1. Elige papel, Excalidraw o Figma.
2. Wireframea la vista principal de la sección de noticias considerando:
   - Cómo llega el usuario desde la nav principal (¿nuevo enlace? ¿dropdown?).
   - La lista de noticias: ¿tarjetas? ¿lista? ¿cuántas visibles?
   - La vista de detalle de una noticia individual.
   - Versión mobile Y versión desktop (mobile-first: hazla primero).
3. Reglas mínimas: aplica la anatomía de landing donde aplique, define el hero de la sección, y marca claramente cuál es LA acción principal.

### Nivel reto (stretch)

Además del wireframe, entrega una **justificación escrita** (media página) que responda:

1. ¿Cuántos clics cuesta llegar de la home a leer una noticia completa? Justifica ese número.
2. ¿Qué estados definiste para tus tarjetas/botones (hover, focus, loading)?
3. ¿Qué sacrificaste al pasar de desktop a móvil y por qué fue correcto sacrificarlo?

---

## Checklist de salida

- [ ] Dibujo de memoria la anatomía de una landing (6 secciones, en orden).
- [ ] Explico por qué un hero lleva UNA acción primaria y reconozco la excepción legítima del doble botón.
- [ ] Puedo defender en voz alta cuándo usar hamburguesa vs barra completa.
- [ ] Nombro los 7 estados de interacción sin mirar la tabla.
- [ ] Mi wireframe de noticias tiene versión mobile, versión desktop y una acción principal marcada.
- [ ] Sé exactamente qué decisión mía voy a tener que defender cuando esto llegue a código en S13.

---

## Recursos extra

- [Landing pages: anatomía (web.dev)](https://web.dev/articles/lcp?hl=es-419) — además conecta el concepto con performance (LCP), que retomaremos en S11.
- [Excalidraw](https://excalidraw.com/) — para wireframes rápidos compartibles.
- [Ley de Hick (NN/g)](https://www.nngroup.com/articles/minimize-cognitive-load/) — cuántas opciones son demasiadas opciones.

---

<div align="center">

[← Indice](../../Indice.md) · [← Anterior: S2 Diseño UI](../s2-diseno-ui/README.md)

</div>
