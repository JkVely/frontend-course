# S5 — TypeScript: tipos que hablan antes de que rompa

> **Pregunta guía:** abre la Consola en glud.org y escribe: `const edad = "veintiuno"; console.log(edad + 5)`. En JavaScript el resultado es `"veintiun005"`. ¿Te gustaría que el navegador te avise *antes* de ejecutar que estás sumando texto con número? TypeScript es el guardián que lo hace.

---

## Objetivos de la sesión

Al terminar vas a poder:

1. Explicar por qué JavaScript es **dinámicamente tipado** y qué costo tiene.
2. Instalar y configurar TypeScript en un proyecto Astro/HTML.
3. Declarar variables con tipos (`number`, `string`, `boolean`, `array`, `objeto`, `any`).
4. Usar **interfaces** para describir formas de datos.
5. Comprender `union types`, `literal types` y `null/undefined`.
6. Leer errores de compilación y usarlos para corregir código antes de ejecutar.
7. Conectar lo aprendido con el caso real: cómo TypeScript protege los datos del formulario de SLUD y la lógica de eventos.

> TypeScript es JavaScript, pero con contratos. No cambia cómo corre el navegador, cambia *cuándo* te enteras de los errores.

---

## 1. El problema: JavaScript no avisa hasta que corre

En JS los tipos se deciden en tiempo de ejecución. Eso permite rapidez, pero también errores silenciosos:

```javascript
let edad = 21
edad = "veintiuno"   // válido en JS
console.log(edad + 5) // → "veintiuno5"
```

El error aparece cuando el usuario usa la página. TypeScript mueve la verificación a **tiempo de compilación**: antes de subir nada, el compilador revisa contratos.

Paralelo Minecraft: JS es como construir con redstone a prueba y error; TS es como tener el circuito dibujado en papel, revisado, y luego montarlo. Si el papel está mal, no llega a la partida.

---

## 2. Instalar y configurar TypeScript

En un proyecto Astro/HTML:

```bash
corepack pnpm add -D typescript
npx tsc --init
```

`tsconfig.json` mínimo:

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "ESNext",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  }
}
```

Esto hace que el compilador sea estricto: no permite `any` implícito, exige inicialización, etc.

---

## 3. Declarar con tipos

```typescript
let nombre: string = "Mónica"
let edad: number = 21
const activo: boolean = true

let tags: string[] = ["frontend", "astro"]
let colores: Array<string> = ["rojo", "verde"]

let usuario: { nombre: string; edad: number } = {
  nombre: "Andrés",
  edad: 19
}
```

Si cambias el tipo, el compilador te avisa:

```typescript
nombre = 123  // Error: Type 'number' is not assignable to type 'string'
```

### Ejercicio en clase (5 min)

Declara las siguientes variables con su tipo correcto:

```typescript
let ciudad: string
let miembros: number
let activo: boolean
let cursos: string[]
let perfil: { nombre: string; activo: boolean }

ciudad = "Bogotá"
miembros = 250
activo = true
cursos = ["Frontend 101", "Linux Avanzado"]
perfil = { nombre: "GLUD", activo: true }
```

Ejecuta `pnpm tsc` y corrige cualquier error que aparezca. Comparte el primer error que encontraste y cómo lo solucionaste.

---

## 4. Interfaces: la forma de los datos

Un objeto con forma definida:

```typescript
interface Estudiante {
  nombre: string
  edad: number
  cursos?: string[]   // opcional
  activo: boolean
}

const estudiante: Estudiante = {
  nombre: "Daniela",
  edad: 20,
  activo: true
  // cursos es opcional
}
```

Ventaja: si alguien cambia la propiedad `nombre` a `name`, TypeScript lo señala en todos los usos.

### Ejercicio en clase (7 min)

Crea una interfaz `EventoGLUD` con:

- nombre: string
- fecha: string
- inscritos: number
- gratuito: boolean

Crea un objeto que cumpla la interfaz y verifica que el compilador acepte. Luego intenta quitar una propiedad obligatoria y observa el error.

---

## 5. Union types y literal types

Permite múltiples tipos:

```typescript
type Rol = "estudiante" | "profesor" | "admin"

function saludar(rol: Rol) {
  console.log(`Hola ${rol}`)
}

saludar("estudiante") // ok
saludar("invitado")   // Error
```

Literal types protegen el flujo: una variable no puede ser solo "cualquier string", puede ser exactamente "activo" | "inactivo".

### Ejercicio en clase (7 min)

Declara `type EstadoFormulario = "vacío" | "relleno" | "enviado"`. Crea una variable con ese tipo e intenta asignarle "aprobado". ¿Qué ocurre?

---

## 6. null, undefined y strict null checks

Con `strict: true`, TypeScript distingue `null`/`undefined`:

```typescript
let valor: string | null = null
valor = "hola"

// valor.length funciona porque el compilador sabe que no es null ahora
```

Patrón seguro:

```typescript
if (valor !== null) {
  console.log(valor.length)
}
```

---

## 7. El caso real: glud.org con tipos

Imagina que el botón de copiar correo recibe datos de un objeto:

```typescript
interface BotonCopiar {
  email: string
  textoVisor: string
}

function copiar(boton: BotonCopiar) {
  // lógica de copiar al portapapeles
}
```

Si alguien pasa `{ mail: "..." }` en lugar de `email`, TypeScript lo detecta antes de desplegar. En JS ese error aparece cuando el usuario hace clic y el botón no hace nada.

En el formulario de inscripción SLUD:

```typescript
interface Inscripcion {
  nombre: string
  correo: string
  cursoId: number
}
```

Con tipos, no puedes enviar un número donde va un correo. Eso evita correos inválidos en la base de datos.

---

## Reto después de clase

1. Crea un archivo `tipos.ts` con:
   - Interfaz `Usuario` con nombre, edad, cursos.
   - Función `presentar(usuario: Usuario): string` que devuelva `"Hola, soy X, tengo Y años"`.
2. Ejecuta `pnpm tsc tipos.ts --noEmit` y asegura cero errores.
3. Intenta pasar un objeto incompleto a `presentar` y documenta el error que devuelve el compilador.

---

## Checklist de salida

- [ ] Explico por qué JavaScript es dinámicamente tipado y qué riesgo implica.
- [ ] Declaro variables con tipos y arreglo errores del compilador.
- [ ] Defino interfaces y las uso para modelar datos.
- [ ] Uso union types y literal types para restringir valores.
- [ ] Entiendo `null`/`undefined` en modo strict.

---

## Recursos extra

- TypeScript Handbook — Basic Types
- TypeScript Handbook — Advanced Types
- TS Playground

[Índice](../Indice.md) · [← Anterior: S4 JavaScript](../s4-javascript/README.md) · [Siguiente: S6 → Astro →](../s6-astro/README.md)
