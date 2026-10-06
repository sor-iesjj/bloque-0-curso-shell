# FASE 0 — Prepara el laboratorio de Shell

> **Módulo:** SOR — Sistemas Operativos en Red · **Bloque 0 · Curso de Shell**  
> **Cuándo:** después de «Antes de empezar» y «Entregables», antes de la Fase 1.

Marko necesita un Ubuntu en el que pueda equivocarse sin tocar el servidor Boochan ni los apuntes reales. Al terminar esta fase tendrás una VM **`ShellLab` con Ubuntu Server**, accesible desde **Git Bash de tu ordenador por SSH**, y una instantánea a la que volver.

> [!important] Primera aproximación
> Aquí montas lo imprescindible para aprender Shell. En el **Bloque 1** estudiarás con más profundidad la descarga y verificación de imágenes, la compatibilidad, las redes de VirtualBox y la instalación de sistemas operativos. Esta fase no sustituye ese bloque ni configura la red `10.10.10.0/24` de Boochan.

## Índice y orden obligatorio

| Orden | Práctica | Qué consigues | Puntos |
| :---: | :--- | :--- | ---: |
| 1 | [F0.1 · Descarga y comprueba la ISO](F0-01_ISO.md) | ISO oficial, hash SHA256 coincidente | 20 |
| 2 | [F0.2 · Crea la VM](F0-02_VM.md) | VM independiente con NAT y disco virtual | 25 |
| 3 | [F0.3 · Instala Ubuntu Server](F0-03_INSTALACION.md) | Primer arranque, usuario y OpenSSH | 25 |
| 4 | [F0.4 · Conecta por SSH y guarda](F0-04_SSH.md) | Acceso desde Git Bash e instantánea comprobada | 30 |

**Total: 100 puntos.** Cada práctica tiene una rúbrica observable. La calificación se decide con las evidencias, no con una captura aislada.

## Qué se evalúa

- **RA.01:** «Instala sistemas operativos en red describiendo sus características e interpretando la documentación técnica».
- **CE.01.a:** «Se ha realizado el estudio de compatibilidad del sistema informático». Primer análisis de RAM, espacio y arquitectura en F0.2; el estudio completo se profundiza en el Bloque 1.
- **CE.01.b:** «Se han diferenciado los modos de instalación». En F0.2 comparas instalación manual y desatendida y eliges la manual.
- **CE.01.e:** «Se han seleccionado los componentes a instalar». En F0.3 justificas la selección de OpenSSH.
- **CE.01.i:** «Se ha comprobado la conectividad del servidor con los equipos cliente». En F0.4 demuestras la conexión desde el ordenador anfitrión.

Descargar la ISO y contrastar su hash es una **evidencia preparatoria de RA.01**, no acredita por sí solo un CE distinto. Usar las opciones automáticas de disco en esta introducción **no acredita** el particionado y los sistemas de archivos de CE.01.c y CE.01.d: se trabajarán con detalle en el Bloque 1.

## Trabajo y entrega

- **Una entrada de apuntes** para la fase completa: `00_Apuntes/Trimestre_1/B0_Curso_Shell/shell-0-preparacion-del-laboratorio.md`. Ábrela vacía **antes** de F0.1 y complétala después de cada práctica.
- **Cuatro vídeos**, uno por práctica, con identidad al inicio, grabación del proceso y marcas de tiempo por paso. Playlist `B0_Curso_Shell`, visibilidad «No listado». Cada práctica indica su nombre exacto.
- **Un `commit` y un `push`** desde el repositorio de apuntes al cerrar F0.4. La entrada debe contener los cuatro enlaces y la tabla de evidencias. Entrega el enlace del repositorio en la tarea de Teams.

Consulta la [plantilla y la rúbrica completas](../02_ENTREGABLES.md#fase-0--una-entrada-cuatro-vídeos-y-una-entrega). La ISO, el disco virtual y la contraseña **no se suben** al repositorio.

> [!danger] Dos lugares, dos terminales
> **ORDENADOR** = Windows, VirtualBox, Obsidian, Git Bash antes de `ssh`. **VM** = consola de Ubuntu dentro de VirtualBox o sesión SSH tras conectarte. Nunca ejecutes prácticas de administración en el Git Bash local ni compartas `Boveda_SOR` con la VM.

## Salida de la fase

Solo pasa a [Fase 1](../fase-1-terminal-y-ficheros/README.md) si puedes arrancar `ShellLab`, abrir Git Bash en Windows, conectar con `ssh -p 2222 marko@127.0.0.1` (o el puerto que anotaste), ejecutar `whoami` y `hostname` **dentro de Ubuntu**, salir con `exit` y localizar la instantánea `ShellLab - SSH operativo`.

[← Índice del curso](../00_INDICE.md) · [F0.1 →](F0-01_ISO.md)
