# 🛠️ Antes de empezar — prepara tu sitio de trabajo

> **Módulo:** SOR — Sistemas Operativos en Red · **Bloque 0 · Curso de Shell**
>
> **📍 Cuándo se lee:** **AHORA.** Antes de la Fase 1 y antes de encender ninguna máquina.
>
> **⏱️ Te lleva:** unos 15 minutos.

---

> [!danger] 🛑 No abras la Fase 1 sin haber hecho esto
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

## **2 · CÓMO ESTÁ ORGANIZADA TU BÓVEDA** *(recuerdo rápido)*

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

1. Abre el repositorio del curso: **`github.com/sor-iesjj/bloque-0-curso-shell`**
2. Pulsa el botón verde **`Use this template`** → **`Create a new repository`**
3. **Repository name:** `bloque-0-curso-shell` *(déjalo igual)*
4. Ponlo **público** o **privado**, como prefieras
5. **`Create repository`**

> [!info] 🎓 Qué acaba de pasar
> Ese repositorio **ya no es mío: es tuyo.** Tiene su propio historial y puedes escribir, romper y subir sin pedirle permiso a nadie.
>
> Es exactamente lo que hiciste en la **Bloque 0 · Fase 0.4.a** con Boochan. Todos los repos del curso son plantilla.

### **3B · Clónalo en tu bóveda**

Abre una terminal **en tu ordenador** (aquí todavía no hay máquina virtual) y ve a la carpeta de prácticas:

```bash
cd ~/Boveda_SOR/01_Practicas
git clone git@github.com:TU-USUARIO/bloque-0-curso-shell.git B0_Curso_Shell
cd B0_Curso_Shell
ls
```

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

- **✅ Bien:** el `ls` te muestra `00_INDICE.md`, `01_ANTES_DE_EMPEZAR.md`, `02_ENTREGABLES.md` y las siete carpetas `fase-…`.
- **❌ Mal:** *"Permission denied (publickey)"* → tu SSH no está configurado. Vuelve a la **Fase 0.2.2**.

---

## **4 · 🔴 PASO 2 — PREPARA TU CUADERNO**

Tus apuntes **NO van en la carpeta del curso**. Van en tu repositorio de apuntes.

```bash
cd ~/Boveda_SOR/00_Apuntes/Trimestre_1
mkdir -p B0_Curso_Shell
ls
```

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

```bash
cd ~/Boveda_SOR/00_Apuntes/Trimestre_1
echo "# Prueba del curso de Shell" > B0_Curso_Shell/prueba.md

git add B0_Curso_Shell/
git commit -m "Curso Shell: prueba de que puedo subir apuntes"
git push
```

**Ahora abre `github.com/TU-USUARIO/apuntes-sor-t1` en el navegador.**

- **✅ Bien:** ves la carpeta `B0_Curso_Shell` con `prueba.md` dentro.
- **❌ Mal:** si el `push` da error, **arréglalo hoy**. Es el mismo problema que tendrás en los 65 ejercicios.

**Y ahora borra el fichero de prueba**, que ya ha cumplido:

```bash
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
1. Abres el ejercicio en   01_Practicas/B0_Curso_Shell/fase-N-…/EJ-….md
2. Abres tu entrada en     00_Apuntes/Trimestre_1/B0_Curso_Shell/shell-….md
   (el nombre te lo da el propio ejercicio, en su Paso 0)
3. Grabas con OBS y haces el ejercicio en tu VM
4. Escribes tus apuntes MIENTRAS trabajas, no al final
5. Subes el vídeo y pegas su enlace en la entrada
6. git add → git commit → git push
```

> [!important] 📌 Los seis pasos, siempre iguales
> **No te los vas a aprender leyéndolos**: te los vas a aprender repitiéndolos. En los tres primeros ejercicios te los recuerdo entero. A partir del cuarto, ya son tuyos.

---

## ✅ **CHECKLIST — no pases a la Fase 1 sin esto**

- [ ] Tengo mi copia del curso en GitHub *(botón `Use this template`)*.
- [ ] La he clonado en `01_Practicas/B0_Curso_Shell/` y el `ls` muestra las siete fases.
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
> **Siguiente:** [📦 Qué tienes que entregar](02_ENTREGABLES.md) — cinco minutos y ya empiezas.
