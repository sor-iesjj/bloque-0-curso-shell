# 🛠️ Antes de empezar — prepara tu sitio de trabajo

> **Módulo:** SOR — Sistemas Operativos en Red · **Bloque 0 · Curso de Shell**
>
> **📍 Cuándo se lee:** **AHORA.** Antes de la Fase 0 y antes de encender ninguna máquina.
>
---

> [!danger] 🛑 No abras la Fase 0 sin haber hecho esto
> Aquí dejas listas **las tres cosas** que vas a necesitar durante todo el curso: **el material**, **tu cuaderno** y **dónde se guarda todo**.
>
> Si empiezas sin esto, en el primer ejercicio te van a pedir que guardes una entrada y que hagas un `push`… **y no vas a tener ni dónde ni a dónde.**

---

## **1 · DE DÓNDE VIENES**

Este curso **no empieza de cero**. Das por hecho que ya tienes:

| Ya deberías tener | De dónde sale |
| :--- | :--- |
| Una **cuenta de GitHub** con Git configurado y SSH | Fase 0.2 de prerrequisitos |
| Tu **bóveda** `Boveda_SOR` en Obsidian | Fase 0.1 |
| Tu **repositorio de apuntes** `apuntes-sor-t1` | Fase 0.3 |
| Saber hacer `clone`, `add`, `commit` y `push` | El **curso de Git** |

> [!warning] ⚠️ Si te falta alguna de las cuatro, para aquí
> Vuelve a los prerrequisitos y termínalos. **Este curso los usa desde el primer ejercicio** y no los vuelve a explicar.

---

## **2 · LOS TRES LUGARES DE TRABAJO**

**No hagas las prácticas Linux en el Git Bash local de tu ordenador.** Hay dos ordenadores: el anfitrión y Ubuntu Server en VirtualBox (`ShellLab`). Tras la Fase 0, **abres Git Bash en Windows y conectas por SSH**: desde ese momento los comandos que tecleas actúan en Ubuntu hasta que salgas con `exit`.

| Lugar | Qué haces ahí | Qué no haces ahí |
| :--- | :--- | :--- |
| Tu ordenador · `Boveda_SOR/01_Practicas/B0_Curso_Shell/` | Abres los enunciados descargados **en Obsidian**. | Ejecutar los comandos que modifican usuarios, permisos, discos o servicios. |
| VM `ShellLab` a través de SSH | Ejecutas los comandos Linux y creas los archivos de prueba. | Abrir o modificar `Boveda_SOR`. |
| Tu ordenador · `Boveda_SOR/00_Apuntes/Trimestre_1/B0_Curso_Shell/` | Escribes tu entrada y guardas una **copia revisada** de los archivos que haya que entregar. | Romper cosas para ver qué pasa. |

La [Fase 0](fase-0-preparar-laboratorio/README.md) prepara la conexión SSH sin compartir carpetas de VirtualBox. Cuando una práctica posterior produzca un archivo que debas entregar, cópialo desde Ubuntu a una carpeta temporal **fuera de `Boveda_SOR`** mediante `scp`, revísalo y luego guárdalo en tus apuntes. La primera práctica lo enseña. Nunca se comparte la bóveda entera con la VM.

### Así queda tu bóveda

```
Boveda_SOR/
├── 00_Apuntes/
│   └── Trimestre_1/          ← 📝 ESTO es tu repositorio 'apuntes-sor-t1'
│       ├── B0_Prerrequisitos/
│       └── B0_Curso_Shell/   ← 🆕 la creas hoy: aquí van tus entradas
│
└── 01_Practicas/
    └── B0_Curso_Shell/          ← 🆕 la creas hoy: aquí va ESTE material
```

> [!info] 🎓 Por qué van separados tus apuntes y el material
> Porque **son de dueños distintos**: los apuntes los escribes tú y te los corrijo; el material te lo doy yo.
>
> Y porque **son dos repositorios distintos**: cuando hagas `push` de tus apuntes, no quieres estar subiendo también los ficheros del curso.
>
> Es lo mismo que ya hiciste con Boochan en la Fase 0.4.

---

## **3 · 🔴 PASO 1 — TRAE ESTE CURSO A TU ORDENADOR**

El material vive en un **repositorio plantilla** mío. Tú **sacas tu propia copia** y la clonas.

### **3A · Saca tu copia en GitHub**

1. En el navegador, abre el repositorio del curso: **`https://github.com/sor-iesjj/bloque-0-curso-shell`**. Aquí obtienes tu copia; después leerás el curso descargado en Obsidian.
2. Pulsa el botón verde **`Use this template`** → **`Create a new repository`**
3. **Repository name:** `bloque-0-curso-shell` *(déjalo igual)*
4. Ponlo **público** o **privado**, como prefieras
5. **`Create repository`**

> [!info] 🎓 Qué acaba de pasar
> Ese repositorio **ya no es mío: es tuyo.** Tiene su propio historial y puedes escribir, romper y subir sin pedirle permiso a nadie.
>
> Es exactamente lo que hiciste en la **Bloque 0 · Fase 0.4.a** con Boochan. Todos los repos del curso son plantilla.

### **3B · Clónalo en tu bóveda**

1. En **tu ordenador**, abre el explorador de archivos y localiza **tu** `Boveda_SOR`. En el Bloque 0 · Fase 0.1 apuntaste dónde la creaste. Puede estar dentro de `Documentos/SOR/` o de `SOR/` en tu carpeta personal. **No presupongas que está directamente en `~`.**
2. Entra en `01_Practicas`. Comprueba en la barra de direcciones que está **dentro de `Boveda_SOR`**.
3. Abre una terminal **en esa carpeta**: en Windows, clic derecho en un espacio vacío → **Open Git Bash here / Abrir Git Bash aquí**; en Linux, clic derecho → **Abrir en terminal**. Si no aparece la opción, pide ayuda antes de seguir: el comando siguiente depende de dónde estés.
4. Escribe `pwd` y lee la ruta. Debe terminar en `Boveda_SOR/01_Practicas` (en Git Bash las barras son `/` aunque estés en Windows). `pwd` significa *print working directory*: muestra la carpeta donde actuará la terminal.
5. Sustituye `TU-USUARIO` por **tu usuario real de GitHub** y ejecuta:

```bash
git clone git@github.com:TU-USUARIO/bloque-0-curso-shell.git B0_Curso_Shell
cd B0_Curso_Shell
ls
```

`git clone` descarga tu copia del curso; `B0_Curso_Shell` es el nombre de la carpeta local. `cd` entra en ella y `ls` muestra su contenido. Si `pwd` no terminó donde se indicó en el punto 4, **no ejecutes `git clone`**: se descargaría en otro lugar.

> [!warning] ⚠️ Cambia `TU-USUARIO` por tu usuario de GitHub
> El resto de la línea, **tal cual**. Incluido el `B0_Curso_Shell` del final.

> [!important] 📌 El `B0_Curso_Shell` del final no está de adorno
> Es el **segundo argumento** de `git clone`, y es el que decide **cómo se va a llamar la carpeta** en tu ordenador:
>
> ```
> git clone  <dirección del repositorio>  <nombre de la carpeta>
> ```
>
> **Si lo omites**, Git le pone el nombre del repositorio — te quedaría `bloque-0-curso-shell/` — y tendrías **la misma cosa con dos nombres distintos** según dónde la mires. Eso es exactamente lo que no queremos.
>
> Ya lo usaste en la **Fase 0.3**, cuando clonaste `apuntes-sor-t1` y le dijiste que se llamara `Trimestre_1`.

> [!info] 🎓 Entonces, ¿por qué el repositorio se llama de otra manera?
> Porque **GitHub obliga**: los nombres de repositorio van en minúsculas y con guiones, no admite `B0_Curso_Shell`.
>
> Así que hay dos nombres para dos sitios distintos, y no se mezclan:
>
> | Dónde vive | Cómo se llama |
> | :--- | :--- |
> | **En GitHub**, el repositorio | `bloque-0-curso-shell` *(me lo impone GitHub)* |
> | **En tu ordenador**, la carpeta | `B0_Curso_Shell` *(lo decides tú, con el segundo argumento)* |
>
> **Dentro de tu bóveda, una cosa tiene un nombre y solo uno.** Tus apuntes del curso están en `B0_Curso_Shell`, la práctica está en `B0_Curso_Shell`, y tu playlist se llama `B0_Curso_Shell`. Cuando yo diga *"esto es del Curso de Shell"*, no hay nada que traducir.

- **✅ Bien:** el `ls` te muestra `00_INDICE.md`, `01_ANTES_DE_EMPEZAR.md`, `02_ENTREGABLES.md`, la carpeta `fase-0-preparar-laboratorio` y las siete carpetas siguientes.
- **❌ Mal:** *"Permission denied (publickey)"* → tu SSH no está configurado. Vuelve a la **Fase 0.2.2**.

### **3C · Abre el curso descargado en Obsidian**

1. Abre Obsidian y selecciona tu bóveda **`Boveda_SOR`**. Si aún no aparece, usa **«Abrir carpeta como bóveda»** y elige la carpeta `Boveda_SOR` completa.
2. En el explorador de archivos de Obsidian, abre `01_Practicas`, después `B0_Curso_Shell` y después `00_INDICE.md`. Esta es la **copia local** que acabas de clonar.
3. En ese índice, abre **«Antes de empezar»** y comprueba que estás leyendo la misma guía dentro de Obsidian. Vuelve al índice para seguir el orden indicado: «Entregables» y luego «Fase 0».
4. Comprueba que junto al índice ves `02_ENTREGABLES.md` y la carpeta `fase-0-preparar-laboratorio`. Si faltan, vuelve al Paso 3B y revisa la ruta del clon antes de continuar.

Desde este punto, lee el material del curso **en Obsidian**. GitHub se ha usado para obtener tu copia y se usará al comprobar las entregas; los PDF que facilite el profesor pueden servirte como apoyo.

---

## **4 · 🔴 PASO 2 — PREPARA TU CUADERNO**

Tus apuntes **NO van en la carpeta del curso**. Van en tu repositorio de apuntes.

1. En el explorador de **tu ordenador**, entra en `Boveda_SOR/00_Apuntes/Trimestre_1`. Esa carpeta es la raíz de tu repositorio `apuntes-sor-t1`.
2. Abre ahí Git Bash o una terminal, igual que en el paso anterior. Ejecuta:

   ```bash
   pwd
   git status
   mkdir -p B0_Curso_Shell
   ls
   ```

   `pwd` debe terminar en `Boveda_SOR/00_Apuntes/Trimestre_1`. `git status` confirma que estás dentro de un repositorio; **no sigas si responde `not a git repository`**. `mkdir -p` crea la carpeta del curso sin borrar nada si ya existía. `ls` permite verla junto a `B0_Prerrequisitos`.

- **✅ Bien:** ves `B0_Curso_Shell` junto a `B0_Prerrequisitos`.

> [!danger] 🛑 Comprueba que estás dentro de tu repositorio
> ```bash
> git status
> ```
> - **✅ Bien:** te responde algo sobre la rama y los cambios.
> - **❌ Mal:** *"not a git repository"* → **te has equivocado de carpeta**. `Trimestre_1` es tu repositorio `apuntes-sor-t1`; si `git` no lo reconoce, estás fuera.
>
> **No sigas hasta que `git status` responda.** Si no, escribirás apuntes que no se van a subir a ninguna parte.

---

## **5 · 🔴 PASO 3 — HAZ LA PRUEBA COMPLETA AHORA, CON UN FICHERO TONTO**

**No esperes al primer ejercicio para descubrir que algo no funciona.** Vamos a hacer el recorrido entero con un fichero de prueba.

**Sigue en la terminal abierta en `Trimestre_1`.** Antes de crear el fichero, repite `pwd` y `git status`. Si cerraste la terminal, vuelve a abrirla desde esa carpeta en el explorador.

```bash
echo "# Prueba del curso de Shell" > B0_Curso_Shell/prueba.md

git add B0_Curso_Shell/
git commit -m "Curso Shell: prueba de que puedo subir apuntes"
git push
```

**Ahora abre `github.com/TU-USUARIO/apuntes-sor-t1` en el navegador.**

- **✅ Bien:** ves la carpeta `B0_Curso_Shell` con `prueba.md` dentro.
- **❌ Mal:** si el `push` da error, **arréglalo hoy**. Lo necesitarás desde la entrega de la Fase 0.

**Y ahora borra solo ese fichero de prueba**, que ya ha cumplido. Comprueba primero que la terminal sigue en `Trimestre_1`:

```bash
pwd
rm B0_Curso_Shell/prueba.md
git add B0_Curso_Shell/
git commit -m "Curso Shell: quito el fichero de prueba"
git push
```

> [!success] 🎯 Por qué te hago esto antes de empezar
> Porque **acabas de comprobar el circuito entero** —escribir, añadir, confirmar, subir y verlo en GitHub— **con algo que no importa**.
>
> El día que falle, fallará con un fichero de prueba y no con el trabajo de tres horas.
>
> Es la misma idea que verás en el servidor una y otra vez: **probar antes de necesitarlo**.

---

## **6 · CÓMO VA A SER TU DÍA A DÍA**

A partir de ahora, en cada ejercicio:

```
1. En Obsidian abres el ejercicio en   01_Practicas/B0_Curso_Shell/fase-N-…/EJ-….md
2. Abres tu entrada en     00_Apuntes/Trimestre_1/B0_Curso_Shell/shell-….md
   (el nombre te lo da el propio ejercicio, en su Paso 0)
3. Arrancas ShellLab, abres Git Bash, conectas por SSH y compruebas `whoami` y `hostname`
4. Grabas con OBS y haces las pruebas dentro de la sesión SSH de ShellLab
5. Si hay un archivo que entregar, lo copias con `scp` a una carpeta temporal fuera de la bóveda y compruebas la copia
6. Escribes tus apuntes MIENTRAS trabajas, no al final
7. Subes el vídeo y pegas su enlace en la entrada
8. Desde Trimestre_1: compruebas la ruta → git add → revisas → git commit → git push
```

> [!important] 📌 Sigue este orden en cada ejercicio
> **No te los vas a aprender leyéndolos**: te los vas a aprender repitiéndolos. En los tres primeros ejercicios te los recuerdo entero. A partir del cuarto, ya son tuyos.

---

## ✅ **CHECKLIST — antes de empezar la Fase 0**

- [ ] Tengo mi copia del curso en GitHub *(botón `Use this template`)*.
- [ ] La he clonado en `01_Practicas/B0_Curso_Shell/` y el `ls` muestra la Fase 0 y las siete fases siguientes.
- [ ] He abierto en Obsidian `Boveda_SOR/01_Practicas/B0_Curso_Shell/00_INDICE.md` desde la copia descargada.
- [ ] He creado `00_Apuntes/Trimestre_1/B0_Curso_Shell/`.
- [ ] `git status` me responde desde `Trimestre_1` *(estoy dentro del repo)*.
- [ ] **He hecho la prueba completa**: fichero → `add` → `commit` → `push` → **lo he visto en GitHub**.
- [ ] He borrado el fichero de prueba y he subido el borrado.
- [ ] He leído **[📦 Entregables](02_ENTREGABLES.md)** y sé cómo se llama cada entrada.

---

> [!summary] 🎓 Qué has dejado listo
> **El material** en `01_Practicas/`, **tu cuaderno** en `00_Apuntes/`, y **comprobado que puedes subir a GitHub** — las tres cosas que vas a usar los próximos dos meses.
>
> Y una costumbre que va a volver muchas veces este curso: **probar el circuito con algo que no importa, antes de que importe**.
>
> **Siguiente:** [📦 Qué tienes que entregar](02_ENTREGABLES.md).
