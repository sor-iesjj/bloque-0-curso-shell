# F0.4 — Entra desde Git Bash y guarda el punto de partida

> **SOR · Curso de Shell · Fase 0** · **RA.01 · CE.01.i (introducción)**  
> **Dónde trabajas:** VirtualBox y Git Bash en el **ORDENADOR**; comandos Linux dentro de la sesión de la **VM**.  
> **Vídeo:** `B0.S.0.4 · Marko entra por SSH` · **30 puntos**.

> [!info] Encargo de Lucía
> «Demuestra que puedes trabajar en el servidor desde tu terminal de Windows. Cuando funcione, conserva ese estado para las prácticas».

## Antes de tocar la red

Esta práctica **no necesita una IP de Conselleria** ni pide permisos para cambiar la red del centro. La VM conserva NAT por DHCP. VirtualBox llevará un puerto del **propio ordenador** al puerto `22` de Ubuntu. La dirección `127.0.0.1` significa «este mismo ordenador», no Boochan ni otro equipo del aula. [VirtualBox documenta esta regla de reenvío](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html).

## Procedimiento

> [!example] Paso 0 — Prepara la grabación
> Abre el apartado F0.4 de tu entrada. Ten abiertas las ventanas de VirtualBox, la consola de Ubuntu y Git Bash. Inicia OBS y muestra tu identidad. **Nunca muestres la contraseña**.

> [!example] Paso 1 — Comprueba el cliente (**ORDENADOR, Git Bash todavía local**)
>
> ```bash
> ssh -V
> ```
>
> `ssh -V` muestra la versión del programa cliente. Si Git Bash dice `command not found`, detente y consulta: todavía no puedes entrar en la VM desde esa terminal.

> [!example] Paso 2 — Comprueba el servidor (**VM, consola de VirtualBox**)
> Entra como `marko` y ejecuta:
>
> ```bash
> dpkg-query -W openssh-server
> sudo ss -ltn
> ```
>
> El primer comando muestra si está instalado OpenSSH Server. `ss -ltn` enseña puertos TCP en escucha: busca `:22`. Si falta el paquete, vuelve a [F0.3, Paso 7](F0-03_INSTALACION.md). Si está instalado pero no escucha, anota la salida de `systemctl status ssh.socket ssh.service --no-pager` y consulta antes de editar configuración: según la versión, SSH puede activarse mediante servicio o socket.

> [!example] Paso 3 — Crea la regla en VirtualBox (**ORDENADOR**)
> Apaga la VM de forma normal y espera a que figure como **Apagada**. En la configuración de `ShellLab`, ve al **Adaptador 1 → Avanzadas → Reenvío de puertos**. Añade una regla con estos valores:
>
> | Campo | Valor | Para qué sirve |
> | :--- | :--- | :--- |
> | Nombre | `ssh-shelllab` | Identifica la regla |
> | Protocolo | `TCP` | SSH usa TCP |
> | IP anfitrión | `127.0.0.1` | Solo este ordenador puede usar el puerto reenviado |
> | Puerto anfitrión | `2222` | Puerto al que se conectará Git Bash |
> | IP invitado | **En blanco** | VirtualBox conoce la IP NAT asignada por DHCP |
> | Puerto invitado | `22` | Puerto de OpenSSH dentro de Ubuntu |
>
> Revisa la fila antes de aceptar. Si `2222` está ocupado, elige otro puerto libre con el profesor y anótalo; usa **ese mismo número** en el comando SSH. Si tu versión de VirtualBox presenta otros nombres, contrasta los campos con el [manual oficial](https://docs.oracle.com/en/virtualization/virtualbox/7.2/user/networkingdetails.html) antes de guardar. Arranca de nuevo la VM.

> [!example] Paso 4 — Entra por primera vez (**ORDENADOR, Git Bash**)
>
> ```bash
> ssh -p 2222 marko@127.0.0.1
> ```
>
> `ssh` inicia la conexión; `-p 2222` elige el puerto del anfitrión; `marko` es el usuario de Ubuntu. Sustituye `2222` si anotaste otro. **No uses la IP NAT que viste con `ip`**: desde Git Bash se entra mediante el puerto reenviado de `127.0.0.1`.
>
> La primera vez el cliente pregunta si confías en la huella del servidor. Para comprobarla, en la consola de VirtualBox ejecuta `ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub` y compara la huella `SHA256:` con la que muestra Git Bash **si indica `ED25519`**. Solo si coinciden responde `yes`. Luego escribe la contraseña de `marko`; no se verán caracteres. Si las huellas difieren o no sabes compararlas, detente y consulta. La clave de GitHub del curso de Git **no es la contraseña ni la clave de este servidor**.

> [!example] Paso 5 — Demuestra dónde estás (**sesión SSH dentro de la VM**)
>
> ```bash
> whoami
> hostname
> pwd
> exit
> ```
>
> `whoami` debe identificar a `marko`; `hostname`, a `shelllab`; `pwd` muestra la carpeta de Ubuntu en la que estás. `exit` cierra SSH y devuelve el control a Git Bash **local**. Repite `hostname`: el resultado ya pertenece al ordenador anfitrión y puede ser distinto. Anota la diferencia en la entrada. Si la conexión falla, la consola de VirtualBox sigue disponible para diagnosticar.

> [!example] Paso 6 — Comprueba y guarda la instantánea (**ORDENADOR**)
> Con la conexión probada, apaga Ubuntu normalmente con `sudo poweroff` **dentro de la VM** y espera al estado **Apagada** en VirtualBox. En **Instantáneas**, crea `ShellLab - SSH operativo`. Vuelve a abrir la lista y comprueba que aparece. La instantánea guarda la VM, **no** los apuntes, vídeos ni el disco de Windows. Por eso los apuntes se entregan por separado.

> [!example] Paso 7 — Entrega la Fase 0 (**ORDENADOR, repositorio de apuntes**)
> Cierra y sube el vídeo `B0.S.0.4 · Marko entra por SSH` a `B0_Curso_Shell`, como «No listado», con presentación y marcas de tiempo. Pega sus enlaces y los de F0.1–F0.3 en la entrada. En Git Bash, abre **`Boveda_SOR/00_Apuntes/Trimestre_1`**, comprueba la ruta y el repositorio, y sube **solo** la entrada de la fase:
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
> Si `pwd` no termina en `00_Apuntes/Trimestre_1` o `git status` dice que no hay repositorio, **para antes de `git add`**. Tras `git push`, abre tu repositorio en GitHub y comprueba que aparece la entrada con los cuatro enlaces. Entrega en Teams el enlace del repositorio. No subas ISO, disco virtual, contraseñas ni claves privadas.

## Si no conecta

| Síntoma | Comprueba, en este orden |
| :--- | :--- |
| `Connection refused` | VM arrancada; regla hacia puerto invitado `22`; OpenSSH instalado y `:22` en escucha. |
| `Connection timed out` | Regla de VirtualBox, IP anfitrión `127.0.0.1`, puerto anotado y estado de la VM. |
| `Permission denied` | Usuario `marko`, contraseña creada en Ubuntu y mapa de teclado; **no cambies** aún `sshd_config`. |
| `Address already in use` al crear la regla | El puerto anfitrión está ocupado: elige otro puerto libre con el profesor y úsalo también con `ssh -p`. |
| Aviso de huella cambiada | No borres entradas de `known_hosts` a ciegas: comprueba si restauraste/reinstalaste la VM y consulta. |

## Comprobación y puntuación

| Evidencia visible en vídeo y apuntes | Puntos |
| :--- | ---: |
| Cliente y servidor comprobados, `:22` identificado | 5 |
| Regla NAT correcta y aislada en `127.0.0.1` | 8 |
| Huella contrastada y conexión SSH con contraseña | 7 |
| `whoami`, `hostname`, `pwd` y `exit` explicados | 5 |
| Instantánea visible y entrega completa en GitHub | 5 |

> [!question] Para responder en la entrada
> ¿Qué cambia al ejecutar `exit`? ¿Por qué conectas a `127.0.0.1:2222` y no a `10.10.10.10`? ¿Qué no conserva la instantánea?

**Siguiente:** [Fase 1 · La terminal y los ficheros](../fase-1-terminal-y-ficheros/README.md). · [Índice de Fase 0](README.md)
