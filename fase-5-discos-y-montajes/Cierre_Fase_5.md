---
Tipo: cierre-de-fase
Fase: 05
Título: Cierre de la Fase 5 — Discos, montajes y fstab
---

## 🏁 Cierre de la Fase 5 — Discos, montajes y fstab

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. La Fase 6 da por sabido todo lo que hay aquí, así que si algo no lo tienes claro, **para y repásalo** (o pregúntame) antes de seguir.

---

## 🎓 Lo que has aprendido en la Fase 5

- `df -h` para el espacio libre y `du -sh` para lo que ocupa una carpeta, y a bajar hasta el culpable.
- Qué es un **punto de montaje**, y que la carpeta original **sigue debajo**.
- `dd` y `mkfs.ext4` para fabricar y formatear un volumen — y por qué a `dd` se le llama *disk destroyer*.
- `mount -o loop`, qué es un **dispositivo de bucle** y que un montaje manual **no sobrevive a un reinicio**.
- Los **seis campos** de `/etc/fstab` y `mount -a` como ensayo general obligatorio.
- El **modo emergencia**: provocarlo, reconocerlo y salir. Y la opción `nofail`.
- El **fichero fantasma**: por qué es silencioso, cómo se recupera y cómo se evita.
- `lsblk`, `blkid`, `findmnt` y `stat -c` para inspeccionar con datos exactos.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. Explica la diferencia entre `df` y `du`, y en qué orden los usarías.
> 2. ¿Qué es un punto de montaje y qué queda debajo?
> 3. ¿Por qué un fichero de ceros no sirve hasta que se formatea?
> 4. ¿Por qué `mount -a` es imprescindible antes de reiniciar?
> 5. ¿Qué es un fichero fantasma y por qué no da ningún error?
> 6. ¿Cuál es el orden correcto: crear la estructura o montar? ¿Por qué?
> 7. ¿Por qué `stat -c` es mejor que `ls -l | awk` para un script?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Localizar quién ocupa el disco en tres comandos | ☐ |
> | Distinguir un punto de montaje de una carpeta normal | ☐ |
> | Fabricar y formatear una imagen de disco | ☐ |
> | Montarla a mano y demostrar que no persiste | ☐ |
> | Escribir una línea de `fstab` y probarla con `mount -a` | ☐ |
> | Salir de un modo emergencia sin reinstalar | ☐ |
> | Provocar, diagnosticar y recuperar un fichero fantasma | ☐ |
> | Sacar el dueño, grupo y permisos exactos con `stat -c` | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 5

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | El disco está lleno y `df -h /` dice que no | Otro volumen es el lleno | `df -h` completo. |
> | `wrong fs type, bad option, bad superblock` | Falta el `mkfs` | Formatea antes de montar. |
> | Al reiniciar el montaje ha desaparecido | Montaje manual | Declararlo en `/etc/fstab`. |
> | `You are in emergency mode` | Error en `fstab` | `mount -o remount,rw /`, arreglar `fstab`, reiniciar. Y `mount -a` la próxima vez. |
> | Mis ficheros han desaparecido al montar | Ficheros fantasma | Desmonta y míralos debajo. Luego vacía la carpeta subyacente. |
> | `umount: target is busy` | Estás dentro | `cd ~` primero. |

---

> [!tip] Siguiente paso
> Cuando tengas la tabla de verificación completa, pasa a la **Fase 6 — ACL**: cuando tres casillas de permisos no llegan. Es la Fase 7 de Boochan, entera.

**Siguiente:** [Fase 6 — ACL: cuando los permisos clásicos no bastan](../fase-6-acl/README.md)
