---
Tipo: cierre-de-fase
Fase: 06
Título: Cierre de la Fase 6 — ACL: cuando los permisos clásicos no bastan
---

## 🏁 Cierre de la Fase 6 — ACL: cuando los permisos clásicos no bastan

> [!info] Para qué es esta página
> No es un ejercicio nuevo y **no se graba**: es una parada para consolidar. La Fase 7 da por sabido todo lo que hay aquí, así que si algo no lo tienes claro, **para y repásalo** (o pregúntame) antes de seguir.

---

## 🎓 Lo que has aprendido en la Fase 6

- Por qué los permisos clásicos **no pueden** con tres grupos, demostrado con tres intentos fallidos.
- A leer `getfacl -p` línea a línea, y qué significa el **`+`** de `ls -l`.
- `setfacl -m` con `g:` y `u:`, y que en carpetas **lectura es `rx`**.
- `setfacl -x` y `-b`, y a guardar/restaurar ACL como copia de seguridad.
- La **máscara** y la marca **`#effective`** — y que `chmod` la cambia sin avisar.
- La **ACL por defecto** (`-d`) para el futuro y `-R` para el pasado: hacen falta las dos.
- El **orden de evaluación**, y que la entrada de usuario **gana** a la de grupo.
- Que las **carpetas padre** hacen falta para llegar, y es el fallo que más se olvida.
- A auditar una estructura: entradas, `#effective`, `default:` y **lo que no debe existir**.

---

## ❓ Preguntas de repaso

> [!question] Responde en tus apuntes antes de seguir
> Con tus palabras. Si la respuesta es copiar una línea del ejercicio, no cuenta.
> 1. Explica por qué los permisos clásicos no pueden cumplir una matriz de tres grupos. Cuenta las casillas.
> 2. ¿Cuál es la diferencia entre `group::rwx` y `group:contabilidad:rwx`?
> 3. ¿Por qué en carpetas se da `rx` y no `r`?
> 4. ¿Qué es la máscara, a quién afecta y a quién no?
> 5. ¿Por qué un `chmod` en una carpeta con ACL es peligroso?
> 6. Explica la diferencia entre `-m`, `-d -m` y `-R -m`.
> 7. ¿Por qué una auditoría necesita también la lista de prohibiciones?
> 8. Un compañero dice "a mí me funciona" probándolo con `sudo`. ¿Por qué eso no demuestra nada?

---

## ✅ Tabla de verificación (¿sé hacerlo yo solo?)

> [!success] Marca solo lo que puedas hacer SIN mirar los apuntes
> | Sé… | ¿Sí? |
> | :--- | :---: |
> | Explicar por qué `chmod` no puede con la matriz | ☐ |
> | Leer un `getfacl -p` entero y emparejarlo con `ls -l` | ☐ |
> | Dar acceso a un segundo grupo sin tocar los permisos clásicos | ☐ |
> | Quitar una entrada concreta sin tocar las demás | ☐ |
> | Detectar un `#effective` y arreglarlo sin tocar las entradas | ☐ |
> | Conseguir que lo nuevo nazca con la ACL puesta | ☐ |
> | Verificar un permiso con `sudo -u`, positivo y negativo | ☐ |
> | Diagnosticar una ACL que no funciona con mi checklist de seis puntos | ☐ |
> | Auditar una estructura y detectar lo que sobra | ☐ |

---

## 🚑 Errores frecuentes de toda la Fase 6

> [!bug] Si algo falla, empieza por aquí
> | Síntoma | Causa habitual | Solución |
> | :--- | :--- | :--- |
> | Doy `r` a un grupo y no abren nada | Falta la `x` de travesía | En carpetas, `rx`. |
> | El permiso figura y no funciona | La máscara lo recorta | `getfacl | grep "#effective"` y `setfacl -m m::rwx`. |
> | Funcionaba y con los ficheros nuevos falla | Falta la ACL por defecto | `setfacl -d -m ...`. |
> | La ACL está bien y no se llega | Falta `x` en una carpeta padre | `ls -ld` de toda la cadena, o `namei -l`. |
> | `setfacl: Operation not supported` | El sistema de ficheros no tiene ACL | Comprueba el montaje. En `ext4` van por defecto. |
> | Toca a un usuario y pierde permisos que tenía | Su entrada de usuario gana a la de grupo | El sistema para en la primera coincidencia. |

---

> [!tip] Siguiente paso
> Cuando tengas la tabla de verificación completa, pasa a la **Fase 7 — Scripts**: leer y escribir el bash que hasta ahora era magia negra.

**Siguiente:** [Fase 7 — Leer y escribir un script de bash](../fase-7-scripts/README.md)
