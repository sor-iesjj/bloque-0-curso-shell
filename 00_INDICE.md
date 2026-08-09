# 🐧 Curso de Shell de Linux — Índice general

> **Módulo:** SOR — Sistemas Operativos en Red · **Bloque 0** · **Profesor:** Pedro Navarro Miralles · IES Jorge Juan (Alicante)

---

## **1 · QUÉ ES ESTE CURSO Y PARA QUÉ SIRVE**

Vas a montar un servidor durante el curso. Y ese servidor se administra **escribiendo comandos en una terminal**.

Este curso te enseña esos comandos **antes** de que los necesites, para que cuando llegues al servidor **sepas lo que estás escribiendo** en vez de copiar y pegar sin entender.

> [!info] 🎓 Sigues a Marko, igual que en el curso de Git
> **Marko** es técnico junior en **Boochan Networks S.L.** Ya sabe versionar con Git — eso lo aprendió contigo en el curso anterior. Ahora le toca lo siguiente: **la terminal de Linux**.
>
> Cada ejercicio arranca de un encargo real de la empresa: algo que le pide **Lucía**, su responsable, o un lío que le ha dejado **Carlos**, el senior que nunca documenta nada.

---

## **2 · 🛑 LOS TRES PASOS PREVIOS — NO TE LOS SALTES**

**Antes de abrir la Fase 1**, en este orden:

| # | Qué | Dónde está explicado |
| :--- | :--- | :--- |
| **1** | **Prepara tu sitio de trabajo:** descarga este curso y deja listo dónde vas a guardar todo | **[🛠️ Antes de empezar](01_ANTES_DE_EMPEZAR.md)** |
| **2** | **Entérate de qué tienes que entregar** y cómo se llaman tus ficheros | **[📦 Entregables](02_ENTREGABLES.md)** |
| **3** | **Empieza la Fase 1** | [Fase 1](fase-1-terminal-y-ficheros/README.md) |

> [!danger] 🛑 Si te saltas el paso 1, no tendrás dónde guardar el trabajo
> Y si te saltas el 2, escribirás los apuntes al final de memoria — que **cuenta como no entregado**.
>
> Son **veinte minutos** entre los dos. Te ahorran el curso entero.

---

## **3 · LAS SIETE FASES**

Cada fase tiene **su propio índice** con sus ejercicios ordenados por dificultad. Entra en la que toque:

| # | Fase | La idea central | Ejercicios | Dónde te va a servir |
| :--- | :--- | :--- | :---: | :--- |
| **1** | **[La terminal y el árbol de ficheros](fase-1-terminal-y-ficheros/README.md)** | Saber dónde estás y moverte sin miedo | 9 | En todo el curso |
| **2** | **[Identidad y permisos](fase-2-identidad-y-permisos/README.md)** | Quién eres y qué puedes hacer | 11 | Boochan **F5 y F6** |
| **3** | **[Tuberías y texto](fase-3-tuberias-y-texto/README.md)** | Encadenar comandos y preguntarle cosas al sistema | 9 | Las **verificaciones** de todas las fases |
| **4** | **[El sistema vivo](fase-4-sistema-vivo/README.md)** | Diagnosticar en vez de reiniciar | 9 | Boochan **F1 a F4** |
| **5** | **[Discos y montajes](fase-5-discos-y-montajes/README.md)** | Dónde viven los datos de verdad | 9 | Boochan **F6** |
| **6** | **[ACL](fase-6-acl/README.md)** | Cuando tres casillas de permisos no llegan | 9 | Boochan **F7** |
| **7** | **[Scripts](fase-7-scripts/README.md)** | Leer el código de los verificadores | 9 | Los `verificar_faseN.sh` |

> [!tip] 💡 Cómo se recorre
> **En orden.** Cada fase se apoya en la anterior: en la 6 vas a usar usuarios que creaste en la 2, y en la 7 vas a leer bucles que aprendiste en la 3.
>
> Dentro de cada fase, los ejercicios van **de menos a más**:
>
> | Nivel | Qué es |
> | :--- | :--- |
> | 🟢 **N1 · Mínimo** | Lo que no se puede no saber |
> | 🔵 **N2 · Básico** | El uso normal del día a día |
> | 🟡 **N3 · Medio** | Donde empieza a hacer falta pensar |
> | 🟠 **N4 · Avanzado** | Lo que separa a quien administra de quien copia |
> | 🔴 **N5 · Reto** | Sin procedimiento: te lo montas tú |

---

## **4 · CÓMO ES CADA EJERCICIO**

Todos siguen la misma estructura, así que en cuanto hagas dos ya sabes dónde está cada cosa:

```
📌 Ficha            código, fase, nivel, playlist y nombre del vídeo
💼 Situación        el encargo de Lucía o el lío de Carlos
📚 Fundamento       la idea, el error nº1, el vocabulario
🔗 Dónde lo usarás  la fase de Boochan en la que te hará falta
📹 Grabación        las obligaciones del vídeo
🛠️ Procedimiento    Paso 0 (abre tus apuntes) y los pasos del ejercicio
🚩 Errores          tabla: error · qué pasa · cómo evitarlo
🤔 Comprueba        las preguntas, que van en tus apuntes
✅ Entregables      qué subes y cómo se llama
🎓 Qué has aprendido + Siguiente
```

---

## **5 · LO QUE ENTREGAS**

**Cada ejercicio son tres cosas**, y las tres van juntas:

| | |
| :--- | :--- |
| 📝 **Una entrada de apuntes** | En tu repositorio `apuntes-sor-t1` |
| 📹 **Un vídeo** | En tu playlist `B0_Curso_Shell`, No listado |
| ⬆️ **El `push`** | Que sube la entrada a GitHub |

El detalle completo —ruta, nombres, plantilla copiable y cómo se entrega— está en **[📦 Entregables](02_ENTREGABLES.md)**.

---

## **6 · CUÁNTO TIEMPO LLEVA**

**~16 horas** en total, repartidas en varias semanas. No es una asignatura aparte: es **el terreno que hay que preparar** antes de tocar el servidor.

Yo te diré **qué fases toca hacer y cuándo**. No hace falta que te las hagas todas seguidas.

---

> [!summary] 🎓 Lo que te llevas de este curso
> Que la terminal **no es magia ni un examen de memoria**: es un puñado de herramientas que hacen una cosa cada una y se combinan entre sí.
>
> Y que la diferencia entre copiar un comando y entenderlo es **la misma que hay entre arreglar un servidor y esperar a que venga alguien**.
>
> **Empieza por:** [🛠️ Antes de empezar](01_ANTES_DE_EMPEZAR.md).
