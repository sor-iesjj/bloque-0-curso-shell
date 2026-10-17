# F0.4 — Entra desde Git Bash y guarda el punto de partida
> **Recorrido:** COLE · Este documento pertenece solo a `SOR_Shell_Cole/Boveda_Shell_Cole`. No uses la bóveda del otro contexto. El curso se mantiene fuera de la carpeta SOR para evitar que una orden ejecutada por despiste dañe tus apuntes reales.


> **SOR · Curso de Shell · Fase 0** · **RA.01 · CE.01.i (introducción)**
> **Dónde:** VirtualBox y Git Bash en **Windows**; comandos Linux dentro de la **VM** después de conectar.

> **Teams:** `00.03.00.F004` · Guion de práctica para COLE; la entrega es la Fase 0 completa.
> **Vídeo:** `B0.S.F0 · Marko prepara el laboratorio Shell · COLE` · **Playlist:** `B0_Curso_Shell_F0_Cole` · **Vídeo final de Fase 0** · **30 puntos**.

> [!info] Encargo de Lucía
> «Entra al Ubuntu de prácticas desde la terminal de Windows, demuestra que realmente trabajas dentro de Ubuntu y guarda ese estado antes de hacer ejercicios».

## Qué necesitas entender antes de empezar

- **Git Bash** es una ventana de terminal que se abre en **Windows**. Escribir comandos ahí **no significa estar en Ubuntu**. Solo estarás en Ubuntu cuando establezcas la conexión SSH.
- **SSH** conecta un programa **cliente** (el `ssh` que ejecutarás en Git Bash) con un programa **servidor** (OpenSSH instalado en Ubuntu). Al entrar, la terminal mostrará y ejecutará los comandos en la VM. `exit` cerrará esa conexión y te devolverá a Windows.
- **Puerto:** número que ayuda a dirigir una conexión al programa correcto. OpenSSH escucha normalmente en el puerto `22` **dentro de Ubuntu**. Usaremos `2222` **en Windows** como ejemplo; VirtualBox enlazará ambos números.
- **`127.0.0.1`:** dirección que significa «este mismo ordenador». Aquí señala tu Windows, que es donde se ejecuta VirtualBox. No es una dirección de la red del centro ni la IP interna de Ubuntu.
- **Redirección de puertos:** regla de VirtualBox que recibe la conexión en `127.0.0.1:2222` y la lleva al puerto `22` de Ubuntu. La VM conserva NAT y su dirección interna automática. [Manual de red de VirtualBox](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html).
- **Huella del servidor:** identificador de la clave pública de la VM. En la primera conexión la compararás con lo que muestra la propia consola de Ubuntu antes de aceptarla. **La huella de servidor identifica a Ubuntu. Después crearás en Windows una clave de autenticación SSH exclusiva para este laboratorio. No reutilices la clave de GitHub.**

## Antes de grabar

1. Lee **toda** la práctica, incluida la tabla «Si no conecta». Ubica en VirtualBox el Adaptador 1 de `ShellLab_Cole`; debe seguir en NAT.
2. En Obsidian abre tu nota `Boveda_Shell_Cole/Apuntes_Shell_Cole/Fase_0/shell-0-preparacion-del-laboratorio-cole.md`. Comprueba que los apartados **«F0.1 · ISO»**, **«F0.2 · Máquina virtual»** y **«F0.3 · Instalación»** ya contienen tus resultados.
3. En el encabezado de esa nota identifica la línea «Puerto SSH anfitrión»; ahí anotarás el puerto que realmente uses. Después baja al apartado **«F0.4 · SSH y punto de control»**, donde registrarás la conexión y la instantánea.
4. Ten abiertas la consola de la VM, Git Bash en Windows y OBS. Prepara tu identidad. No digas ni muestres tu contraseña.
5. El título del vídeo será **`B0.S.F0 · Marko prepara el laboratorio Shell · COLE`**. Se incorporará al único vídeo final de Fase 0, que subirás al completar F0.4 a `B0_Curso_Shell_F0_Cole`.

## Procedimiento

> [!example] Paso 0 — Empieza la grabación (**WINDOWS**)
> - **0A.** Pulsa «Iniciar grabación» en OBS.
> - **0B.** Preséntate, muestra tu identidad y explica: «Conectaré Git Bash de Windows al Ubuntu Server de mi VM».
> - **0C.** Muestra **«F0.4 · SSH y punto de control»** de tu nota, todavía sin resultados. Ahí anotarás lo que ocurra realmente.

> [!example] Paso 1 — Comprueba que Git Bash tiene el cliente (**WINDOWS, todavía fuera de Ubuntu**)
> - **1A.** Abre Git Bash en Windows. Antes de teclear, recuerda: aquí los comandos actúan en **Windows**.
> - **1B.** Escribe el siguiente comando y pulsa `Enter`:
>
> ```bash
> ssh -V
> ```
>
> - **1C.** `ssh` es el cliente; `-V` pide mostrar su versión. Anota si responde. Si aparece `command not found`, detente y consulta: aún no puedes conectarte desde esta terminal.

> [!example] Paso 2 — Comprueba el servidor SSH (**VM, consola de VirtualBox**)
> - **2A.** Arranca `ShellLab_Cole` y entra como `marko` directamente en la ventana de VirtualBox. Ahora **sí** estás tecleando en Ubuntu.
> - **2B.** Ejecuta los dos comandos, uno tras otro:
>
> ```bash
> dpkg-query -W openssh-server
> sudo ss -ltn
> ```
>
> - **2C.** `dpkg-query -W` pregunta si está instalado el paquete `openssh-server`. `ss -ltn` muestra los puertos TCP en escucha; busca una línea que contenga `:22`. `sudo` da permiso para consultar toda la información y puede pedir tu contraseña.
> - **2D.** Si falta el paquete, vuelve al [Paso 7 de F0.3](F0-03_INSTALACION.md). Si está instalado pero no aparece `:22`, anota el resultado y consulta; no edites `/etc/ssh/sshd_config` a ciegas. En algunas versiones Ubuntu usa `ssh.service` y en otras puede activar SSH mediante `ssh.socket`; la **conexión real** será la comprobación final.

> [!example] Paso 3 — Configura VirtualBox (**WINDOWS, con la VM apagada**)
> - **3A.** En la consola de Ubuntu ejecuta `sudo poweroff` y espera a que VirtualBox muestre `ShellLab_Cole` como **Apagada**. Este comando apaga Ubuntu de forma ordenada.
> - **3B.** Selecciona `ShellLab_Cole` en VirtualBox y abre **Configuración → Red → Adaptador 1**. Comprueba otra vez que «Conectado a» indica **NAT**.
> - **3C.** Abre **Avanzadas → Reenvío de puertos** y añade una fila. Escribe estos valores en sus campos correspondientes:
>
> | Campo de VirtualBox | Valor que escribes | Qué significa |
> | :--- | :--- | :--- |
> | Nombre | `ssh-shelllab-cole` | Nombre de esta regla |
> | Protocolo | `TCP` | Tipo de conexión usado por SSH |
> | IP anfitrión | `127.0.0.1` | Solo el propio Windows recibirá la conexión |
> | Puerto anfitrión | `2222` | Número que usarás en Git Bash |
> | IP invitado | **Vacía** | VirtualBox conoce la IP interna asignada a la VM |
> | Puerto invitado | `22` | Número en el que escucha OpenSSH dentro de Ubuntu |
>
> - **3D.** Relee **toda** la fila antes de guardar. Si `2222` está ocupado, anota el error, consulta y elige otro puerto libre; **anota el número nuevo y úsalo también en el Paso 4**. No dejes vacía la «IP anfitrión»: entonces podrías abrir el puerto en otras interfaces del ordenador. Si los nombres de los campos no coinciden con los de tu versión, consulta el [manual oficial](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html) antes de aceptar.
> - **3E.** Guarda la regla, arranca `ShellLab_Cole` y espera a que aparezca `login:`. No hace falta iniciar sesión en la consola para que el servidor SSH esté disponible.

> [!example] Paso 4 — Conecta por primera vez (**WINDOWS, Git Bash**)
> - **4A.** Vuelve a Git Bash. Escribe el comando; cambia `2222` **solo si anotaste otro puerto en 3D**:
>
> ```bash
> ssh -p 2222 marko@127.0.0.1
> ```
>
> - **4B.** `ssh` abre la conexión. `-p 2222` selecciona el puerto de Windows que acabas de configurar. `marko` es la cuenta de Ubuntu. `127.0.0.1` señala el propio Windows, donde VirtualBox recibe y redirige la conexión. **Todavía no uses** la dirección interna que mostró `ip` en F0.3.
> - **4C.** La primera vez Git Bash puede mostrar una pregunta sobre la huella del servidor. **No escribas `yes` aún.** Mantén esa pregunta en pantalla y, en la consola de VirtualBox, entra como `marko` y ejecuta:
>
> ```bash
> ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub
> ```
>
> - **4D.** El comando de Ubuntu muestra la huella de su clave pública ED25519. Compara la cadena que empieza por `SHA256:` con la que aparece en Git Bash **si la pregunta de Git Bash dice `ED25519`**. Si coincide, vuelve a Git Bash, escribe `yes` y pulsa `Enter`. Si no coincide o el tipo de clave es otro, detente y consulta.
> - **4E.** Git Bash pedirá la contraseña inicial de `marko`. Escríbela y pulsa `Enter`; no aparecen caracteres mientras tecleas. Esta contraseña se usa solo para autorizar tu clave pública en el siguiente paso; no es la clave de GitHub.


> [!example] Paso 5 — Crea una clave SSH propia y autoriza solo la pública (**Windows y consola Ubuntu**)
> - **5A.** En Git Bash local de Windows, fuera de cualquier sesión SSH, comprueba que esos nombres no existen. No sobrescribas una clave anterior; si alguno existe, detente y pide al profesor una instrucción para recuperarla.
>
> ```bash
> test ! -e ~/.ssh/shelllab_cole_ed25519 && test ! -e ~/.ssh/shelllab_cole_ed25519.pub
> ```
>
> Si el comando no termina correctamente, no continúes. Si ambos nombres están libres, crea el directorio si hace falta y genera una clave Ed25519 exclusiva de este contexto.
>
> ```bash
> mkdir -p ~/.ssh
> ssh-keygen -t ed25519 -a 64 -f ~/.ssh/shelllab_cole_ed25519 -C shelllab-cole
> ```
>
> `mkdir -p` crea `~/.ssh` si hace falta; `ssh-keygen` genera el par; `-t ed25519` elige el tipo; `-a 64` refuerza el derivado de la frase de paso; `-f` fija nombres distintos por contexto; `-C` añade una etiqueta. Si pregunta por una frase de paso, crea una que puedas recuperar y **no la muestres ni la guardes en los apuntes**. Se crean dos archivos: el que acaba en `.pub` es público; el que no lleva `.pub` es privado.
> - **5B.** Antes de continuar, confirma en Git Bash que existen ambos archivos, sin abrir ni mostrar el contenido de la clave privada:
>
> ```bash
> test -f ~/.ssh/shelllab_cole_ed25519 && test -f ~/.ssh/shelllab_cole_ed25519.pub && echo "Par de claves creado"
> ```
>
> `test -f` comprueba cada archivo y `&&` ejecuta el mensaje solo si existen los dos. Si no aparece «Par de claves creado», detente y consulta. **Nunca copies el archivo privado** `shelllab_cole_ed25519`, ni lo subas a GitHub, Teams, vídeos o apuntes.
> - **5C.** Con la conexión SSH inicial por contraseña abierta, ejecuta este bloque desde **Git Bash local** para enviar solo la clave pública a Ubuntu. Abre otra pestaña/ventana Git Bash si hace falta; conserva la consola de la VM como rescate.
>
> ```bash
> cat ~/.ssh/shelllab_cole_ed25519.pub | ssh -p 2222 -o PubkeyAuthentication=no -o PreferredAuthentications=password marko@127.0.0.1 'umask 077; mkdir -p ~/.ssh; cat >> ~/.ssh/authorized_keys; chmod 700 ~/.ssh; chmod 600 ~/.ssh/authorized_keys'
> ```
>
> `cat` lee únicamente el archivo `.pub`; `|` pasa esa línea al cliente SSH; `-o PubkeyAuthentication=no` fuerza esta primera autorización con contraseña; el texto entre comillas se ejecuta en Ubuntu: crea `.ssh`, añade la clave a `authorized_keys` y fija permisos privados. Escribe la contraseña de Ubuntu si la pide. Ejecuta esta instalación **una sola vez** para evitar entradas duplicadas. Si tu puerto no es 2222, reemplázalo por el que anotaste en F0.4.
> - **5D.** Cierra la sesión inicial con `exit` y vuelve a probar desde Windows forzando autenticación por clave:
>
> ```bash
> ssh -i ~/.ssh/shelllab_cole_ed25519 -o IdentitiesOnly=yes -o PubkeyAuthentication=yes -o PasswordAuthentication=no -o KbdInteractiveAuthentication=no -o PreferredAuthentications=publickey -p 2222 marko@127.0.0.1
> ```
>
> `-i` selecciona la clave privada local; `IdentitiesOnly=yes` evita probar otras claves; `PasswordAuthentication=no` hace que esta prueba falle en vez de ocultar un problema usando la contraseña; `-p` selecciona el puerto anfitrión. Puede pedir la frase de paso local de la clave, no la contraseña de Ubuntu. Si no entra, no borres `authorized_keys` ni desactives contraseñas: consulta la tabla de recuperación y conserva la consola local.
> - **5E.** Ya dentro por clave, anota que la clave privada permanece en Windows y que Ubuntu recibió solo la pública. No copies ninguna clave al repositorio.

> [!example] Paso 6 — Demuestra que has entrado en Ubuntu (**sesión SSH de la VM**)
> - **6A.** Ejecuta estos comandos, uno por uno:
>
> ```bash
> whoami
> hostname
> pwd
> ```
>
> - **6B.** `whoami` debe identificar a `marko`. `hostname` debe mostrar `shelllab-cole`. `pwd` muestra la carpeta actual de Ubuntu. Anota los resultados reales bajo **«F0.4 · SSH y punto de control»** de tu nota; **estos tres comandos ahora se ejecutan en la VM, aunque la ventana sea Git Bash de Windows**.
> - **6C.** Ejecuta `exit`. Este comando cierra la sesión SSH y te devuelve a **Git Bash local de Windows**. Anota qué cambió en el indicador de la terminal. Si quieres comprobarlo, ejecuta `hostname` de nuevo: ahora se refiere al anfitrión.

> [!example] Paso 7 — Guarda una instantánea (**VM y WINDOWS**)
> - **7A.** Después de comprobar el acceso, entra en la consola de Ubuntu o vuelve a conectarte por SSH y ejecuta `sudo poweroff`. Espera a que VirtualBox muestre la VM como **Apagada**.
> - **7B.** En VirtualBox abre la vista **Instantáneas** de `ShellLab_Cole` y elige **Tomar**. Nómbrala exactamente **`ShellLab_Cole - SSH con clave`**.
> - **7C.** Vuelve a la lista y comprueba que aparece. Una instantánea conserva el estado de la VM, **pero no** tus apuntes de Windows, vídeos o contraseña guardada fuera de la VM. No restauremos todavía nada: aprenderás a usarla cuando un ejercicio lo requiera.

> [!example] Paso 8 — Cierra el vídeo y entrega (**WINDOWS, repositorio de apuntes**)
> - **8A.** Detén OBS. Une los tramos grabados de F0.1 a F0.4 en un único vídeo final de Fase 0. Súbelo con el título **`B0.S.F0 · Marko prepara el laboratorio Shell · COLE`** a la playlist **`B0_Curso_Shell_F0_Cole`**, como **«No listado»**. Añade `00:00 Presentación` y marcas de tiempo para los cuatro bloques de prácticas.
> - **8B.** Pega el enlace en la línea «Vídeo» bajo **«F0.4 · SSH y punto de control»** de tu nota. Comprueba que esa misma nota contiene **el enlace del vídeo final, las 20 respuestas numeradas** y las evidencias de las cuatro prácticas. No incluyas contraseñas, claves privadas, ISO ni discos virtuales.
> - **8C.** En el Explorador de Windows entra en `Boveda_Shell_Cole/Apuntes_Shell_Cole`, raíz local del repositorio `apuntes-shell-cole`. Abre **Git Bash en esa carpeta**, como ya aprendiste en el curso de Git. Antes de subir, ejecuta:
>
> ```bash
> pwd
> git status
> git add Fase_0/shell-0-preparacion-del-laboratorio-cole.md
> git diff --cached --stat
> git commit -m "Curso Shell: Fase 0 terminada"
> git push
> ```
>
> - **8D.** `pwd` debe terminar en `Apuntes_Shell_Cole`; `git status` debe reconocer el repositorio y `git remote -v` debe mostrar tu repo `apuntes-shell-cole` de tu cuenta, nunca `sor-iesjj/bloque-0-curso-shell`. Si no es así, **detente antes de `git add`**. `git add` prepara solo tu entrada; `git diff --cached --stat` enseña qué fichero entrará en el commit; `git commit` guarda la versión local y `git push` la envía a GitHub. Si `git diff --cached --stat` muestra otro archivo que no esperabas, consulta antes de confirmar.
> - **8E.** Abre tu repositorio de apuntes en GitHub y comprueba que la entrada y los cuatro enlaces aparecen. Entrega en la tarea/canal de Teams `00.03.00.F004` los dos enlaces de este proyecto: el repositorio `apuntes-shell-cole` y la playlist `B0_Curso_Shell_F0_Cole`.

## Si no conecta

| Lo que ves | Qué compruebas, en ese orden |
| :--- | :--- |
| `Connection refused` | VM encendida; regla hacia puerto `22`; OpenSSH instalado y `:22` en escucha. |
| `Connection timed out` | VM encendida; Adaptador 1 en NAT; regla con `127.0.0.1` y mismo puerto que `ssh -p`. |
| `Permission denied` | Comprueba usuario y puerto; para la clave, revisa que seleccionaste el fichero privado correcto y que se instaló la clave pública. No cambies permisos ni borres `authorized_keys` a ciegas. Usa la consola de VirtualBox como rescate y consulta. |
| Puerto anfitrión ya usado | Anota el error; usa otro puerto libre con el profesor y cámbialo **tanto** en VirtualBox como en `ssh -p`. |
| Aviso de huella cambiada | No borres `known_hosts` a ciegas; revisa si restauraste o reinstalaste `ShellLab_Cole` y consulta. |

## Cómo se puntúa y qué compruebas

| Evidencia en vídeo y apuntes | Puntos |
| :--- | ---: |
| Cliente y servidor comprobados; clave de alumno propia separada de GitHub | 4 |
| Regla NAT con anfitrión `127.0.0.1` y puertos anotados | 7 |
| Huella contrastada, clave pública instalada y acceso probado con clave | 6 |
| `whoami`, `hostname`, `pwd` y `exit` ejecutados y explicados | 3 |
| Instantánea visible y entrada completa comprobada en GitHub | 5 |
| Respuestas 1–5 de esta práctica en la nota: un punto por respuesta correcta y explicada | 5 |

> [!question] F0.4 · Responde las cinco preguntas bajo «F0.4 · SSH y punto de control» de tu nota
> Usa los números «F0.4.1» a «F0.4.5» de la plantilla y contesta con tus palabras. Si cambiaste el puerto `2222`, usa en la respuesta el puerto que anotaste de verdad.
>
> 1. **F0.4.1.** ¿Dónde se ejecuta `ssh -V` antes de conectar? Después de entrar por SSH, ¿dónde se ejecutan `whoami` y `pwd`, aunque uses la misma ventana de Git Bash?
> 2. **F0.4.2.** En `ssh -p 2222 marko@127.0.0.1`, ¿qué significan `marko`, `127.0.0.1` y `2222`? ¿Qué puerto recibe la conexión dentro de Ubuntu?
> 3. **F0.4.3.** ¿Qué valores pusiste en «IP anfitrión» e «IP invitado» de la regla NAT? Explica por qué los pusiste así.
> 4. **F0.4.4.** En la primera conexión, ¿cómo comprobaste la huella antes de escribir `yes`? ¿Cómo probaste después que el acceso usa clave pública y no una contraseña de Ubuntu?
> 5. **F0.4.5.** ¿Qué diferencia hay entre la clave pública instalada en Ubuntu y la privada que permanece en Windows? ¿Qué demuestra `exit` y qué conserva la instantánea `ShellLab_Cole - SSH con clave` y qué entregables quedan fuera de ella?

**Siguiente:** [Fase 1 · La terminal y los ficheros](../../fase-1-terminal-y-ficheros/Cole/README.md). · [Índice de Fase 0](README.md)
