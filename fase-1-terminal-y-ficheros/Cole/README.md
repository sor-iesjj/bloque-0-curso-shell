# Fase 1 · Terminal y ficheros · Cole

**Contexto:** Cole · **Bóveda:** `Boveda_Shell_Cole` · **Repositorio:** `apuntes-shell-cole` · **Playlist:** `B0_Curso_Shell_F1_Cole`

> [!danger] 🛑 Aislamiento del laboratorio
> Este laboratorio está fuera de `SOR` y `Boveda_SOR`, donde se guardan los apuntes reales. Antes de crear archivos o ejecutar Git, comprueba que estás en el proyecto del contexto indicado. `SOR_Shell_Cole` es el espacio separado del laboratorio; no es la carpeta del módulo `SOR`. No uses rutas, bóvedas, repositorios ni claves de Casa/Cole de forma cruzada.

Esta guía presupone que completaste **tu propio** [laboratorio Fase 0 · Cole](../../fase-0-preparar-laboratorio/Cole/README.md): VM `ShellLab_Cole`, Ubuntu `shelllab-cole`, usuario `marko`, Git Bash de Windows como cliente SSH, Ubuntu como servidor SSH y clave Ed25519 propia del contexto. Casa no presupone que hayas hecho Cole.

## Prepara la bitácora antes del primer ejercicio

En Obsidian, dentro de `Boveda_Shell_Cole/Apuntes_Shell_Cole`, crea las carpetas `Fase_1/Bitacora/` si no existen. Ese es el repositorio personal `apuntes-shell-cole`; no inicialices Git en toda la bóveda ni en el clon docente. Antes de cada ejercicio, crea allí la nota con el nombre exacto que muestra su Paso 0. Las notas persisten y se versionan; los comandos y archivos de prueba pasajeros de Ubuntu no se añaden automáticamente.

## Cómo trabajar en esta fase

Cada EJ desarrolla una tarea real del escenario y guarda una entrada en la bitácora persistente del repositorio: `Fase_1/Bitacora/`. Git se usa para versionar esos ficheros que cambian; los comandos que escribes en Ubuntu y los archivos pasajeros de práctica no se convierten automáticamente en repositorio. Sigue las comprobaciones de ruta de cada paso y detente si no coincide el usuario, la máquina o el directorio.

Los bloques de terminal distinguen el equipo Windows del servidor Ubuntu. Ejecuta SSH/SCP desde Git Bash en Windows; ejecuta los ejercicios Linux dentro de la sesión SSH, después de comprobar `whoami`, `hostname` y `pwd`. Usa solo la clave privada de este contexto; se queda en Windows y nunca se copia a Ubuntu, a la bóveda ni al repositorio.

## Índice de ejercicios y publicaciones

| Código Teams | Canal/publicación | Práctica |
| :--- | :--- | :--- |
| `EJ0101` | `00.03.01.EJ0101 Comprobar laboratorio` | [EJ-01-01-01](./EJ-01-01-01.md) — Marko comprueba SSH y copia un archivo de prueba a Windows |
| `EJ0102` | `00.03.01.EJ0102 Leer la terminal` | [EJ-01-01-02](./EJ-01-01-02.md) — Marko abre la terminal y aprende a leer el prompt |
| `EJ0201` | `00.03.01.EJ0201 Navegar por rutas` | [EJ-01-02-01](./EJ-01-02-01.md) — Marko se mueve por el árbol: rutas absolutas y relativas |
| `EJ0202` | `00.03.01.EJ0202 Listar y leer ficheros` | [EJ-01-02-02](./EJ-01-02-02.md) — Marko lista y lee ficheros sin abrir un editor |
| `EJ0301` | `00.03.01.EJ0301 Crear copiar mover y borrar` | [EJ-01-03-01](./EJ-01-03-01.md) — Marko crea, copia, mueve y borra |
| `EJ0302` | `00.03.01.EJ0302 Editar con nano` | [EJ-01-03-02](./EJ-01-03-02.md) — Marko edita con nano y hace copia antes |
| `EJ0401` | `00.03.01.EJ0401 Atajos e historial` | [EJ-01-04-01](./EJ-01-04-01.md) — Marko deja de teclear de más: Tab, historial y atajos |
| `EJ0402` | `00.03.01.EJ0402 Consultar ayuda` | [EJ-01-04-02](./EJ-01-04-02.md) — Marko aprende a resolver dudas solo: man y --help |
| `EJ0501` | `00.03.01.EJ0501 Reconstruir el árbol` | [EJ-01-05-01](./EJ-01-05-01.md) — Reto: Marko reconstruye a ciegas el árbol de Boochan |

Los nueve canales/posts orientan cada práctica y pueden publicar el PDF de Cole y Casa. **La entrega de la fase es una sola tarea de Teams para este contexto**, no nueve tareas: al terminar, entrega el enlace al repositorio `apuntes-shell-cole` y el enlace a la playlist `B0_Curso_Shell_F1_Cole`.

## Vídeo y cierre de fase

Entrega un único vídeo final de fase con el nombre **`B0.S.F1.Cole · Terminal y ficheros`** en **`B0_Curso_Shell_F1_Cole`**. Puedes unir grabaciones cortas de sesiones distintas o hacer una demostración final breve de los hitos. No tienes que grabar nueve vídeos ni mantener OBS encendido durante toda la fase. Consulta [Cierre de Fase 1](./Cierre_Fase_1.md).

## Requisitos previos y enlaces

- [README del laboratorio Fase 0 · Cole](../../fase-0-preparar-laboratorio/Cole/README.md).

> [!warning] Continuidad
> Fases 2–7 aún conservan material anterior no adaptado a estos espacios independientes. Al terminar Fase 1, detente en su cierre; no uses rutas antiguas como continuación.
