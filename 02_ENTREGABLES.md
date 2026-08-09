	# 📦 Qué tienes que entregar — LÉEME ANTES DEL PRIMER EJERCICIO

> **Módulo:** SOR — Sistemas Operativos en Red · **Profesor:** Pedro Navarro Miralles · IES Jorge Juan (Alicante)
>
> **📍 Cuándo se lee:** **AHORA.** Antes de abrir la Fase 1, antes de encender ninguna máquina.

---

> [!danger] 🛑 No empieces ningún ejercicio sin haber leído esta página
> Aquí está **todo lo que se te va a pedir**: dónde van tus apuntes, cómo se llaman, qué tienen que contener y cómo se entregan.
>
> Si empiezas a hacer ejercicios y dejas los apuntes "para luego", te va a pasar una de estas dos: o los escribes de memoria al final —y se nota—, o los pierdes. **Las dos cuentan como no entregado.**

---

## **1 · LOS TRES ENTREGABLES DE CADA EJERCICIO**

Cada uno de los 65 ejercicios produce **tres cosas**, y las tres van juntas:

| # | Entregable | Dónde vive |
| :--- | :--- | :--- |
| 1 | **Una entrada de apuntes** | Tu repositorio de apuntes, en GitHub |
| 2 | **Un vídeo** | Tu playlist de YouTube, **No listado** |
| 3 | **El `push`** que sube la entrada | Tu repositorio |

**No hay entrega parcial.** Un vídeo sin entrada no cuenta, y una entrada sin el enlace del vídeo tampoco.

---

## **2 · DÓNDE VAN TUS APUNTES**

Dentro de **tu bóveda de apuntes** —la que creaste en la Fase 0 de prerrequisitos—, en esta ruta exacta:

```
00_Apuntes/Trimestre_1/B0_Curso_Shell/
```

> [!warning] ⚠️ Esa carpeta la creas TÚ, ahora, antes de empezar
> No la tienes todavía. Créala en tu bóveda y déjala lista:
>
> ```bash
> mkdir -p 00_Apuntes/Trimestre_1/B0_Curso_Shell
> ```
>
> *(Si tu bóveda usa otro trimestre porque empezaste más tarde, cambia el número. Lo que no cambia es `B0_Curso_Shell`.)*

---

## **3 · CÓMO SE LLAMA CADA ENTRADA**

**Una entrada por ejercicio.** El nombre se construye siempre igual:

```
shell-<fase>.<nivel>.<numero>-<titulo-en-minusculas-con-guiones>.md
```

**Ejemplos reales del curso:**

| Ejercicio | Fichero de apuntes |
| :--- | :--- |
| `EJ-01-01-01` — Marko monta el laboratorio | `shell-1.1.1-monta-el-laboratorio.md` |
| `EJ-01-02-01` — Marko se mueve por el árbol | `shell-1.2.1-se-mueve-por-el-arbol.md` |
| `EJ-06-01-01` — Cuando tres casillas no llegan | `shell-6.1.1-cuando-tres-casillas-no-llegan.md` |

> [!important] 📌 El nombre exacto te lo da cada ejercicio
> **No tienes que inventártelo.** Al principio de cada ejercicio, en el `Paso 0`, aparece el nombre que le toca. Cópialo tal cual.

> [!danger] ⚠️ Los nombres NO son orientativos
> Con un grupo entero entregando, si cada uno pone el nombre que le apetece **corregir se vuelve imposible y tu entrega se pierde**. Sin dramas y sin excepciones: el nombre es el que pone el ejercicio.

---

## **4 · 🔴 QUÉ LLEVA DENTRO CADA ENTRADA**

**Esta estructura es obligatoria.** Cópiala y rellénala:

```markdown
# shell-1.2.1 · Marko se mueve por el árbol

- **Alumno:** Nombre Apellido
- **Fecha de inicio:** 2026-09-15
- **Fecha de entrega:** 2026-09-17
- **Fase:** 1 — La terminal y el árbol de ficheros
- **Nivel:** N2 — Básico
- **Ejercicio:** EJ-01-02-01

---

## 🎯 Qué se pedía

*(Dos o tres líneas con tus palabras: qué te encargaba Lucía y qué había que resolver.)*

---

## ⌨️ Comandos y pasos importantes

*(Los comandos de este ejercicio, con una línea diciendo QUÉ HACE cada uno.
No pegues la terminal entera: quédate con los que importan.)*

- `comando` — para qué sirve.

---

## 🛠️ Qué he hecho

*(Los pasos que has seguido. No copies el enunciado: cuenta lo que hiciste tú.)*

---

## 🚩 Qué me ha fallado y cómo lo he resuelto

*(Los errores que te han salido, con el mensaje literal, y qué hiciste.
Si no te falló nada, escribe "nada" — pero piénsalo dos veces antes.)*

---

## 🤔 Respuestas a las preguntas

*(Las preguntas del apartado "Comprueba que lo has entendido", con tus palabras.
Copiar del enunciado NO cuenta como respuesta.)*

**1.**
**2.**
**3.**

---

## 🔗 Enlaces

- **Vídeo de esta práctica:**
- **Playlist:** `B0_Curso_Shell`

---

## 💭 Dudas / a repasar

*(Lo que no te ha quedado claro.)*
```

> [!success] 🎯 Por qué se pide la fecha de inicio Y la de entrega
> Porque **un ejercicio puede durarte varios días**, y eso es normal.
>
> **Lo que NO se hace es abrir una entrada nueva cada día.** Abres la del ejercicio el primer día y sigues escribiendo en ella hasta terminarlo. Una entrada = un ejercicio, dure lo que dure.

> [!warning] ⚠️ El apartado que más se deja vacío es el de los fallos
> Y es el que más dice de ti. **Un ejercicio donde todo salió a la primera es casi siempre un ejercicio que no se ha entendido**, o uno donde se copió y pegó sin mirar.
>
> Anota el mensaje de error **literal**. Te servirá a ti dentro de tres semanas y a un compañero la semana que viene.

---

## **5 · LOS VÍDEOS**

| | |
| :--- | :--- |
| **Playlist** | `B0_Curso_Shell` — **una sola para todo el curso**, No listado |
| **Nombre del vídeo** | Te lo da cada ejercicio en su ficha. Cópialo **exacto** |
| **Al empezar** | Preséntate y **muestra tu identidad** (tu perfil de GitHub, tu Teams o tu correo `@alu.edu.gva.es`) |
| **Timestamps** | `00:00 Presentación` y uno por paso. **Sin timestamps no se corrige** |
| **Duración** | La que ponga el ejercicio. Si se te va de largo, pártelo en dos y pon los dos enlaces |

> [!info] 🎓 Por qué te obligo a identificarte en cada vídeo
> Porque un vídeo sin cara y sin nombre **no demuestra que lo hayas hecho tú**. Y porque en tres meses, cuando tengas 65 vídeos, vas a agradecer que cada uno diga de quién es y de qué va.

---

## **6 · CÓMO SE ENTREGA**

**Al terminar cada ejercicio, en este orden:**

1. **Guarda tu entrada** con el nombre correcto en `00_Apuntes/Trimestre_1/B0_Curso_Shell/`.
2. **Sube el vídeo** a tu playlist del curso y **pega su enlace dentro de la entrada**.
3. **Sube la entrada a tu repositorio:**
   ```bash
   git add 00_Apuntes/Trimestre_1/B0_Curso_Shell/
   git commit -m "Curso Shell: EJ-01-02-01 terminado"
   git push
   ```
4. **Entrega el enlace** a tu repositorio por la tarea de Teams.

> [!success] 🎯 Aquí es donde el curso de Git empieza a servirte
> Esto no es papeleo: **es exactamente el flujo que aprendiste con Marko en el curso de Git.** Documentar, versionar, subir.
>
> La diferencia es que ahora **no es un ejercicio de Git**: es cómo vas a trabajar el resto del curso, y el resto de tu vida profesional.

> [!question] 🤔 ¿Y si hago tres ejercicios el mismo día?
> **Tres entradas y tres `commit`.** Uno por ejercicio, con su mensaje.
>
> No juntes tres ejercicios en un `commit` que diga *"apuntes"*: el historial de tu repositorio es parte de lo que se mira.

---

## **7 · CRITERIO DE ÉXITO**

> [!success] 🎯 Qué miro cuando corrijo
> Abro tu repositorio, busco la entrada del ejercicio, y dentro tiene que estar:
>
> - **Qué se pedía**, con tus palabras.
> - **Qué hiciste** tú, no lo que decía el enunciado.
> - **Qué te falló** y cómo saliste.
> - **Las respuestas** a las preguntas, contestadas y no copiadas.
> - **El enlace al vídeo** donde se te ve haciéndolo.
>
> **Si falta el enlace o faltan las respuestas, el ejercicio no cuenta como entregado.** Y no es por rigidez: es que sin eso no puedo saber si lo hiciste tú ni si lo entendiste.

---

## **8 · RESUMEN PARA TENER A MANO**

```
CARPETA   00_Apuntes/Trimestre_1/B0_Curso_Shell/
FICHERO   shell-<fase>.<nivel>.<num>-<titulo>.md   (lo dice cada ejercicio)
DENTRO    cabecera · qué se pedía · qué hice · qué falló ·
          respuestas · enlaces (vídeo + playlist + repo)
VÍDEO     playlist "B0_Curso_Shell", No listado, con timestamps
ENTREGA   git add → commit → push → enlace del repo por Teams
```

---

> [!summary] 🎓 Lo que tienes que llevarte de esta página
> Que **los apuntes no son un trámite del final: son parte del trabajo**, y se abren **antes** de empezar, no después de terminar.
>
> Y que la estructura no está para fastidiarte. Está para que dentro de seis meses, cuando busques *"cómo era aquello de los permisos"*, **encuentres tu propia respuesta en dos clics** — que es exactamente lo que hace un técnico con su documentación.
>
> **Siguiente:** [Empieza por la Fase 1](fase-1-terminal-y-ficheros/README.md).
