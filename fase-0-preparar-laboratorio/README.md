# FASE 0 — Prepara el laboratorio de Shell

> **Módulo:** SOR — Sistemas Operativos en Red · **Bloque 0 · Curso de Shell**
> **Cuándo:** después de «Antes de empezar» y «Entregables», antes de la Fase 1.

En este curso sigues a **Marko**, un técnico ficticio que está aprendiendo. Necesita un ordenador de pruebas donde ensayar comandos sin modificar los apuntes que guardas en Windows. Ese ordenador será una **máquina virtual** (VM): un sistema que funciona dentro de VirtualBox. Lo llamarás `ShellLab` e instalarás en él Ubuntu Server.

Al terminar podrás abrir **Git Bash en Windows** y, desde esa ventana, entrar por **SSH** en la VM. SSH es la conexión que permite usar la terminal de Ubuntu a distancia. También guardarás una **instantánea**, una copia del estado de la VM a la que podrás volver si una práctica la estropea.

> [!important] Primera aproximación
> Aquí montas lo imprescindible para empezar. En el **Bloque 1**, más adelante, estudiarás con más profundidad cómo elegir y comprobar una imagen de instalación, dimensionar una VM, configurar distintas redes virtuales e instalar sistemas operativos. En esta fase usaremos una configuración sencilla y separada de la red física del centro.

## Índice y orden obligatorio

| Orden | Práctica | Qué consigues | Puntos |
| :---: | :--- | :--- | ---: |
| 1 | [F0.1 · Descarga y comprueba la ISO](F0-01_ISO.md) | ISO oficial, hash SHA256 coincidente | 20 |
| 2 | [F0.2 · Crea la VM](F0-02_VM.md) | VM independiente con NAT y disco virtual | 25 |
| 3 | [F0.3 · Instala Ubuntu Server](F0-03_INSTALACION.md) | Primer arranque, usuario y OpenSSH | 25 |
| 4 | [F0.4 · Conecta por SSH y guarda](F0-04_SSH.md) | Acceso desde Git Bash e instantánea comprobada | 30 |

**Total: 100 puntos.** Cada práctica tiene una rúbrica observable: 5 puntos corresponden a sus cinco preguntas numeradas. La calificación se decide con las evidencias y las respuestas, no con una captura aislada.

## Qué se evalúa

- **RA.01:** «Instala sistemas operativos en red describiendo sus características e interpretando la documentación técnica».
- **CE.01.a:** «Se ha realizado el estudio de compatibilidad del sistema informático». Primer análisis de RAM, espacio y arquitectura en F0.2; el estudio completo se profundiza en el Bloque 1.
- **CE.01.b:** «Se han diferenciado los modos de instalación». En F0.2 comparas instalación manual y desatendida y eliges la manual.
- **CE.01.e:** «Se han seleccionado los componentes a instalar». En F0.3 justificas la selección de OpenSSH.
- **CE.01.i:** «Se ha comprobado la conectividad del servidor con los equipos cliente». En F0.4 demuestras la conexión desde el ordenador anfitrión.

Descargar la ISO y contrastar su hash es una **evidencia preparatoria de RA.01**; por sí solo no demuestra otro CE. Usar las opciones automáticas de disco en esta introducción tampoco demuestra que sepas diseñar particiones y elegir sistemas de archivos: eso se trabajará en el Bloque 1.

## Trabajo y entrega

- **Una entrada de apuntes** para la fase completa: `00_Apuntes/Trimestre_1/B0_Curso_Shell/shell-0-preparacion-del-laboratorio.md`. Ábrela vacía **antes** de F0.1 y complétala después de cada práctica. En ella respondes, con tus palabras, las cinco preguntas numeradas de cada práctica: 20 respuestas en total.
- **Cuatro vídeos**, uno por práctica. Antes de grabar lee todos los pasos, abre la entrada, prepara OBS y tu identificación. En cada vídeo preséntate, muestra tu identidad, graba el procedimiento, explica las decisiones y pon marcas de tiempo por paso. Crea una sola playlist llamada `B0_Curso_Shell`; los cuatro vídeos se suben como «No listado». Cada práctica repite su nombre exacto y sus instrucciones de cierre.
- **Un `commit` y un `push`** desde el repositorio de apuntes al cerrar F0.4. La entrada debe contener los cuatro enlaces y la tabla de evidencias. Entrega el enlace del repositorio en la tarea de Teams.

Consulta la [plantilla y la rúbrica completas](../02_ENTREGABLES.md). La ISO, el disco virtual y la contraseña **no se suben** al repositorio.

> [!danger] Dos lugares, dos terminales
> **ORDENADOR** = Windows, VirtualBox, Obsidian, Git Bash antes de `ssh`. **VM** = consola de Ubuntu dentro de VirtualBox o sesión SSH tras conectarte. Nunca ejecutes prácticas de administración en el Git Bash local ni compartas `Boveda_SOR` con la VM.

## Salida de la fase

Solo pasa a [Fase 1](../fase-1-terminal-y-ficheros/README.md) si puedes arrancar `ShellLab`, abrir Git Bash en Windows, conectar mediante el comando SSH que aprenderás en F0.4, comprobar que estás **dentro de Ubuntu**, salir de la conexión y localizar la instantánea `ShellLab - SSH operativo`.

> [!warning] Comprobación previa en el aula
> **Procedimiento no ejecutado todavía en un equipo de Conselleria.** Antes de pedirlo al alumnado, el profesor debe probar allí la apertura de PowerShell o Git Bash en la carpeta de la ISO, las pantallas de la versión instalada de VirtualBox, la regla NAT ligada a `127.0.0.1` y la conexión SSH real. Si una política del equipo bloquea alguno de esos pasos, se documentará la ruta que sí funcione antes de usar la práctica.

[← Índice del curso](../00_INDICE.md) · [F0.1 →](F0-01_ISO.md)
