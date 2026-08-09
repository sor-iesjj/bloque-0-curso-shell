---
Tipo: cierre-de-fase
Fase: 02
Título: Cierre de la Fase 2 — Identidad y permisos clásicos
---

## 🏁 Cierre de la Fase 2 — Identidad y permisos clásicos

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. La Fase 3 da por sabido todo lo que hay aquí, así que si algo no lo tienes claro, **para y repásalo** (o pregúntame) antes de seguir.

---

## 🎓 Lo que has aprendido en la Fase 2

- Que el sistema te identifica por **UID** y **GID**, no por tu nombre.
- La diferencia entre **grupo principal** y **grupos secundarios**, y que un grupo nuevo no se aplica hasta reiniciar sesión.
- Qué hace `sudo` de verdad, y `sudo -u` para **probar permisos desde la piel de otro**.
- A leer una línea de `ls -l` entera: siete campos y diez caracteres.
- Que la **`x` de un directorio es atravesarlo**, no ejecutarlo — y que el peaje se cobra en cada tramo.
- Que **propiedad** (`chown`) y **permisos** (`chmod`) son cosas distintas.
- Permisos en **octal** y en **simbólico**, y a traducir entre los dos con cuatro dígitos.
- **setgid** (`2770`) y **sticky bit** (`1777`): qué problema real resuelve cada uno.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. Explica la diferencia entre tu grupo principal y un grupo secundario.
> 2. ¿Por qué `chmod 770` no arreglaba el problema y `chown` sí?
> 3. ¿Qué significa la `x` en un directorio? ¿Por qué la lectura útil es `r-x` y no `r--`?
> 4. Traduce `drwxrws---` a octal y explica de dónde sale cada dígito.
> 5. ¿Qué te avisa una `S` mayúscula en `ls -l`?
> 6. ¿Por qué borrar un fichero depende de la carpeta y no del fichero?
> 7. ¿Por qué una prueba negativa vale más que una positiva en una configuración de permisos?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Explicar mi salida de `id` campo a campo | ☐ |
> | Usar `sudo -u` para comprobar un permiso | ☐ |
> | Desmontar una línea de `ls -l` en sus siete campos | ☐ |
> | Explicar por qué un fichero `644` puede no ser legible | ☐ |
> | Traducir `2770` ↔ `drwxrws---` sin mirar la tabla | ☐ |
> | Cambiar un solo permiso con `chmod g+w` sin tocar el resto | ☐ |
> | Montar una carpeta de equipo con setgid y demostrar la herencia | ☐ |
> | Montar una carpeta común con sticky bit y demostrar que protege | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 2

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | `usermod -G` me ha sacado de mis grupos | Faltaba la `-a` | Siempre `usermod -aG`. |
> | Doy permisos al grupo y sigue sin funcionar | El grupo dueño es el equivocado | `chown root:grupo` primero, `chmod` después. |
> | `Permission denied` sobre un fichero `644` | Falta `x` en alguna carpeta del camino | `namei -l ruta` o `ls -ld` de cada tramo. |
> | `chmod g=w` ha roto el acceso | `=` reemplaza la terna entera | `+` añade, `=` reemplaza. |
> | El setgid no arregla lo que ya había | Solo afecta a lo nuevo | `chgrp -R` para lo viejo. |
> | Aplico `2770` y no sé si se aplicó | `ls` contesta en letras | `stat -c '%a %A'`: los dos idiomas de golpe. |

---

> [!tip] Siguiente paso
> Cuando tengas la tabla de verificación completa, pasa a la **Fase 3 — Redirección, tuberías y texto**: dejar de leer salidas a ojo y empezar a preguntarle cosas concretas al sistema.

**Siguiente:** [Fase 3 — Redirección, tuberías y texto](../fase-3-tuberias-y-texto/README.md)
