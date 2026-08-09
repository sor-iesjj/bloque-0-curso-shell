---
Tipo: cierre-de-fase
Fase: 03
Título: Cierre de la Fase 3 — Redirección, tuberías y texto
---

## 🏁 Cierre de la Fase 3 — Redirección, tuberías y texto

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. La Fase 4 da por sabido todo lo que hay aquí, así que si algo no lo tienes claro, **para y repásalo** (o pregúntame) antes de seguir.

---

## 🎓 Lo que has aprendido en la Fase 3

- A **redirigir** con `>` (machaca) y `>>` (añade), y el patrón de informe.
- Que hay **tres canales**: stdin, stdout y **stderr**, y a redirigirlos por separado (`2>/dev/null`, `2>&1`).
- La **tubería `|`**, y que los errores **no pasan** por ella.
- `grep` de verdad: `-i -n -c -v -r -q -w -E` y el ancla `^`.
- `cut`, `sort`, `uniq -d` y `wc` — y que `uniq` sin `sort` **miente en silencio**.
- Por qué `sudo comando > /etc/…` falla, y el patrón `| sudo tee -a`.
- Las **comillas**: sin comillas, `"dobles"` y `'simples'`, y por qué `'DOMINIO\usuario'` va en simples.
- `sed -i` con sus tres pasos seguros: copia, ensayo, aplicar.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. ¿Cuántas veces usas `>` al construir un informe de diez secciones, y por qué?
> 2. Explica qué hace `>/dev/null 2>&1` y cuándo lo usarías.
> 3. ¿Por qué los errores no pasan por la tubería?
> 4. ¿Por qué `grep -c "facturacion"` y `grep -c "^\[facturacion\]"` dan resultados distintos?
> 5. ¿Por qué `uniq` necesita `sort` delante?
> 6. Explica, como si se lo contaras a un compañero atascado, por qué falla `sudo echo "x" > /etc/fichero`.
> 7. ¿Por qué `sudo -u 'BOOCHANLAB\masao.sato'` lleva comillas simples?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Construir un informe por secciones sin machacar nada | ☐ |
> | Separar la salida normal de los errores en dos ficheros | ☐ |
> | Responder a una pregunta del sistema con una tubería de tres | ☐ |
> | Contar apariciones de una sección con `grep -c` y `^` | ☐ |
> | Detectar duplicados con `sort | uniq -d` | ☐ |
> | Escribir en `/etc` con `| sudo tee -a` | ☐ |
> | Explicar los tres tipos de comillas con ejemplos propios | ☐ |
> | Hacer una sustitución con `sed` ensayando antes | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 3

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | Mi informe solo tiene la última sección | `>` en cada línea | `>` una vez, `>>` el resto. |
> | Los errores siguen saliendo por pantalla | `>` solo redirige stdout | Añade `2>` o `2>&1`. |
> | `ls -l /etc > grep conf` no filtra | Confundir `|` con `>` | `|` a comando, `>` a fichero. |
> | Busco algo y no aparece, pero está | Diferencia de mayúsculas | `grep -i` la primera vez. |
> | `sudo echo ... > /etc/x` da Permiso denegado | El `>` lo hace tu shell | `| sudo tee`. |
> | Una ruta con espacios falla | Variable sin comillas | `"$VAR"` siempre. |

---

> [!tip] Siguiente paso
> Cuando tengas la tabla de verificación completa, pasa a la **Fase 4 — El sistema vivo**: servicios, paquetes, red y procesos. Diagnosticar en vez de adivinar.

**Siguiente:** [Fase 4 — El sistema vivo: servicios, paquetes y red](../fase-4-sistema-vivo/README.md)
