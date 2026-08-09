---
Tipo: cierre-de-fase
Fase: 01
Título: Cierre de la Fase 1 — La terminal y el árbol de ficheros
---

## 🏁 Cierre de la Fase 1 — La terminal y el árbol de ficheros

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. La Fase 2 da por sabido todo lo que hay aquí, así que si algo no lo tienes claro, **para y repásalo** (o pregúntame) antes de seguir.

---

## 🎓 Lo que has aprendido en la Fase 1

- Qué es una **máquina virtual** y por qué se aprende Linux dentro de una.
- A leer el **prompt**: usuario, máquina, carpeta y si eres root.
- La diferencia entre **ruta absoluta** y **ruta relativa**, y cuándo usar cada una.
- A listar con `ls` (`-l -a -h -d -R`) y a leer ficheros con `cat`, `less`, `head` y `tail`.
- A crear, copiar, mover y borrar — y a temer a `rm -rf`.
- A editar con **nano** y la **regla del `.bak`**: copia antes de tocar `/etc`.
- Tab, historial, `Ctrl`+`R`, `!!` y los atajos de control.
- A resolver dudas tú solo con `man`, `--help` y `apropos`.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. Explica la diferencia entre ruta absoluta y relativa con **un ejemplo tuyo**.
> 2. ¿Por qué el material de Boochan escribe siempre las rutas enteras en vez de moverse con `cd`?
> 3. ¿Qué cambia al añadir `-d` a `ls -l` y cuándo lo necesitas?
> 4. ¿Cuál es la costumbre que te protege de un `rm -rf` mal escrito, y por qué funciona?
> 5. ¿Por qué se hace la copia `.bak` **antes** de editar y no después?
> 6. ¿Por qué se dice que el Tab **verifica**, además de completar?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Moverme a cualquier ruta y saber dónde estoy | ☐ |
> | Leer un fichero sin abrir un editor | ☐ |
> | Distinguir `ls -l` de `ls -ld` | ☐ |
> | Crear una estructura con `mkdir -p` | ☐ |
> | Editar `/etc/hosts` con copia previa y restaurarla | ☐ |
> | Comprobar un cambio con `diff` | ☐ |
> | Completar rutas con Tab y buscar en el historial | ☐ |
> | Resolver una duda de opciones en el `man` | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 1

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | `cd carpeta` no funciona | Ruta relativa desde donde no era | Usa la ruta absoluta, o comprueba con `pwd`. |
> | No puedo salir de `less` o de `man` | Es un paginador | `q`. |
> | `Permiso denegado` al guardar en nano | Falta `sudo` | `sudo nano`. Mira el aviso de solo lectura al abrir. |
> | He borrado lo que no era | `rm -rf` con la ruta mal | `ls -ld` con la MISMA ruta antes de borrar. |
> | `ls -l` no me enseña los permisos de la carpeta | Te enseña los de su contenido | `ls -ld`. |

---

> [!tip] Siguiente paso
> Cuando tengas la tabla de verificación completa, pasa a la **Fase 2 — Identidad y permisos clásicos**: quién eres para el sistema, y por qué unos entran y otros no.

**Siguiente:** [Fase 2 — Identidad y permisos clásicos](../fase-2-identidad-y-permisos/README.md)
