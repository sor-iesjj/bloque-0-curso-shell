# F0.3 — Instala Ubuntu Server y entra por primera vez

> **SOR · Curso de Shell · Fase 0** · **RA.01 · CE.01.e (introducción)**  
> **Dónde trabajas:** pantalla de la **VM** dentro de VirtualBox.  
> **Vídeo:** `B0.S.0.3 · Marko instala Ubuntu Server` · **25 puntos**.

> [!info] Encargo de Lucía
> «Instala el sistema en el disco virtual y deja preparada la puerta de acceso remoto. Todavía no toques la red de Boochan».

## Antes de arrancar

Lee todas las decisiones antes de grabar. La instalación completa se hace en `ShellLab`, que debe estar **vacía**. El disco que verá Ubuntu es el virtual creado en F0.2. Si aparecen otros discos o no sabes identificarlo, **detente y consulta antes de confirmar el borrado**.

## Procedimiento

> [!example] Paso 0 — Prepara tu entrada y OBS
> Abre F0.3 en `shell-0-preparacion-del-laboratorio.md`. Inicia OBS, muestra tu identidad y explica que instalarás Ubuntu Server en el disco virtual de `ShellLab`. Al escribir contraseñas, detén la captura de esa ventana o cubre el campo en la edición del vídeo antes de publicarlo; el procedimiento puede seguir grabándose alrededor de ese momento.

> [!example] Paso 1 — Arranca el instalador (**VM**)
> Inicia `ShellLab` en VirtualBox. Comprueba que arranca desde la ISO de F0.1. Elige el idioma y el mapa de teclado que puedas usar; comprueba especialmente cómo se escribe `@`, porque un mapa incorrecto cambia lo que tecleas al crear la contraseña. Selecciona la instalación normal de **Ubuntu Server**. No necesitas Ubuntu Desktop ni escritorio gráfico.

> [!example] Paso 2 — Configura la red inicial (**VM**)
> Deja el adaptador NAT en **automático (DHCP)**. El instalador puede mostrar un nombre como `enp0s3`, pero anota el que aparezca realmente. No escribas una IP fija, DNS, puerta de enlace ni la dirección `10.10.10.10`: VirtualBox entrega los datos de esta red interna. Si el instalador no obtiene red, anota el mensaje y vuelve a revisar el Adaptador 1 de F0.2 con la VM apagada.

> [!example] Paso 3 — Elige el disco virtual (**VM**)
> En almacenamiento, identifica el **disco virtual de `ShellLab`** por la capacidad que escogiste. Acepta usarlo completo para esta VM de pruebas y confirma el resumen. Esta elección automática permite arrancar el laboratorio; el diseño de particiones y sistemas de archivos se estudia y evalúa con profundidad en el **Bloque 1**. No describas esta elección como si hubieras diseñado un particionado manual.

> [!example] Paso 4 — Crea la cuenta (**VM**)
> Usa `shelllab` como nombre de servidor y `marko` como nombre de usuario. Elige una contraseña que puedas recuperar según las normas del centro y **no la escribas en apuntes, vídeos ni GitHub**. El usuario `marko` servirá para entrar primero en la consola y luego por SSH. Anota únicamente el nombre de usuario y de servidor.

> [!example] Paso 5 — Selecciona OpenSSH (**VM**)
> En la pantalla de SSH, marca **`Install OpenSSH server`**. Ese componente permite que el `ssh` de Git Bash abra una sesión en Ubuntu. No importes todavía claves: empezaremos con la contraseña de `marko` y estudiaremos las claves después. No añadas otros paquetes o snaps destacados para este laboratorio. [Ubuntu documenta OpenSSH Server y su instalación](https://ubuntu.com/server/docs/how-to/security/openssh-server/).

> [!example] Paso 6 — Termina, reinicia y comprueba (**VM**)
> Espera a que termine la instalación y reinicia. Si vuelve al instalador, retira la ISO de la unidad óptica virtual y vuelve a arrancar **sin reinstalar**. En el indicador `login:` escribe `marko` y la contraseña elegida; no se muestran caracteres al escribirla. Ya dentro, ejecuta:
>
> ```bash
> whoami
> hostname
> ip -br address
> ```
>
> `whoami` debe identificar al usuario de la sesión; `hostname`, al servidor. `ip -br address` resume las interfaces y permite ver que el adaptador obtuvo dirección por DHCP. La IP concreta puede variar y **no será la dirección que utilizarás en Git Bash**.

> [!example] Paso 7 — Si olvidaste OpenSSH (**VM**, solo en ese caso)
> Ejecuta `dpkg-query -W openssh-server`. Si informa de que el paquete no está instalado y la VM tiene salida a Internet, instálalo:
>
> ```bash
> sudo apt update
> sudo apt install openssh-server
> ```
>
> `sudo` solicita tu contraseña para actuar como administrador; `apt update` refresca la lista de paquetes y `apt install` instala el servidor. **No edites** `/etc/ssh/sshd_config` por rutina. Si falla la descarga, anota el error: revisaremos la NAT antes de cambiar la configuración de SSH.

> [!example] Paso 8 — Cierra el vídeo
> Muestra los resultados de `whoami`, `hostname` e `ip -br address`, sin enseñar la contraseña. Sube `B0.S.0.3 · Marko instala Ubuntu Server` como «No listado» a `B0_Curso_Shell`, con presentación y marcas de tiempo; pega el enlace en la entrada.

## Comprobación y puntuación

| Evidencia visible en vídeo y apuntes | Puntos |
| :--- | ---: |
| Arranque del instalador, teclado y elección de Ubuntu Server | 4 |
| NAT por DHCP y elección consciente del disco **virtual** | 6 |
| Cuenta `marko`, servidor `shelllab`, sin divulgar contraseña | 5 |
| OpenSSH seleccionado o instalado tras comprobar que faltaba | 6 |
| Primer arranque y tres comandos de comprobación explicados | 4 |

> [!question] Para responder en la entrada
> ¿Qué disco usaste y por qué sabes que era virtual? ¿Por qué instalaste OpenSSH? ¿Qué prueba cada uno de los tres comandos finales?

**Siguiente:** [F0.4 · Conecta por SSH](F0-04_SSH.md). · [Índice de Fase 0](README.md)
