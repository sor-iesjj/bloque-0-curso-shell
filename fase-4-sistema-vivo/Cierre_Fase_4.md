---
Tipo: cierre-de-fase
Fase: 04
Título: Cierre de la Fase 4 — El sistema vivo: servicios, paquetes y red
---

## 🏁 Cierre de la Fase 4 — El sistema vivo: servicios, paquetes y red

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. La Fase 5 da por sabido todo lo que hay aquí, así que si algo no lo tienes claro, **para y repásalo** (o pregúntame) antes de seguir.

---

## 🎓 Lo que has aprendido en la Fase 4

- Qué es un **servicio** y qué es **systemd**: `status`, `is-active`, `start`, `stop`, `restart`, `reload`.
- Que **`start` y `enable` son cosas distintas**, comprobado con un reinicio real.
- `mask` y por qué Boochan tiene que hacer `unmask samba-ad-dc`.
- A leer un servicio caído con `journalctl -u ... -n 30 --no-pager`, y a **validar la configuración antes de reiniciar**.
- `apt` y `dpkg`: la diferencia entre `remove` y `purge`, y los estados `ii` y `rc`.
- A descomponer *"no hay red"* en loopback, tarjeta y salida, con `ip`, `ping -c2` e `ip route`.
- `ss -tlnp` para saber quién ocupa un puerto, y la diferencia entre `0.0.0.0` y `127.0.0.1`.
- A separar **"hay camino"** de **"hay DNS"**, y que `/etc/hosts` gana al DNS.
- Procesos: `ps`, `top`, `pgrep`, y `kill` frente a `kill -9`.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. ¿Por qué es peligroso hacer `restart` de un servicio del que dependes?
> 2. Explica la diferencia entre `is-active` e `is-enabled` y por qué hay que mirar las dos.
> 3. ¿Por qué el mensaje de `systemctl` no basta para diagnosticar?
> 4. ¿Qué diferencia hay entre `apt remove` y `apt purge`, y qué problema causa confundirlos?
> 5. ¿Por qué `ping 8.8.8.8` y `ping google.com` prueban cosas distintas?
> 6. Un servicio está `active` pero desde fuera no se conecta nadie. Da **dos** causas posibles.
> 7. ¿Por qué se empieza por `kill` y no por `kill -9`?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Comprobar si un servicio está vivo por dos vías distintas | ☐ |
> | Dejar un servicio funcionando **y** configurado para el arranque | ☐ |
> | Encontrar en el log la causa de un servicio caído | ☐ |
> | Validar una configuración antes de reiniciar | ☐ |
> | Eliminar un paquete sin dejar residuos y demostrarlo | ☐ |
> | Descomponer un "no hay red" en tres pruebas | ☐ |
> | Averiguar qué proceso ocupa un puerto | ☐ |
> | Distinguir un fallo de red de uno de DNS | ☐ |
> | Localizar un proceso que consume y terminarlo bien | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 4

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | Funcionaba y tras reiniciar no está | `start` sin `enable` | `enable --now`, y comprueba `is-enabled`. |
> | `Unit is masked` | El paquete lo deja bloqueado | `sudo systemctl unmask`. |
> | Reinicio el servicio y sigue fallando | No has leído el log | `journalctl -u X -n 30 --no-pager`. |
> | `Could not resolve host` | Es DNS, no red | `ping 8.8.8.8` + `getent hosts` + `cat /etc/resolv.conf`. |
> | El puerto está ocupado y no sé por quién | Falta `sudo` o falta `-p` | `sudo ss -tlnp`. |
> | `umount: target is busy` | Algo usa la carpeta | `fuser -v` o `lsof +D`. Y `cd ~` primero. |

---

> [!tip] Siguiente paso
> Cuando tengas la tabla de verificación completa, pasa a la **Fase 5 — Discos, montajes y fstab**: dónde viven los datos de verdad, y por qué a veces desaparecen.

**Siguiente:** [Fase 5 — Discos, montajes y fstab](../fase-5-discos-y-montajes/README.md)
