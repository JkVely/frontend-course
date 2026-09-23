# S4 — JavaScript desde DevTools

> **Pregunta guía:** abre glud.org, presiona `F12`, pestaña **Consola**, y escribe:
>
> ```javascript
> document.title = "Tú mandas"
> ```
>
> La pestaña cambió de nombre. Ningún programa externo hizo eso: lo ejecutaste tú, dentro del navegador. Hoy aprendemos a usar ese poder con intención.

---

## Objetivos de la sesión

Al terminar vas a poder:

1. Explicar qué es JavaScript y **dónde se ejecuta** (en el navegador del visitante, no en tu servidor).
2. Usar la **Consola de DevTools** como laboratorio: ejecutar expresiones, guardar valores, probar ideas sin instalar nada.
3. Declarar variables (`const`, `let`) y usar los tipos básicos: string, number, boolean, array, objeto.
4. Acceder a elementos de una página con el **DOM** (`querySelector`) y leer su contenido.
5. Modificar el DOM en tiempo real: texto, estilos, clases.
6. Escuchar eventos del usuario (`addEventListener`) y responder con código.
7. Leer errores en la Consola y depurar con `console.log`.

> Hoy el navegador es el IDE. Nada se instala; todo se prueba al momento.

---

## 1. JavaScript corre en el navegador del visitante

Cuando una página tiene comportamiento — un menú que se desliza, un botón que copia texto, un contador que sube — hay JavaScript ejecutándose. Y se ejecuta **en la máquina del usuario**, no en el servidor.

| Concepto | Qué es | Analogía |
| --- | --- | --- |
| **Expresión** | Código que produce un valor | Una pregunta que el motor responde |
| **Sentencia** | Una orden que hace algo (`document.title = ...`) | Una instrucción que das al navegador |
| **Declaración** | Darle nombre a un valor (`const nombre = "GLUD"`) | Poner una etiqueta a un objeto |

El motor JS interpreta todo en la máquina de quien visita. Por eso "poco JavaScript" significa "página más rápida": el visitante no tiene que descargar ni ejecutar tanto.

### En la consola ahora

Abre cualquier página, pulsa `F12` → **Consola**, y escribe:

```javascript
2 + 3
typeof "GLUD"
typeof 42
document.body.innerText
document.body.children.length
```

La Consola es un REPL: lee, evalúa, imprime, repite.

### Paralelo Minecraft

La redstone en tu mundo: cuando pisas una placa de presión y la puerta se abre, eso no pasa en el servidor de Mojang — tu PC calcula esa lógica. JavaScript es tu redstone: cablea eventos dentro del navegador del visitante.

---

## 2. Tipos: qué valores puedes guardar

```javascript
const nombre = "Mónica"
const edad = 21
let puntos = 0

const activa = true

const materiales = ["piedra", "madera", "hierro"]
materiales.length
materiales[0]

const grupo = {
  nombre: "GLUD",
  miembros: 250,
  activos: true
}
grupo.nombre
```

Regla práctica: `typeof valor` responde `"string"`, `"number"`, `"boolean"`, `"object"`, `"undefined"` o `"function"`.

### Ejercicio en clase (5 min)

```javascript
const estudiante = "Daniela"
let puntos = 0
let vistaPremium = false

console.log(typeof estudiante)
console.log(typeof puntos)
console.log(typeof vistaPremium)
console.log(estudiante.length)
```

Comparte en el chat un resultado que no esperabas. `typeof []` da `"object"` — es la discusión de hoy.

---

## 3. Funciones: empaquetar decisiones

```javascript
function saludar(nombre) {
  return "Hola, " + nombre + ", ¿cómo va tu curso?"
}

saludar("Mónica")
```

Versión moderna:

```javascript
const despedirse = (nombre) => "Chao, " + nombre
```

Regla mnemotécnica: **entrada → decisión → salida**. Si no tiene `return`, no devuelve nada.

### Ejercicio en clase (7 min)

```javascript
function formatearNombre(nombre) {
  const limpio = nombre.trim()
  return limpio.charAt(0).toUpperCase() + limpio.slice(1)
}

console.log(formatearNombre("  daniela "))
console.log(formatearNombre("  MÓNICA "))
```

Actividad: corrige la función para que el resultado sea siempre capitalizado correctamente. Comparte la solución.

---

## 4. El DOM: cómo JavaScript toca la página

El DOM es el árbol de elementos HTML como objetos accesibles.

```javascript
const titulo = document.querySelector("h1")
const botones = document.querySelectorAll("button")

console.log(titulo.innerText)
titulo.innerText = "Cursos del GLUD"
titulo.style.color = "#1affff"
titulo.classList.add("grande")
```

`querySelector` devuelve el **primer** elemento. Si necesitas todos, usa `querySelectorAll`.

### Ejercicio en clase (10 min) — tocando glud.org

1. Glud.org abierto, `F12` → Consola.
2. Lee el primer h1:

```javascript
const titulo = document.querySelector("h1")
console.log(titulo.innerText)
```

3. Modifícalo:

```javascript
titulo.style.color = "#ff9e64"
titulo.innerText = "Frontend 101 2026"
```

4. Pregunta: ¿qué se pierde si este cambio se hace solo con CSS?

---

## 5. Eventos

```javascript
const burger = document.querySelector(".menu-toggle")
burger.addEventListener("click", () => {
  console.log("Click")
  document.body.classList.toggle("menu-abierto")
})
```

Patrón: elemento → tipo de evento → función a ejecutar.

### Ejercicio en clase (10 min) — clic contador

```javascript
let totalClics = 0
document.addEventListener("click", () => {
  totalClics++
  console.log(`Clic número ${totalClics}`)
})
```

Cambia el evento a `"mouseover"` y observa cómo cambia el comportamiento.

---

## 6. El caso real: glud.org

La mayoría del sitio es estático (SSG). Lo que JS sí hace:

| Script | Qué hace | Por qué JS |
| --- | --- | --- |
| Menú hamburguesa | Alterna clases `.open`, maneja `aria-expanded` | Sin JS no abre |
| Copiar correo | Usa `navigator.clipboard.writeText` | Portapapeles necesita JS |
| Navegación al hacer scroll | Marca enlace activo según sección visible | Evento de scroll |
| Carga ligera | Todo en CDN, ~8 KB propios | De S0 |

### Ejercicio de inspección (5 min)

```javascript
document.querySelectorAll("button").length
document.querySelectorAll("script").length
document.scripts[0]?.src
```

Compartan cuántos scripts carga la página y qué hacen.

---

## Reto después de clase

1. Abre glud.org y en la Consola crea un `<div id="contador">`.
2. Añade un botón y un contador que incremente con cada clic.
3. Usa `addEventListener` para conectar botón y contador.

Entrega: captura del código en la Consola y el resultado visible.

---

## Checklist de salida

- [ ] Explico que JS corre en el navegador del visitante.
- [ ] Declaro variables con `const`/`let` y distingo tipos.
- [ ] Escribo funciones con `return`.
- [ ] Selecciono elementos con `querySelector` y leo/modifico su contenido.
- [ ] Registro un `addEventListener` y cuento eventos.

---

## Recursos extra

- MDN — Introducción al DOM
- MDN — Introducción a eventos
- javascript.info — La consola

[Índice](../Indice.md) · [← Anterior: S3](../s3-anatomia-landing/README.md) · [Siguiente: S5 TypeScript →](../s5-typescript/README.md)
