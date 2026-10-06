# F0.1 — Descarga y comprueba la ISO

> **SOR · Curso de Shell · Fase 0** · **RA.01 (preparación)**  
> **Dónde trabajas:** navegador y Git Bash o PowerShell del **ORDENADOR**, todavía sin VM.  
> **Vídeo:** `B0.S.0.1 · Marko comprueba la ISO` · **20 puntos**.

> [!info] Encargo de Lucía
> «Antes de instalar el laboratorio de Marko, demuestra de dónde viene el instalador y que el archivo descargado coincide con el publicado».

## Qué necesitas entender

- **ISO:** archivo que contiene el instalador de Ubuntu Server. Todavía no es una máquina virtual.
- **SHA256:** resultado calculado a partir de los bytes del archivo. Si el valor de tu descarga coincide con el publicado en la página oficial, has comprobado su integridad respecto de esa fuente. **El hash solo no autentica a quien publicó la página**: por eso consultas la web oficial mediante HTTPS.
- **LTS:** edición con soporte prolongado. Anota la versión exacta que descargaste; no inventes el nombre del archivo.

## Procedimiento

> [!example] Paso 0 — Abre la entrada y graba
> En tu repositorio `apuntes-sor-t1`, crea vacía `B0_Curso_Shell/shell-0-preparacion-del-laboratorio.md` usando la [plantilla de entregables](../02_ENTREGABLES.md#fase-0--una-entrada-cuatro-vídeos-y-una-entrega). Abre OBS, preséntate y muestra tu identidad. Graba esta práctica completa.

> [!example] Paso 1 — Descarga de la fuente oficial (**ORDENADOR**)
> Abre [Ubuntu Server](https://ubuntu.com/download/server). Elige la ISO **Ubuntu Server LTS para la arquitectura de tu equipo**; si no sabes cuál corresponde, anótalo y consulta antes de descargar. Guarda el archivo en una carpeta local que encuentres después. Anota en la entrada la página, versión, nombre exacto del `.iso` y carpeta. En el Bloque 1 analizarás con más detalle las ediciones y arquitecturas.

> [!example] Paso 2 — Localiza la suma oficial (**ORDENADOR**)
> Desde el enlace de descarga oficial, localiza el directorio de esa misma versión en `releases.ubuntu.com` y su archivo `SHA256SUMS`. Busca allí la línea que **coincide exactamente con el nombre de tu ISO**. Copia la suma esperada y la dirección de la página a tus apuntes. Si no aparece el nombre, no uses una suma de otra versión: pide ayuda.

> [!example] Paso 3 — Calcula la suma local (**ORDENADOR**)
> Abre Git Bash en la carpeta donde está la ISO. Primero `pwd` confirma dónde estás y `ls` enseña el nombre exacto del archivo. Sustituye `NOMBRE-REAL.iso` por ese nombre:
>
> ```bash
> pwd
> ls
> sha256sum NOMBRE-REAL.iso
> ```
>
> `sha256sum` lee el archivo y calcula su huella; **no modifica la ISO**. Si el nombre contiene espacios, escríbelo entre comillas. Si Git Bash responde `command not found`, usa PowerShell en esa misma carpeta: `Get-FileHash .\NOMBRE-REAL.iso -Algorithm SHA256`. No copies el carácter `$` del prompt como parte del comando.

> [!example] Paso 4 — Compara y documenta (**ORDENADOR**)
> En tu entrada coloca juntos el SHA256 oficial y el calculado. Compáralos completos, no solo el principio. Escribe «coinciden» o «no coinciden». Si no coinciden, **detente**: comprueba el nombre y vuelve a descargar desde la fuente oficial antes de continuar.

> [!example] Paso 5 — Cierra el vídeo
> Detén OBS; sube el vídeo como «No listado» a `B0_Curso_Shell` con el nombre `B0.S.0.1 · Marko comprueba la ISO`. En la descripción añade `00:00 Presentación` y una marca por paso. Pega el enlace en el apartado F0.1 de tu entrada. La entrada se sube a GitHub **al final de la Fase 0**, no necesitas crear otra.

## Comprobación y puntuación

| Evidencia visible en vídeo y apuntes | Puntos |
| :--- | ---: |
| Fuente oficial, versión y nombre de ISO identificados | 5 |
| `SHA256SUMS` correspondiente a esa misma ISO | 5 |
| Cálculo local mostrado y coincidencia completa documentada | 8 |
| Explicas qué significa la coincidencia y qué harías si falla | 2 |

> [!question] Para responder en la entrada
> ¿Por qué el nombre del archivo junto al hash importa? ¿Qué harías si los valores no coincidieran?

**Siguiente:** [F0.2 · Crea la VM](F0-02_VM.md). · [Índice de Fase 0](README.md)
