# Guía del Estudiante

> **Cómo funciona Frontend 101:** este documento explica la mecánica de las sesiones, cómo se evalúan los retos y el flujo de trabajo que vas a usar todo el semestre. Léelo completo antes de la primera sesión.

---

## Antes de empezar: qué necesitas instalar

No instales nada por adelantado si no te sientes seguro: la Sesión 0 se dedica completa a dejar tu equipo listo. Esta es la lista para que sepas a dónde vamos:

1. **Git** — control de versiones.
2. **Node.js 20+** — el motor que ejecuta JavaScript fuera del navegador.
3. **pnpm** — gestor de paquetes (se activa con `corepack`, no se instala aparte).
4. **VS Code** — editor de código con extensiones recomendadas en clase.

---

## Mecánica de cada sesión (2 horas)

| Minuto | Actividad | Qué haces tú |
| --- | --- | --- |
| 0-15 | Pregunta guía | Propones hipótesis sin ver código todavía |
| 15-45 | Disección en vivo | Sigues la navegación por el sitio real; preguntas libre |
| 45-85 | Hands-on | Trabajas tu reto en tu propio clon del sitio |
| 85-100 | Revisión social | Muestras tu resultado y comentas el de otros |
| 100-110 | Cierre | Recibes la lectura de la siguiente sesión |

> **La regla de oro:** no hay pregunta tonta. Si algo no quedó claro, el momento de preguntar es ese mismo minuto, no "después en casa".

---

## Los retos: dos niveles en cada sesión

### Nivel base (obligatorio)

Alcanzable desde cero con lo visto en clase y el material de la sesión. Si terminas el nivel base, ya entendiste la sesión.

### Nivel reto (stretch goal)

Para quien ya vuela o termina rápido. Suele exigir investigar un paso más allá de lo explicado. Quien hace nivel reto también funge de **mentor de mesa**: ayuda a los demás durante el hands-on, porque enseñar es la mejor forma de consolidar.

> **Elegir mal es normal:** si un día tomas el nivel reto y no lo logras, nada pasa. El único fracaso permitido es no intentar el nivel base.

---

## Rúbrica de evaluación (desde S1)

Los retos se autoevalúan contra esta checklist antes de mostrarlos en la revisión social:

| Criterio | Pregunta que debes hacerte |
| --- | --- |
| Funciona | Hace lo que pedía el reto, sin pasos rotos |
| Se entiende | Otra persona puede mirarlo y explicar qué hace |
| Justificado | Puedes responder por qué tomaste cada decisión |
| Entregado a tiempo | Estaba listo al iniciar la revisión social |

> **Sin notas ni exámenes:** el curso aprueba con asistencia (mínimo 10 de 14 sesiones) y con el proyecto final entregado en S13. La rúbrica existe para darte criterio, no para asustarte.

---

## Flujo de trabajo con Git (el que usaremos siempre)

Este taller usa el mismo flujo del grupo GLUD en producción. Lo aprenderás usándolo:

```
main        # Producción: solo sale aquí vía merge request
dev         # Integración: donde se prueban los cambios juntos
feat/*      # Tu rama personal de trabajo
```

1. Se crea un issue describiendo el trabajo.
2. Desde `dev` se crea una rama propia (`feat/mi-cambio`).
3. Se trabaja y se hacen commits semánticos (`feat(agenda): filtro por mes`).
4. Se abre un Merge Request hacia `dev`.
5. Alguien más revisa y aprueba.
6. Merge. Nunca se commitea directo sobre `main`.

> En las primeras sesiones este flujo lo hacemos guiados. Para la S13 abrirás tu MR solito, como en la vida real del grupo.

---

## Cómo estudiar el material

Cada sesión tiene su carpeta en [`sesiones/`](../Indice.md) con un `README.md` estructurado igual:

1. **Pregunta guía** — inténtala responder ANTES de leer la teoría. En serio.
2. **Teoría + analogías** — los conceptos abstractos vienen con analogías cotidianas; si una analogía no te cuadra, busca la tuya: esa memoria personal vale más que la mía.
3. **En el sitio real** — ejemplos concretos de glud.org, con aciertos y errores propios incluidos.
4. **Reto base / nivel reto** — el hands-on.
5. **Checklist de salida** — si puedes marcar todas, dominaste la sesión.

---

## Reglas de convivencia del taller

1. Se critica el diseño, nunca a la persona que lo hizo.
2. El código de otro se comenta con respeto y con motivo ("¿por qué usaste grid aquí?" y no "esto está feo").
3. Todo error propio que aparezca en clase es material público de estudio: el admin del sitio también se equivoca, y documentarlo nos enseña a todos.
4. Celulares para mirar el sitio responsive, no para distraerse. Bueno... al menos eso intentamos.

---

<div align="center">

[← Volver al Índice](../Indice.md)

</div>
