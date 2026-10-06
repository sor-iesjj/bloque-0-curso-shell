# F0.3 — Instala Ubuntu Server y comprueba el primer arranque

> **SOR · Curso de Shell · Fase 0** · **RA.01 · CE.01.e (introducción)**
> **Dónde:** ventana de la **VM** `ShellLab` en VirtualBox; todavía no se usa SSH.
> **Vídeo:** `B0.S.0.3 · Marko instala Ubuntu Server` · **Playlist:** `B0_Curso_Shell` · **25 puntos**.

> [!info] Encargo de Lucía
> «Instala Ubuntu en el disco de pruebas y deja preparado el programa que permitirá entrar desde la terminal de Windows».

## Qué necesitas entender antes de instalar

- **Ubuntu Server:** edición de Ubuntu pensada para trabajar por terminal; no muestra un escritorio como Windows. Verás texto y un campo `login:` para entrar.
- **Instalador:** programa que copia Ubuntu al disco virtual y pide varias decisiones. No todos los instaladores muestran exactamente los mismos textos: **lee cada pantalla antes de aceptarla**.
- **DHCP:** sistema que da a la VM una dirección de red automáticamente. En esta fase lo hace la red NAT de VirtualBox. No tienes que escribir una dirección del centro.
- **OpenSSH Server:** programa de Ubuntu que acepta conexiones SSH. En F0.4 Git Bash será el cliente que se conectará a este servidor. Seleccionarlo es la evidencia inicial de **CE.01.e**.
- **Usuario y contraseña:** la cuenta `marko` servirá para entrar en Ubuntu. El nombre se puede mostrar en la grabación; **la contraseña nunca se dice, escribe en apuntes ni publica**.

## Antes de grabar

1. Lee **todos** los pasos, hasta la tabla de comprobación. Identifica las pantallas donde elegirás disco, usuario y OpenSSH.
2. Confirma en VirtualBox que la VM se llama `ShellLab`, que su Adaptador 1 está en NAT y que lleva la ISO cuya huella coincidió en F0.1.
3. Abre tu entrada común `shell-0-preparacion-del-laboratorio.md` por F0.3 y ten OBS y tu identificación preparados.
4. El título del vídeo será **`B0.S.0.3 · Marko instala Ubuntu Server`**. Se sube a `B0_Curso_Shell` como «No listado», con presentación y marcas de tiempo.

## Procedimiento

> [!example] Paso 0 — Empieza la grabación (**WINDOWS y VM**)
> - **0A.** Inicia OBS, preséntate y muestra tu identidad.
> - **0B.** Explica que instalarás Ubuntu Server **dentro de `ShellLab`**, no sobre el disco del ordenador Windows.
> - **0C.** Muestra F0.3 de tu entrada antes de comenzar; anota las decisiones mientras trabajas.

> [!example] Paso 1 — Arranca y elige idioma y teclado (**VM**)
> - **1A.** En VirtualBox pulsa **«Iniciar»** sobre `ShellLab`. Debe arrancar desde la ISO seleccionada. Si entra en otro sistema o aparece un error, detente y revisa la ISO; no continúes a ciegas.
> - **1B.** Elige el idioma que puedas seguir y selecciona la distribución de teclado española si es la de tu equipo. Usa el campo de prueba del instalador para escribir `@`: una contraseña escrita con otro mapa puede ser distinta de la que crees.
> - **1C.** Selecciona **Ubuntu Server**, instalación normal, si el instalador ofrece varias modalidades. Aquí no instalas Ubuntu Desktop. Anota en F0.3 lo que elegiste.

> [!example] Paso 2 — Deja que VirtualBox asigne la red (**VM**)
> - **2A.** En la pantalla de red identifica el adaptador que muestra el instalador. Su nombre puede ser `enp0s3` u otro: **anota el que veas**.
> - **2B.** Déjalo en **automático/DHCP**. No introduzcas una IP fija, puerta de enlace o DNS. Esa red NAT es interna de VirtualBox y no necesitas conocer la IP de los ordenadores del centro.
> - **2C.** Si el instalador indica que no tiene red, anota el mensaje. Más tarde apaga la VM y vuelve a comprobar el Adaptador 1 de F0.2. No inventes direcciones para hacerlo avanzar.

> [!example] Paso 3 — Elige el disco de pruebas (**VM**)
> - **3A.** En la pantalla de almacenamiento identifica el disco virtual creado para `ShellLab` por su tamaño. Comprueba el resumen antes de aceptar el borrado.
> - **3B.** Selecciona **usar el disco completo de la VM** con la opción automática del instalador. **No selecciones otro disco** si aparecieran varios: detente y consulta.
> - **3C.** Confirma solo después de verificar que es el disco virtual. En F0.3 escribe qué tamaño viste y cómo lo reconociste. Esta elección nos permite arrancar; aprender a planificar particiones y sistemas de archivos se reserva para el **Bloque 1**.

> [!example] Paso 4 — Crea la cuenta de Ubuntu (**VM**)
> - **4A.** En «nombre del servidor» escribe **`shelllab`**. Ese nombre aparecerá luego al comprobar en qué máquina estás.
> - **4B.** En «nombre de usuario» escribe **`marko`**. El nombre visible de la persona puede ser el tuyo.
> - **4C.** Crea una contraseña que puedas recordar o recuperar según las instrucciones del profesor. Mira el teclado antes de escribirla; **no la pronuncies, no la anotes en F0.3 y no la muestres en el vídeo**. Los campos de contraseña la ocultan.
> - **4D.** Antes de pasar a la pantalla siguiente, comprueba de nuevo que el usuario es `marko` y el servidor `shelllab`.

> [!example] Paso 5 — Selecciona el acceso remoto (**VM**)
> - **5A.** En la pantalla de SSH, marca **`Install OpenSSH server`**. OpenSSH permitirá que Git Bash se conecte a Ubuntu en F0.4.
> - **5B.** No importes claves SSH en esta primera instalación. Para empezar usarás el usuario y la contraseña que acabas de crear. La clave de GitHub del curso de Git pertenece a otro acceso.
> - **5C.** No añadas paquetes destacados o *snaps* que no te pida la práctica. Anota en F0.3 que seleccionaste OpenSSH y **por qué**. [Documentación oficial de Ubuntu sobre OpenSSH](https://ubuntu.com/server/docs/how-to/security/openssh-server/).

> [!example] Paso 6 — Termina e inicia sesión por primera vez (**VM**)
> - **6A.** Espera a que termine la instalación y elige reiniciar. Si VirtualBox vuelve a mostrar el instalador, retira la ISO de la unidad óptica virtual y reinicia **sin repetir la instalación**.
> - **6B.** Cuando veas `login:`, escribe `marko`, pulsa `Enter` y escribe la contraseña. No se ven caracteres mientras escribes: es normal.
> - **6C.** Ejecuta los comandos siguientes **dentro de la consola de Ubuntu**, uno por uno:
>
> ```bash
> whoami
> hostname
> ip -br address
> ```
>
> - **6D.** `whoami` responde quién ha iniciado la sesión; debe corresponder a `marko`. `hostname` muestra el nombre del equipo; debe corresponder a `shelllab`. `ip -br address` resume las conexiones de red y sus direcciones: anota si el adaptador NAT recibió una dirección. **No copies esa dirección en el comando SSH**: F0.4 enseñará cómo llegar desde Windows sin depender de ella.

> [!example] Paso 7 — Si olvidaste OpenSSH, corrígelo (**VM**, solo si hace falta)
> - **7A.** Comprueba si está instalado con `dpkg-query -W openssh-server`. Ese comando pregunta a Ubuntu por un paquete; no cambia nada.
> - **7B.** Si dice que el paquete no existe, y Ubuntu tiene salida a Internet, ejecuta **uno por uno**:
>
> ```bash
> sudo apt update
> sudo apt install openssh-server
> ```
>
> - **7C.** `sudo` solicita permisos de administración y pedirá tu contraseña; `apt update` actualiza el catálogo de paquetes y `apt install` descarga e instala el servidor SSH. Si falla por falta de red, anota el mensaje y revisa el Paso 2 con el profesor. **No edites** archivos de configuración para compensar un error que aún no has identificado. Si el paquete ya estaba instalado, no hace falta reinstalarlo.

> [!example] Paso 8 — Cierra el vídeo (**WINDOWS**)
> - **8A.** Muestra las tres comprobaciones del Paso 6, sin revelar la contraseña. Explica qué prueban. Detén OBS.
> - **8B.** Sube el vídeo con título **`B0.S.0.3 · Marko instala Ubuntu Server`** a la playlist **`B0_Curso_Shell`**, como **«No listado»**. En la descripción añade `00:00 Presentación` y una marca por paso.
> - **8C.** Pega el enlace en F0.3 de tu entrada común. La entrada se entregará en GitHub después de F0.4.

## Cómo se puntúa y qué compruebas

| Evidencia en vídeo y apuntes | Puntos |
| :--- | ---: |
| Arranque, teclado comprobado y Ubuntu Server elegido | 4 |
| Red por DHCP y disco **virtual** identificado antes de aceptar | 6 |
| Usuario `marko`, servidor `shelllab`, contraseña no publicada | 5 |
| OpenSSH seleccionado o instalado tras comprobar que faltaba | 6 |
| Primer arranque y tres comandos ejecutados y explicados | 4 |

> [!question] Responde en F0.3 con tus palabras
> ¿Qué disco usaste y cómo sabes que era el virtual? ¿Para qué seleccionaste OpenSSH? ¿Qué comprueba cada uno de los tres comandos del primer arranque?

**Siguiente:** [F0.4 · Conecta por SSH](F0-04_SSH.md). · [Índice de Fase 0](README.md)
