# S1 — ¿Cómo piensa un usuario cuando usa tu sitio?

> **Pregunta guía:** piensa en el último sitio donde te perdiste y terminaste cerrando la pestaña. No era feo necesariamente: simplemente **no encontrabas lo que viniste a buscar**. Antes de leer: ¿qué era exactamente lo que fallaba ahí? La respuesta casi nunca es "los colores". Hoy aprendemos a nombrar lo que falla.

---

## Objetivos de la sesión

Al terminar vas a poder:

1. Diferenciar UX de UI sin confundirlas jamás, con tus propias palabras.
2. Explicar qué es la jerarquía visual y cómo dirige la mirada del usuario.
3. Organizar contenidos según arquitectura de información y dibujar un sitemap.
4. Usar (y no abusar de) la regla de los 3 clics.
5. Medir la experiencia de un sitio real mediante flujos de tarea.

> Esta sesión NO usa código. El criterio se entrena mirando, midiendo y discutiendo. Trae el navegador abierto en glud.org toda la clase.

---

## 1. UX vs UI: la confusión más común del oficio

| | UX (User Experience) | UI (User Interface) |
| --- | --- | --- |
| Pregunta que responde | ¿Logré lo que vine a hacer, sin fricción? | ¿Qué veo y con qué interactúo? |
| Alcance | Toda la experiencia: velocidad, flujos, textos, errores | La superficie visible: botones, colores, tipografía |
| Se mide con | Tareas completadas, clics, tiempo, frustración | Ratios de contraste, escalas, alineación |
| Falla cuando | "No encontré cómo inscribirme" | "Este botón no parece botón" |

La UI es una parte de la UX, no su sinónimo. Un sitio puede ser hermoso (UI excelente) y horrible de usar (UX pésima): como un restaurante de emplatado digno de foto pero donde el plato tarda dos horas y la cuenta viene equivocada.

### Analogía de Minecraft

- **UX es el game design completo:** la progresión (madera → piedra → hierro → diamante), los controles, cuánto tarda romper cada bloque. Es lo que hace que jugar SE SIENTA bien.
- **UI es la hotbar y los inventarios:** la superficie gráfica sobre la que actúas.

Minecraft tiene una UI modesta (cuadrados grises, sin adornos) y una UX legendaria: millones de personas pasan horas porque el sistema funciona. Nadie juega Minecraft por sus menús bonitos. Esa es la lección: **la interfaz sirve a la experiencia, no al revés**.

---

## 2. Jerarquía visual: dirigir el ojo

El usuario NO lee tu página: la escanea en orden de prioridad visual. Cuatro palancas controlan ese orden:

| Palanca | Cómo funciona | Ejemplo |
| --- | --- | --- |
| Tamaño | Lo grande se ve primero | El título del hero sobre cualquier párrafo |
| Contraste/color | Lo que resalta llama primero | Un botón relleno entre texto plano |
| Posición | Arriba e izquierda antes que abajo y derecha | Logo arriba a la izquierda |
| Espacio | Lo aislado parece importante | Un botón rodeado de aire pide clics |

Dos patrones clásicos de escaneo:

1. **Patrón F** — en páginas de lectura (artículos, documentación): el ojo barre horizontal arriba, luego baja en diagonal leyendo menos cada línea.
2. **Patrón Z** — en landings visuales con poco texto: arriba izquierda → arriba derecha → diagonal → abajo izquierda → abajo derecha.

### Analogía de Minecraft

Abre el juego sin mirar el HUD y pregúntate: ¿dónde está mi vida? Arriba, siempre, porque es lo más crítico. ¿El chat? Abajo, pequeño, porque es secundario. Mojang tomó miles de decisiones de jerarquía y las fijó en pantalla para que NUNCA tengas que buscarlas. Tu landing debe lograr lo mismo: que lo importante sea imposible de no ver.

---

## 3. Arquitectura de información y sitemap

La arquitectura de información (IA) decide **qué contenidos existen, cómo se agrupan y cómo se conectan**. El error de principiante es organizar según la estructura interna del equipo ("lo del evento", "lo que hizo Fulano") en vez de según el modelo mental del visitante ("quiero saber cuándo es el próximo evento").

El sitemap es el dibujo de esa organización: cajas por página y flechas por conexiones. No necesita herramientas elegantes; papel sirve.

Reglas prácticas:

1. Agrupa por lo que el usuario quiere HACER, no por quién produjo el contenido.
2. Cada página responde a un propósito único; si hay dos propósitos, son dos páginas.
3. Todo contenido debe ser alcanzable desde la home en un camino obvio.
4. Los nombres de navegación describen contenido ("Agenda"), no ingenio ("Nuestro mundo").

### Analogía de comida

Una carta bien hecha agrupa por lo que el comensal busca: entradas, platos fuertes, postres, bebidas. Ningún restaurante ordena la carta por orden de llegada de las recetas a la cocina. Pero eso mismo es hacer una web "sección interna A, sección interna B": organiza por la casa, no por el cliente.

### Analogía de Minecraft

Los cofres etiquetados: "Redstone", "Construcción", "Comida". Aunque internamente guardes cosas muy distintas dentro de cada uno, la etiqueta responde a la pregunta del jugador ("¿dónde está mi pollo asado?"). Un almacén de 40 cofres sin etiquetas es una web sin arquitectura de información.

---

## 4. La regla de los 3 clics: verdad útil, mentira literal

La regla dice: *cualquier contenido debe alcanzarse en máximo 3 clics desde la home*. Nació como intuición popular de los años 90 y sobrevive en oficinas hasta hoy.

La investigación posterior (NN/g y otros) la mató como ley: los usuarios toleran perfectamente 5, 6 o más clics **si cada paso les da confianza de ir bien camino**. El problema real no es el conteo, es perder la orientación.

Lo que sí importa (y sí se defiende en este curso):

1. Saber siempre DÓNDE estoy (ubicación clara).
2. Saber QUÉ puedo hacer aquí (acciones visibles).
3. Saber CUÁL es el siguiente paso si esto es lo que busco (camino evidente).

### Analogía de Minecraft

Llegar a diamantes toma decenas de pasos: bajar niveles, encontrar cuevas, minar obsidiana de camino... y nadie abandona por eso, porque las **coordenadas** te dicen dónde estás y la profundidad te dice si vas bien (más abajo = más cerca). El viaje largo funciona cuando la orientación funciona. Un sitio con 6 clics claros vence siempre a uno con 3 clics confusos.

---

## 5. Flujos de tarea: medir UX en vez de opinar

"Me parece poco usable" es opinión. Medir es distinto. El método que usaremos todo el semestre:

1. Define la tarea como la plantearía un usuario real ("averiguar cuándo es la próxima SLUD").
2. Ejecútala tú mismo contando clics y cronometrando.
3. Registra cada momento de fricción: cada segundo de duda tipo "¿dónde hago clic?".
4. Repite la misma tarea en otro dispositivo (desktop vs móvil).
5. Compara contra el mínimo teórico: ¿cuántos clics DEBERÍA costar si el diseño fuera perfecto?

La diferencia entre lo medido y el mínimo teórico es tu margen de mejora. Eso convierte la crítica en evidencia.

---

## El caso real: glud.org

Datos verificados del sitio que usaremos hoy:

1. **Lo urgente, sin clics:** la home destaca una tarjeta prominente con la SLUD (su evento anual) visible apenas carga. Buena decisión: el contenido temporal más importante no obliga a buscar.
2. **Menú dual:** barra horizontal con enlaces grandes en desktop; panel inferior deslizable (bottom sheet) con targets táctiles amplios en móvil. El patrón cambia, la orientación se conserva.
3. **Contacto en el footer:** cuatro columnas con correo oficial del grupo y seis iconos de redes sociales accesibles (con etiquetas para lectores de pantalla). El que llega al footer buscando contacto, lo encuentra.

Ahora la prueba real: ¿es tan fácil como suena? Eso lo decides tú en el reto.

---

## Reto de la sesión: auditoría de flujos de tarea

### Nivel base (obligatorio)

Sobre [glud.org](https://glud.org), ejecuta y documenta estas tres tareas:

1. Enterarte de cuándo y dónde es la próxima SLUD.
2. Encontrar el correo oficial del grupo.
3. Averiguar cómo participar en los cursos GNUBIES.

Para CADA tarea y EN CADA dispositivo (desktop + móvil), llena esta tabla:

| Tarea | Dispositivo | Clics usados | Tiempo | Momentos de confusión |
| --- | --- | --- | --- | --- |
| ... | ... | ... | ... | ... |

Entrega: la tabla completa (6 filas) con las fricciones descritas con precisión ("no vi el enlace X porque...", no "estaba difícil").

### Nivel reto (stretch)

Con tu tabla como evidencia:

1. Propón 3 mejoras de navegación concretas para glud.org.
2. Justifica cada una citando el dato medido que la respalda.
3. Priorízalas en una matriz impacto/esfuerzo simple (alto/bajo por eje) y di cuál implementarías primero y por qué.

---

## Checklist de salida

- [ ] Explico UX vs UI con un ejemplo propio (que no sea de esta lectura).
- [ ] Nombro las 4 palancas de jerarquía visual y doy un caso de cada una.
- [ ] Sé por qué la regla de los 3 clics no es ley y qué importa en su lugar.
- [ ] Medí 3 tareas reales en glud.org y tengo los números anotados.
- [ ] Mis fricciones están descritas con causa ("no encontré X"), no con sentimiento ("era confuso").
- [ ] Puedo defender una mejora concreta para el sitio con mi propia evidencia.

---

## Recursos extra

- [The 3-Click Rule Can Make or Break Your Navigation (NN/g)](https://www.nngroup.com/videos/three-click-rule/) — video corto del grupo que estudió la regla a fondo.
- [Hick's Law (Laws of UX)](https://lawsofux.com/hicks-law/) — cuántas opciones son demasiadas opciones.
- [Information Architecture (Figma)](https://www.figma.com/resource-library/what-is-information-architecture/) — introducción práctica a la IA.

---

<div align="center">

[← Indice](../../Indice.md) · [← Anterior: S0 Contexto](../s0-contexto/README.md) · [Siguiente: S2 Diseño UI →](../s2-diseno-ui/README.md)

</div>
