# F0.1 — Descarga y comprueba la ISO en Windows
> **Recorrido:** COLE · Este documento pertenece solo a `SOR_Shell_Cole/Boveda_Shell_Cole`. No uses la bóveda del otro contexto. El curso se mantiene fuera de la carpeta SOR para evitar que una orden ejecutada por despiste dañe tus apuntes reales.


> **SOR · Curso de Shell · Fase 0** · **Preparación de RA.01**
> **Dónde:** navegador, Explorador de archivos y PowerShell **del ordenador Windows**. Todavía no hay VM ni se usa Linux.

> **Canal Teams:** `00.03.00.F001` · Publicación del guion y su PDF. La tarea independiente de entrega cubre Fase 0 completa para COLE.
> **Vídeo:** `B0.S.F0 · Marko prepara el laboratorio Shell · COLE` · **Playlist:** `B0_Curso_Shell_F0_Cole` · **Vídeo final de Fase 0** · **20 puntos**.

> [!info] Encargo de Lucía
> «Antes de instalar nada, comprueba que el archivo que vas a usar procede de Ubuntu y que la descarga no ha cambiado por el camino».

## Antes de hacer clic: qué significan estas palabras

- **ISO:** el archivo que descargaremos en Windows para instalar Ubuntu Server en una máquina virtual. Piensa en él como un DVD de instalación guardado en un solo archivo. Su nombre termina en `.iso`.
- **Huella o hash SHA256:** un programa lee el archivo completo y produce una cadena de caracteres. Ubuntu publica la cadena correspondiente al archivo original. Si tu descarga da la misma cadena, sus bytes coinciden con los del archivo al que se refiere la lista oficial. Si da otra, **no se instala**. La comparación sirve para detectar cambios o errores de descarga; por sí sola no demuestra quién escribió la página web.
- **`SHA256SUMS`:** lista publicada por Ubuntu que contiene nombres de archivos y sus huellas SHA256. La línea elegida tiene que nombrar **exactamente** tu ISO.
- **PowerShell:** terminal incluida en Windows. En esta práctica se usa para calcular la huella del archivo guardado en el disco de Windows. No vamos a ejecutar ningún comando Linux.

## Antes de grabar

1. Lee **todos** los pasos de esta página, incluidos la verificación y la entrega.
2. Antes de descargar una ISO de varios GB, abre **Configuración de Windows → Sistema → Acerca de** y comprueba «Tipo de sistema»: debe indicar un procesador x64. Si indica ARM o no sabes distinguirlo, detente y consulta; esta guía usa Ubuntu Server amd64.
3. Ten preparado el navegador, el Explorador de archivos, OBS y una forma de mostrar tu identidad (por ejemplo, tu perfil de Teams o tu correo del centro). Evita mostrar datos que no formen parte de la práctica.
4. En Obsidian, comprueba que tienes la nota `Boveda_Shell_Cole/Apuntes_Shell_Cole/Fase_0/shell-0-preparacion-del-laboratorio-cole.md`. Si aún no existe, vuelve al [índice de este recorrido](README.md) y sigue el apartado 3 antes de continuar.
5. Abre esa nota y localiza el título **«F0.1 · ISO»**. Es el apartado donde escribirás los resultados de esta práctica. Conserva los otros tres apartados para las prácticas siguientes.
6. Comprueba dónde OBS guardará las grabaciones de trabajo. Al terminar F0.4 unirás los tramos en un vídeo final llamado **`B0.S.F0 · Marko prepara el laboratorio Shell · COLE`**.

## Procedimiento

> [!example] Paso 0 — Empieza la grabación (**WINDOWS**)
> - **0A.** Inicia OBS y pulsa «Iniciar grabación».
> - **0B.** Preséntate, muestra tu identidad y di: «Voy a descargar Ubuntu Server y comprobar en Windows la huella de la ISO».
> - **0C.** Muestra el apartado **«F0.1 · ISO»** de tu nota de apuntes, aún sin resultados. Ahí documentarás lo que ocurra, incluidos los fallos.

> [!example] Paso 1 — Descarga la ISO oficial (**WINDOWS**)
> - **1A.** En el navegador, abre [la página oficial de Ubuntu Server 24.04](https://releases.ubuntu.com/24.04/).
> - **1B.** Localiza el archivo `ubuntu-24.04.5-live-server-amd64.iso`, indicado como imagen de instalación de servidor para PC de 64 bits (AMD64). Esta práctica usa Ubuntu Server 24.04 LTS amd64. Si no ves ese archivo o la página oficial muestra otra versión, detente y consulta al profesor antes de descargar; no uses una imagen ARM.
> - **1C.** Descarga el `.iso` en una carpeta del disco de Windows que puedas localizar. Al terminar, abre el **Explorador de archivos** y ve a esa carpeta.
> - **1D.** Bajo **«F0.1 · ISO»** de tu nota, escribe la dirección de la página, la versión mostrada y el **nombre real** del archivo. No uses un nombre de ejemplo en tus apuntes.

> [!example] Paso 2 — Busca la huella publicada por Ubuntu (**WINDOWS**)
> - **2A.** Abre el [`SHA256SUMS` de Ubuntu 24.04](https://releases.ubuntu.com/24.04/SHA256SUMS). Localiza la línea que nombra exactamente `ubuntu-24.04.5-live-server-amd64.iso`. **No uses otra línea ni una suma de otro directorio.** Si el archivo oficial del Paso 1 ya no coincide con ese nombre, detente y consulta al profesor.
> - **2B.** Abre `SHA256SUMS` en el navegador. Cada línea contiene una huella y el nombre de un archivo. Busca **el mismo nombre** que viste en el Explorador.
> - **2C.** Bajo **«F0.1 · ISO»** de tu nota, copia la huella de esa línea y la dirección web del `SHA256SUMS`. Si el nombre no coincide, **detente**: puede ser otra versión y esa huella no sirve para tu descarga.

> [!example] Paso 3 — Calcula la huella de TU archivo con PowerShell (**WINDOWS**)
> - **3A.** Mantén abierto el Explorador **dentro de la carpeta que contiene la ISO**. Mira el nombre del archivo antes de escribir el comando.
> - **3B.** Haz clic en la **barra de direcciones** del Explorador, escribe `powershell` y pulsa `Enter`. Se abrirá PowerShell situada en esa carpeta. Si la política del equipo impide abrirlo, anota el mensaje y avisa al profesor; no cambies la configuración del equipo.
> - **3C.** En PowerShell escribe `Get-ChildItem` y pulsa `Enter`. Este comando **muestra** los archivos de la carpeta; comprueba que aparece tu `.iso`. Si no aparece, estás en otra carpeta: vuelve al Explorador y repite 3A–3B.
> - **3D.** Sustituye `NOMBRE-REAL.iso` por el nombre exacto que acabas de ver, **manteniendo las comillas**. El ejemplo no se puede copiar sin cambiarlo:
>
> ```powershell
> Get-FileHash -LiteralPath '.\NOMBRE-REAL.iso' -Algorithm SHA256
> ```
>
> - **3E. Qué hace la línea:** `Get-FileHash` lee el archivo y calcula la huella; `-LiteralPath` indica qué archivo leer; `'.\NOMBRE-REAL.iso'` señala el archivo en la carpeta actual; `-Algorithm SHA256` usa el mismo cálculo que la lista oficial. **No borra ni modifica la ISO.** Copia el valor del campo `Hash` bajo **«F0.1 · ISO»** de tu nota. Si aparece «no se encuentra la ruta», comprueba carpeta y nombre antes de repetir.
>
> - **3F. Si PowerShell está bloqueado en tu equipo:** vuelve al Explorador, entra en la carpeta de la ISO y usa «Open Git Bash here / Abrir Git Bash aquí», que ya utilizaste en el curso de Git. Ejecuta este bloque sustituyendo el nombre de ejemplo por el nombre real:
>
> ```bash
> pwd
> ls
> sha256sum 'NOMBRE-REAL.iso'
> ```
>
> **Línea 1:** muestra la carpeta actual. **Línea 2:** lista los archivos y permite comprobar que aparece la ISO. **Línea 3:** lee el archivo de Windows desde Git Bash y calcula su huella; no estás dentro de Ubuntu. Copia la cadena anterior al nombre. Si tampoco puedes abrir Git Bash, anota el mensaje y consulta sin cambiar las políticas del ordenador.

> [!example] Paso 4 — Compara y decide (**WINDOWS**)
> - **4A.** Bajo **«F0.1 · ISO»** de tu nota, coloca una debajo de otra la huella de `SHA256SUMS` y la que calculaste en Windows.
> - **4B.** Compara **todos** los caracteres. Mayúsculas y minúsculas en letras hexadecimales representan el mismo valor; si cambia algún carácter, las huellas no coinciden.
> - **4C.** Escribe «Coinciden: puedo usar esta ISO» o «No coinciden: no instalo esta ISO». Si no coinciden, primero comprueba que elegiste la línea del archivo correcto; después vuelve a descargar desde la página oficial y repite el cálculo. No pases a F0.2 con una ISO distinta de la comprobada.

> [!example] Paso 5 — Guarda la evidencia para el vídeo final (**WINDOWS**)
> - **5A.** Muestra en pantalla la comparación y explica con tus palabras qué comprobaste. Detén OBS.
> - **5B.** No subas todavía un vídeo. Guarda este tramo para el único vídeo final de Fase 0, que presentarás al terminar F0.4 en la playlist `B0_Curso_Shell_F0_Cole`.
> - **5C.** Al montar el vídeo final, añade a su descripción `00:00 Presentación` y una marca de tiempo para cada bloque de la fase. Pega el único enlace del vídeo final en la línea «Vídeo final de Fase 0» al principio de tu nota cuando cierres F0.4. La nota se sube al repositorio al completar la fase.

## Cómo se puntúa y qué compruebas

| Evidencia que debe verse en vídeo y apuntes | Puntos |
| :--- | ---: |
| Página oficial, versión, carpeta y nombre real de la ISO | 3 |
| Línea correcta del `SHA256SUMS` de esa versión | 4 |
| Comando de PowerShell o alternativa de Git Bash ejecutado sobre el archivo correcto y valor de la huella anotado | 6 |
| Comparación completa, decisión y explicación de qué hacer si falla | 2 |
| Respuestas 1–5 de esta práctica en la nota: un punto por respuesta correcta y explicada | 5 |

> [!question] F0.1 · Responde las cinco preguntas bajo «F0.1 · ISO» de tu nota
> Usa los números «F0.1.1» a «F0.1.5» de la plantilla y contesta con tus palabras después de hacer la comprobación. No copies el enunciado como respuesta.
>
> 1. **F0.1.1.** ¿Qué es un archivo ISO, dónde lo guardaste y para qué lo usarás en esta fase?
> 2. **F0.1.2.** ¿Qué contiene `SHA256SUMS` y por qué has elegido la línea que nombra exactamente tu archivo?
> 3. **F0.1.3.** ¿Qué comando utilizaste en Windows para calcular la huella de tu ISO? Explica qué archivo leyó y dónde viste el resultado. Si usaste Git Bash porque PowerShell estaba bloqueado, indica el comando que realmente ejecutaste.
> 4. **F0.1.4.** ¿Qué significa que coincidan las dos huellas? ¿Qué aspecto no demuestra esta comparación por sí sola?
> 5. **F0.1.5.** Si las huellas no coinciden, ¿qué compruebas primero y qué haces antes de pasar a F0.2?

**Siguiente:** [F0.2 · Crea la VM](F0-02_VM.md). · [Índice de Fase 0](README.md)
