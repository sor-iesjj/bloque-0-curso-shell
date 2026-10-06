# F0.1 — Descarga y comprueba la ISO en Windows

> **SOR · Curso de Shell · Fase 0** · **Preparación de RA.01**
> **Dónde:** navegador, Explorador de archivos y PowerShell **del ordenador Windows**. Todavía no hay VM ni se usa Linux.
> **Vídeo:** `B0.S.0.1 · Marko comprueba la ISO` · **Playlist:** `B0_Curso_Shell` · **20 puntos**.

> [!info] Encargo de Lucía
> «Antes de instalar nada, comprueba que el archivo que vas a usar procede de Ubuntu y que la descarga no ha cambiado por el camino».

## Antes de hacer clic: qué significan estas palabras

- **ISO:** el archivo que descargaremos en Windows para instalar Ubuntu Server en una máquina virtual. Piensa en él como un DVD de instalación guardado en un solo archivo. Su nombre termina en `.iso`.
- **Huella o hash SHA256:** un programa lee el archivo completo y produce una cadena de caracteres. Ubuntu publica la cadena correspondiente al archivo original. Si tu descarga da la misma cadena, sus bytes coinciden con los del archivo al que se refiere la lista oficial. Si da otra, **no se instala**. La comparación sirve para detectar cambios o errores de descarga; por sí sola no demuestra quién escribió la página web.
- **`SHA256SUMS`:** lista publicada por Ubuntu que contiene nombres de archivos y sus huellas SHA256. La línea elegida tiene que nombrar **exactamente** tu ISO.
- **PowerShell:** terminal incluida en Windows. En esta práctica se usa para calcular la huella del archivo guardado en el disco de Windows. No vamos a ejecutar ningún comando Linux.

## Antes de grabar

1. Lee **todos** los pasos de esta página, incluidos la verificación y la entrega.
2. Ten preparado el navegador, el Explorador de archivos, OBS y una forma de mostrar tu identidad (por ejemplo, tu perfil de Teams o tu correo del centro). Evita mostrar datos que no formen parte de la práctica.
3. Abre en tus apuntes la **única entrada de la Fase 0**, `B0_Curso_Shell/shell-0-preparacion-del-laboratorio.md`, dentro del repositorio `apuntes-sor-t1`. Copia la [plantilla de entregables](../02_ENTREGABLES.md) y deja F0.1 lista para rellenar. **No esperes al final para crearla.**
4. Comprueba que sabes dónde OBS guardará el vídeo. El nombre final será **`B0.S.0.1 · Marko comprueba la ISO`**.

## Procedimiento

> [!example] Paso 0 — Empieza la grabación (**WINDOWS**)
> - **0A.** Inicia OBS y pulsa «Iniciar grabación».
> - **0B.** Preséntate, muestra tu identidad y di: «Voy a descargar Ubuntu Server y comprobar en Windows la huella de la ISO».
> - **0C.** Muestra la entrada F0.1 vacía: será donde documentes lo que ocurra, incluidos los fallos.

> [!example] Paso 1 — Descarga la ISO oficial (**WINDOWS**)
> - **1A.** En el navegador, abre [la página oficial de Ubuntu Server](https://ubuntu.com/download/server).
> - **1B.** Localiza la descarga **LTS** adecuada para el tipo de equipo indicado por el profesor. LTS significa que Ubuntu mantiene esa versión durante más tiempo. **No adivines** la arquitectura: si la página ofrece varias y no sabes cuál corresponde a tu equipo, anótalo y pregunta antes de descargar.
> - **1C.** Descarga el `.iso` en una carpeta del disco de Windows que puedas localizar. Al terminar, abre el **Explorador de archivos** y ve a esa carpeta.
> - **1D.** Copia en F0.1 la dirección de la página, la versión mostrada y el **nombre real** del archivo. No uses un nombre de ejemplo en tus apuntes.

> [!example] Paso 2 — Busca la huella publicada por Ubuntu (**WINDOWS**)
> - **2A.** Si en el Paso 1 descargaste **Ubuntu Server 26.04.1 LTS**, abre en el navegador el [`SHA256SUMS` oficial de Ubuntu 26.04](https://releases.ubuntu.com/26.04/SHA256SUMS): contiene la línea de `ubuntu-26.04.1-live-server-amd64.iso`. **Comprueba que ese es el nombre real de tu archivo antes de usar esa línea.** Si la página de descarga ofrece otra versión cuando hagas la práctica, busca el `SHA256SUMS` del directorio oficial de **esa otra versión** en `releases.ubuntu.com`; no uses por costumbre el enlace de 26.04.
> - **2B.** Abre `SHA256SUMS` en el navegador. Cada línea contiene una huella y el nombre de un archivo. Busca **el mismo nombre** que viste en el Explorador.
> - **2C.** Copia en F0.1 la huella de esa línea y la dirección web del `SHA256SUMS`. Si el nombre no coincide, **detente**: puede ser otra versión y esa huella no sirve para tu descarga.

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
> - **3E.** Pulsa `Enter`. `Get-FileHash` **lee** el archivo y calcula la huella; `-LiteralPath` indica qué archivo leer; `'.\NOMBRE-REAL.iso'` significa «ese archivo en la carpeta actual»; `-Algorithm SHA256` pide usar el mismo cálculo que la lista oficial. **No borra ni modifica la ISO.** En el resultado, copia el valor del campo `Hash` a F0.1. Si aparece «no se encuentra la ruta», comprueba carpeta y nombre antes de repetir.
>
> - **3F. Si PowerShell está bloqueado en tu equipo:** vuelve al Explorador, entra en la carpeta de la ISO y usa «Open Git Bash here / Abrir Git Bash aquí», que ya utilizaste en el curso de Git. Escribe `pwd` para mostrar la carpeta y `ls` para confirmar que ves el `.iso`. Sustituye el nombre real en `sha256sum 'NOMBRE-REAL.iso'` y pulsa `Enter`. `sha256sum` lee el archivo de **Windows** desde Git Bash y muestra su huella; no estás dentro de Ubuntu. Copia la cadena que aparece antes del nombre. Si tampoco puedes abrir Git Bash, anota el mensaje y consulta sin modificar las políticas del ordenador.

> [!example] Paso 4 — Compara y decide (**WINDOWS**)
> - **4A.** Coloca en F0.1, una debajo de otra, la huella de `SHA256SUMS` y la que mostró PowerShell.
> - **4B.** Compara **todos** los caracteres. Mayúsculas y minúsculas en letras hexadecimales representan el mismo valor; si cambia algún carácter, las huellas no coinciden.
> - **4C.** Escribe «Coinciden: puedo usar esta ISO» o «No coinciden: no instalo esta ISO». Si no coinciden, primero comprueba que elegiste la línea del archivo correcto; después vuelve a descargar desde la página oficial y repite el cálculo. No pases a F0.2 con una ISO distinta de la comprobada.

> [!example] Paso 5 — Termina el vídeo y registra su enlace (**WINDOWS**)
> - **5A.** Muestra en pantalla la comparación y explica con tus palabras qué comprobaste. Detén OBS.
> - **5B.** En YouTube crea, si aún no existe, **una sola playlist** llamada `B0_Curso_Shell`. Sube el vídeo con el título **`B0.S.0.1 · Marko comprueba la ISO`** y visibilidad **«No listado»**. No crees una playlist por práctica.
> - **5C.** En la descripción escribe `00:00 Presentación` y una marca de tiempo para cada paso grabado. Copia el enlace del vídeo en F0.1 de la entrada. La entrada común se subirá al repositorio **al cerrar F0.4**; sigue escribiendo en ella durante la fase.

## Cómo se puntúa y qué compruebas

| Evidencia que debe verse en vídeo y apuntes | Puntos |
| :--- | ---: |
| Página oficial, versión, carpeta y nombre real de la ISO | 5 |
| Línea correcta del `SHA256SUMS` de esa versión | 5 |
| Comando de PowerShell ejecutado sobre el archivo correcto y valor `Hash` anotado | 8 |
| Comparación completa, decisión y explicación de qué hacer si falla | 2 |

> [!question] Responde en F0.1 con tus palabras
> ¿Por qué importa que la línea de `SHA256SUMS` nombre tu archivo exacto? ¿Qué demuestra una coincidencia de huellas y qué harías si no coincidieran?

**Siguiente:** [F0.2 · Crea la VM](F0-02_VM.md). · [Índice de Fase 0](README.md)
