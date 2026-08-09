---
Tipo: cierre-de-fase
Fase: 07
Título: Cierre de la Fase 7 — Leer y escribir un script de bash
---

## 🏁 Cierre de la Fase 7 — Leer y escribir un script de bash

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. Es también el cierre del curso entero. Léelo con calma.

---

## 🎓 Lo que has aprendido en la Fase 7

- Qué hace falta para un script: **shebang**, `chmod +x` y `./`.
- **Variables**: el `=` pegado, el `$` al usar, y las comillas dobles siempre.
- **`$( )`** para capturar la salida de un comando, y que una sustitución fallida deja la variable vacía **en silencio**.
- El bucle **`for`**, sus cuatro formas de lista, y el **ensayo con `echo`** antes de ejecutar.
- Que **`if` mira códigos de salida**, que `[ ]` es un comando y **necesita espacios**.
- **`while IFS= read -r ... <<< "$VAR"`** para recorrer líneas, y qué hace cada pieza.
- **Expansión de parámetros**: `${x%:*}`, `${x#*:}`, `${x//-/}`, `${x:-0}`.
- **Funciones**, contadores con `$(( ))`, veredicto y `exit 0` / `exit 1`.
- A **leer** un script de bash real de trescientas líneas.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. ¿Por qué el directorio actual no está en el `PATH`?
> 2. Explica las tres reglas de sintaxis de una variable en bash.
> 3. ¿Por qué es peligroso que una sustitución de comandos falle en silencio?
> 4. ¿Por qué `[ "$A"="$B" ]` es **siempre cierto**?
> 5. ¿Cuándo usarías `for` y cuándo `while IFS= read -r`?
> 6. Explica la diferencia entre `${x%:*}` y `${x#*:}` y qué pasa si los confundes en una matriz.
> 7. ¿Por qué las funciones se definen antes de llamarlas?
> 8. ¿Por qué el `verificar_fase7.sh` de Boochan **no** usa `set -e`?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Convertir una secuencia repetida en un script ejecutable | ☐ |
> | Usar variables para que la ruta se escriba una sola vez | ☐ |
> | Capturar la salida de un comando con `$( )` | ☐ |
> | Escribir un `for` y ensayarlo con `echo` antes | ☐ |
> | Escribir un `if` que compare y no mienta | ☐ |
> | Recorrer una matriz línea a línea y partirla en campos | ☐ |
> | Leer `${regla%:*}` y decir qué devuelve sin ejecutarlo | ☐ |
> | Escribir funciones, contar fallos y dar un veredicto | ☐ |
> | Leer un `verificar_faseN.sh` de Boochan y explicarlo | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 7

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | `orden no encontrada` con el script delante | Falta `./` | `./script.sh`. |
> | `Permiso denegado` al ejecutar | Falta `chmod +x` | `chmod +x script.sh`. |
> | `VAR: orden no encontrada` | Espacios alrededor del `=` | `VAR=valor`, pegado. |
> | Mi `if` siempre entra | Faltan espacios dentro de `[ ]` | `[ "$A" = "$B" ]`. |
> | El bucle da una vuelta con todo junto | Has entrecomillado la lista | La lista sin comillas, los usos con comillas. |
> | `orden no encontrada` al llamar a mi función | Definida después | Las funciones, arriba. |
> | Error de sintaxis raro en una comparación | La variable quedó vacía | `"$VAR"` y `${VAR:-0}`. |

---

> [!success] 🎓 Has terminado el curso de Shell
> Empezaste sin haber abierto una terminal. Ahora lees un script de bash de trescientas líneas, montas una matriz de permisos con ACL y diagnosticas un servidor caído sin reiniciar a ciegas.
>
> **Lo que viene ahora es el Bloque 2: Boochan.** Y la diferencia con quien no ha hecho este curso es que tú, cuando veas `setfacl -m g:comercial:rx`, vas a saber qué estás escribiendo.

> [!question] Última pregunta, y va en serio
> Vuelve a la nota que escribiste en el reto de la Fase 1 (`EJ-01-05-01`), cuando te pedí que **predijeras** qué haría falta para que comercial no entrara en RRHH. Léela ahora.
>
> ¿Qué has aprendido desde entonces? Escríbelo. Esa distancia es el curso.

**Siguiente:** el **Bloque 2 — Boochan**. Nos vemos en la Fase 1.
