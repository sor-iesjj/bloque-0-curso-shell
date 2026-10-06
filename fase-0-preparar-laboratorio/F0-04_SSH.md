# F0.4 — Entra desde Git Bash y guarda el punto de partida

> **SOR · Curso de Shell · Fase 0** · **RA.01 · CE.01.i (introducción)**
> **Dónde:** VirtualBox y Git Bash en **Windows**; comandos Linux dentro de la **VM** después de conectar.
> **Vídeo:** `B0.S.0.4 · Marko entra por SSH` · **Playlist:** `B0_Curso_Shell` · **30 puntos**.

> [!info] Encargo de Lucía
> «Entra al Ubuntu de prácticas desde la terminal de Windows, demuestra que realmente trabajas dentro de Ubuntu y guarda ese estado antes de hacer ejercicios».

## Qué necesitas entender antes de empezar

- **Git Bash** es una ventana de terminal que se abre en **Windows**. Escribir comandos ahí **no significa estar en Ubuntu**. Solo estarás en Ubuntu cuando establezcas la conexión SSH.
- **SSH** conecta un programa **cliente** (el `ssh` que ejecutarás en Git Bash) con un programa **servidor** (OpenSSH instalado en Ubuntu). Al entrar, la terminal mostrará y ejecutará los comandos en la VM. `exit` cerrará esa conexión y te devolverá a Windows.
- **Puerto:** número que ayuda a dirigir una conexión al programa correcto. OpenSSH escucha normalmente en el puerto `22` **dentro de Ubuntu**. Usaremos `2222` **en Windows** como ejemplo; VirtualBox enlazará ambos números.
- **`127.0.0.1`:** dirección que significa «este mismo ordenador». Aquí señala tu Windows, que es donde se ejecuta VirtualBox. No es una dirección de la red del centro ni la IP interna de Ubuntu.
- **Redirección de puertos:** regla de VirtualBox que recibe la conexión en `127.0.0.1:2222` y la lleva al puerto `22` de Ubuntu. La VM conserva NAT y su dirección interna automática. [Manual de red de VirtualBox](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html).
- **Huella del servidor:** identificador de la clave pública de la VM. En la primera conexión la compararás con lo que muestra la propia consola de Ubuntu antes de aceptarla. **La clave de GitHub del curso de Git pertenece a GitHub; aquí entrarás con la contraseña de `marko`.**

## Antes de grabar

1. Lee **toda** la práctica, incluida la tabla «Si no conecta». Ubica en VirtualBox el Adaptador 1 de `ShellLab`; debe seguir en NAT.
2. Abre la entrada `shell-0-preparacion-del-laboratorio.md` por F0.4; comprueba que ya contiene F0.1, F0.2 y F0.3. Deja preparada una línea para anotar el puerto que realmente uses.
3. Ten abiertas la consola de la VM, Git Bash en Windows y OBS. Prepara tu identidad. No digas ni muestres tu contraseña.
4. El título del vídeo será **`B0.S.0.4 · Marko entra por SSH`**. Lo subirás a la **misma playlist** `B0_Curso_Shell` como **«No listado»**, con marcas de tiempo por paso.

## Procedimiento

> [!example] Paso 0 — Empieza la grabación (**WINDOWS**)
> - **0A.** Pulsa «Iniciar grabación» en OBS.
> - **0B.** Preséntate, muestra tu identidad y explica: «Conectaré Git Bash de Windows al Ubuntu Server de mi VM».
> - **0C.** Muestra el apartado F0.4 de la entrada, todavía sin resultados. Anotarás lo que ocurra realmente.

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
> - **2A.** Arranca `ShellLab` y entra como `marko` directamente en la ventana de VirtualBox. Ahora **sí** estás tecleando en Ubuntu.
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
> - **3A.** En la consola de Ubuntu ejecuta `sudo poweroff` y espera a que VirtualBox muestre `ShellLab` como **Apagada**. Este comando apaga Ubuntu de forma ordenada.
> - **3B.** Selecciona `ShellLab` en VirtualBox y abre **Configuración → Red → Adaptador 1**. Comprueba otra vez que «Conectado a» indica **NAT**.
> - **3C.** Abre **Avanzadas → Reenvío de puertos** y añade una fila. Escribe estos valores en sus campos correspondientes:
>
> | Campo de VirtualBox | Valor que escribes | Qué significa |
> | :--- | :--- | :--- |
> | Nombre | `ssh-shelllab` | Nombre de esta regla |
> | Protocolo | `TCP` | Tipo de conexión usado por SSH |
> | IP anfitrión | `127.0.0.1` | Solo el propio Windows recibirá la conexión |
> | Puerto anfitrión | `2222` | Número que usarás en Git Bash |
> | IP invitado | **Vacía** | VirtualBox conoce la IP interna asignada a la VM |
> | Puerto invitado | `22` | Número en el que escucha OpenSSH dentro de Ubuntu |
>
> - **3D.** Relee **toda** la fila antes de guardar. Si `2222` está ocupado, anota el error, consulta y elige otro puerto libre; **anota el número nuevo y úsalo también en el Paso 4**. No dejes vacía la «IP anfitrión»: entonces podrías abrir el puerto en otras interfaces del ordenador. Si los nombres de los campos no coinciden con los de tu versión, consulta el [manual oficial](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html) antes de aceptar.
> - **3E.** Guarda la regla, arranca `ShellLab` y espera a que aparezca `login:`. No hace falta iniciar sesión en la consola para que el servidor SSH esté disponible.

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
> - **4E.** Git Bash pedirá la contraseña de `marko`. Escríbela y pulsa `Enter`; **no aparecen caracteres mientras tecleas**, y eso es normal. No es la clave de GitHub. Si vuelve a pedir la contraseña, revisa usuario y teclado antes de insistir.

> [!example] Paso 5 — Demuestra que has entrado en Ubuntu (**sesión SSH de la VM**)
> - **5A.** Ejecuta estos comandos, uno por uno:
>
> ```bash
> whoami
> hostname
> pwd
> ```
>
> - **5B.** `whoami` debe identificar a `marko`. `hostname` debe mostrar `shelllab`. `pwd` muestra la carpeta actual de Ubuntu. Anota los resultados reales en F0.4; **estos tres comandos ahora se ejecutan en la VM, aunque la ventana sea Git Bash de Windows**.
> - **5C.** Ejecuta `exit`. Este comando cierra la sesión SSH y te devuelve a **Git Bash local de Windows**. Anota qué cambió en el indicador de la terminal. Si quieres comprobarlo, ejecuta `hostname` de nuevo: ahora se refiere al anfitrión.

> [!example] Paso 6 — Guarda una instantánea (**VM y WINDOWS**)
> - **6A.** Después de comprobar el acceso, entra en la consola de Ubuntu o vuelve a conectarte por SSH y ejecuta `sudo poweroff`. Espera a que VirtualBox muestre la VM como **Apagada**.
> - **6B.** En VirtualBox abre la vista **Instantáneas** de `ShellLab` y elige **Tomar**. Nómbrala exactamente **`ShellLab - SSH operativo`**.
> - **6C.** Vuelve a la lista y comprueba que aparece. Una instantánea conserva el estado de la VM, **pero no** tus apuntes de Windows, vídeos o contraseña guardada fuera de la VM. No restauremos todavía nada: aprenderás a usarla cuando un ejercicio lo requiera.

> [!example] Paso 7 — Cierra el vídeo y entrega (**WINDOWS, repositorio de apuntes**)
> - **7A.** Detén OBS. Sube el vídeo con el título **`B0.S.0.4 · Marko entra por SSH`** a la playlist **`B0_Curso_Shell`**, como **«No listado»**. Añade `00:00 Presentación` y una marca por cada paso en la descripción.
> - **7B.** Pega en F0.4 el enlace de este vídeo. Comprueba que la entrada común tiene **los cuatro enlaces**, las respuestas y las evidencias de F0.1 a F0.4. No incluyas contraseñas, claves privadas, ISO ni discos virtuales.
> - **7C.** En el Explorador de Windows entra en `Boveda_SOR/00_Apuntes/Trimestre_1`, que es la raíz de tu repositorio `apuntes-sor-t1`. Abre **Git Bash en esa carpeta**, como ya aprendiste en el curso de Git. Antes de subir, ejecuta:
>
> ```bash
> pwd
> git status
> git add B0_Curso_Shell/shell-0-preparacion-del-laboratorio.md
> git diff --cached --stat
> git commit -m "Curso Shell: Fase 0 terminada"
> git push
> ```
>
> - **7D.** `pwd` debe terminar en `00_Apuntes/Trimestre_1`; `git status` debe reconocer el repositorio. Si no es así, **detente antes de `git add`**. `git add` prepara solo tu entrada; `git diff --cached --stat` enseña qué fichero entrará en el commit; `git commit` guarda la versión local y `git push` la envía a GitHub. Si `git diff --cached --stat` muestra otro archivo que no esperabas, consulta antes de confirmar.
> - **7E.** Abre tu repositorio de apuntes en GitHub y comprueba que la entrada y los cuatro enlaces aparecen. Entrega en la tarea de Teams el enlace al repositorio.

## Si no conecta

| Lo que ves | Qué compruebas, en ese orden |
| :--- | :--- |
| `Connection refused` | VM encendida; regla hacia puerto `22`; OpenSSH instalado y `:22` en escucha. |
| `Connection timed out` | VM encendida; Adaptador 1 en NAT; regla con `127.0.0.1` y mismo puerto que `ssh -p`. |
| `Permission denied` | Nombre `marko`, contraseña de Ubuntu y mapa del teclado; no cambies la configuración de SSH sin saber la causa. |
| Puerto anfitrión ya usado | Anota el error; usa otro puerto libre con el profesor y cámbialo **tanto** en VirtualBox como en `ssh -p`. |
| Aviso de huella cambiada | No borres `known_hosts` a ciegas; revisa si restauraste o reinstalaste `ShellLab` y consulta. |

## Cómo se puntúa y qué compruebas

| Evidencia en vídeo y apuntes | Puntos |
| :--- | ---: |
| Cliente y servidor comprobados; `:22` identificado | 5 |
| Regla NAT con anfitrión `127.0.0.1` y puertos anotados | 8 |
| Huella contrastada y conexión SSH con contraseña | 7 |
| `whoami`, `hostname`, `pwd` y `exit` ejecutados y explicados | 5 |
| Instantánea visible y entrada completa comprobada en GitHub | 5 |

> [!question] Responde en F0.4 con tus palabras
> ¿Cómo sabes cuándo Git Bash está trabajando en Ubuntu y cuándo en Windows? ¿Por qué escribiste `127.0.0.1` y `-p 2222`? ¿Qué no guarda la instantánea?

**Siguiente:** [Fase 1 · La terminal y los ficheros](../fase-1-terminal-y-ficheros/README.md). · [Índice de Fase 0](README.md)
