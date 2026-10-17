# Fase 0 · Prepara el laboratorio Shell — CASA

> **Módulo:** SOR · **Contexto:** CASA · **Bóveda:** `Boveda_Shell_Casa`

Esta guía es un recorrido completo y autónomo. No presupone que hayas realizado la edición Cole. Conserva aquí tu VM, tus apuntes, tu repositorio y tu playlist de esta fase. El laboratorio queda fuera de la carpeta SOR para evitar que una orden ejecutada por despiste dañe tus apuntes reales.

> [!danger] No trabajes dentro de SOR
> Antes de crear carpetas o ejecutar Git, comprueba la ruta física completa. Si aparece un ancestro llamado `SOR` o `Boveda_SOR`, detente. No abras, muevas ni renombres carpetas de ese árbol. `SOR_Shell_Casa` debe ser una carpeta creada en una ubicación local neutral, por ejemplo una carpeta de proyectos fuera de OneDrive. Si Documents está sincronizado, elige otra ubicación local que no esté sincronizada. La única condición es quedar fuera del árbol SOR; el árbol hermano del dibujo es un ejemplo, no una obligación.

## 1 · Prepara una ubicación neutral

Abre Git Bash desde una carpeta local existente que no esté dentro de SOR ni de una carpeta sincronizada con OneDrive, Dropbox o Google Drive. Comprueba la ruta que ves en el Explorador; si no sabes si está sincronizada, detente y elige otra. **Antes de crear nada**, ejecuta este bloque:

```bash
command -v git >/dev/null 2>&1 || { echo "PARADA: Git Bash/Git no está disponible; consulta al profesor antes de continuar"; exit 1; }
pwd -P
PARENT=$(pwd -P)
NORMALIZED=$(printf '%s' "$PARENT" | tr '[:upper:]' '[:lower:]')
case "$NORMALIZED" in */sor|*/sor/*|*/boveda_sor|*/boveda_sor/*) echo "PARADA: esta ruta está dentro de SOR"; exit 1;; esac
if git -C "$PARENT" rev-parse --show-toplevel >/dev/null 2>&1; then echo "PARADA: esta carpeta hereda un repositorio Git"; exit 1; fi
```

Línea a línea: `pwd -P` muestra la ruta física; `PARENT` la guarda; `NORMALIZED` convierte mayúsculas a minúsculas; `case` detiene si la ruta está en `SOR` o `Boveda_SOR`; `git rev-parse` detecta si una carpeta superior ya contiene un repositorio. **Si aparece una parada o un error, no continúes.**

Si no se activó ninguna parada, crea el espacio y repite la barrera ya dentro de la raíz:

```bash
mkdir -- 'SOR_Shell_Casa' || { echo "PARADA: la carpeta ya existe o no se pudo crear; no reutilices un espacio anterior"; exit 1; }
cd 'SOR_Shell_Casa' || exit 1
pwd -P
P=$(pwd -P)
N=$(printf '%s' "$P" | tr '[:upper:]' '[:lower:]')
case "$N" in */sor|*/sor/*|*/boveda_sor|*/boveda_sor/*) echo "PARADA: el destino quedó dentro de SOR"; exit 1;; esac
if git rev-parse --show-toplevel >/dev/null 2>&1; then echo "PARADA: el destino hereda un repositorio Git"; exit 1; fi
```

La ruta final debe terminar en `/SOR_Shell_Casa` y no tener un ancestro `/SOR/` ni `/Boveda_SOR/`. Puede estar en cualquier ubicación local neutral fuera de OneDrive; no es necesario que esté al mismo nivel que SOR. Si falla, no crees la bóveda; pide ayuda y deja intacta la carpeta equivocada. Si pasa, crea la bóveda vacía:

```bash
mkdir -- 'VMs' || { echo "PARADA: VMs ya existe; revisa antes de continuar"; exit 1; }
mkdir -- 'Boveda_Shell_Casa' || { echo "PARADA: la bóveda ya existe; revisa antes de continuar"; exit 1; }
```

`mkdir` solo crea la carpeta; no inicializa Git ni toca el SOR real. En Obsidian usa **Abrir carpeta como bóveda** y selecciona `Boveda_Shell_Casa`.

## 2 · Clona el material de lectura y prepara tu repositorio

El repositorio `sor-iesjj/bloque-0-curso-shell` es material común del profesor y se usa solo para leer. Desde la terminal situada en la bóveda, clónalo con este nombre local:

```bash
cd 'Boveda_Shell_Casa'
git clone https://github.com/sor-iesjj/bloque-0-curso-shell.git B0_Curso_Shell_Casa
```

Tu repositorio de escritura es otro: **`apuntes-shell-casa`**, de tu cuenta GitHub. Créalo vacío desde tu cuenta personal; no lo clones del profesor ni uses la fuente docente como `origin`. Cuando el repositorio exista, clónalo también dentro de la bóveda con el nombre `Apuntes_Shell_Casa`. En el comando siguiente reemplaza `TU_USUARIO` por el nombre exacto de tu cuenta antes de ejecutarlo:

```bash
git clone https://github.com/TU_USUARIO/apuntes-shell-casa.git Apuntes_Shell_Casa
```

Su remoto debe apuntar a tu cuenta y al repo `apuntes-shell-casa`. Comprueba `pwd` y `git remote -v` antes de escribir. Si el repo personal aún no existe o no tienes permiso para crearlo, detente y consulta; no inicialices Git en la bóveda completa ni en el clon docente.

El Git del curso versiona notas, scripts y archivos persistentes del proyecto, no cada comando temporal de la VM. La VM y sus discos se guardan en `SOR_Shell_Casa/VMs/ShellLab_Casa`, fuera de la bóveda y del repo. La carpeta `VMs` se crea en el paso anterior como hermana de la bóveda.

## 3 · Prepara la nota Fase 0

Dentro de `Apuntes_Shell_Casa`, crea `Fase_0/` y la nota `Fase_0/shell-0-preparacion-del-laboratorio-casa.md`. En Obsidian pega esta estructura y rellénala con datos observados:

```markdown
# Fase 0 · Preparación del laboratorio Shell — Casa

- Contexto: Casa
- Alumno:
- Fechas de inicio y cierre:
- VM: ShellLab_Casa
- Hostname Ubuntu: shelllab-casa
- Usuario Ubuntu: marko
- Puerto anfitrión SSH: 2223 (o el que realmente use)

## F0.1 · ISO
- URL oficial, versión y nombre real del archivo:
- URL de SHA256SUMS y huella oficial:
- Huella calculada y comparación:
- Vídeo:
- Respuestas F0.1.1–F0.1.5:

## F0.2 · VirtualBox y VM
- Tipo de sistema/arquitectura y virtualización:
- Versión de VirtualBox y cómo se obtuvo:
- RAM y espacio libre medidos; recursos asignados y motivo:
- Ruta física de la VM (fuera de SOR, bóveda y repo):
- NAT:
- Vídeo:
- Respuestas F0.2.1–F0.2.5:

## F0.3 · Ubuntu Server
- Teclado, red, disco virtual y decisiones de instalación:
- Resultado de whoami, hostname e ip -br address:
- OpenSSH instalado:
- Vídeo:
- Respuestas F0.3.1–F0.3.5:

## F0.4 · SSH y punto de control
- Huella de servidor contrastada:
- Nombre de la clave pública creada (sin copiar su contenido):
- Puerto anfitrión/invitado y prueba de acceso por clave:
- Nombre de instantánea:
- Vídeo:
- Respuestas F0.4.1–F0.4.5:

## Fallos observados y solución

## Qué aprendí / qué falta comprobar
```

No guardes contraseñas, frase de paso, contenido de claves privadas ni datos personales innecesarios. No añadas nunca la clave privada al repo.

## 4 · Orden de la Fase 0

1. [F0.1 · Descarga y comprueba la ISO](F0-01_ISO.md)
2. [F0.2 · Comprueba el equipo y crea la VM](F0-02_VM.md)
3. [F0.3 · Instala Ubuntu Server](F0-03_INSTALACION.md)
4. [F0.4 · Configura SSH con tu clave](F0-04_SSH.md)

### Entrega parcial F0 · CASA

- Una nota de fase, versionada en `apuntes-shell-casa` al terminar F0.4.
- Un vídeo final de la Fase 0 en la playlist propia `B0_Curso_Shell_F0_Casa`. Puedes grabar los pasos en varias sesiones y unirlos para la entrega final; no subas un vídeo por práctica.
- Canales `00.03.00.F001`–`F004` publican el guion y su PDF. La tarea de entrega es la de Fase 0 completa para Casa; termina en F004 y contiene el vídeo final.
- La tarea independiente de esta fase enlaza exactamente este repositorio y esta playlist; no mezcles la edición Cole.
- No subas ISO, disco virtual, contraseñas ni claves privadas.

[Índice general del curso](../../00_INDICE.md)
