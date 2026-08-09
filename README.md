# Curso de Shell de Linux — 2.º SMR (práctica independiente)

> **Módulo:** SOR — Sistemas Operativos en Red · **Profesor:** Pedro Navarro Miralles · IES Jorge Juan (Alicante)
> **Autor y propietario:** © 2026 Pedro Navarro Miralles. **Licencia:** [CC BY-NC-SA 4.0](LICENSE) — atribución obligatoria, uso no comercial.

## Qué es este curso (y por qué existe)

Es un **curso de terminal de Linux autocontenido**, en forma de simulación: sigues a **Marko**, un técnico junior ficticio, y aprendes a administrar un sistema **desde cero**, en tu propia máquina virtual.

Y existe por una razón muy concreta.

> [!danger] 🎯 El problema que este curso resuelve
> En el **Bloque 2 (Boochan)** montas un servidor Ubuntu con Samba AD DC, VPN, cuotas, montajes y ACL. Ocho fases.
>
> A partir de la **Fase 6** —montajes, `fstab`, setgid, sticky bit— y sobre todo en la **Fase 7** —ACL, máscara, `setfacl`— mucha gente deja de entender lo que escribe y empieza a **copiar comandos**. No porque el material esté mal, sino porque da por sabido un nivel de terminal que nadie ha enseñado.
>
> **Este curso es ese repaso que falta.** El objetivo es uno y se puede medir: que el día que veas
>
> ```
> sudo setfacl -m g:comercial:rx /srv/samba/departamentos/rrhh
> ```
>
> sepas exactamente qué estás escribiendo, trozo a trozo, y por qué no es `r` en vez de `rx`.

> [!important] Es INDEPENDIENTE de tu trabajo real
> Este curso vive en **la máquina virtual de Marko**, separada del servidor Boochan con el que trabajas de verdad. Aquí se rompe todo lo que haga falta: es un laboratorio. La forma de trabajar es la misma, pero **no se mezclan**.

---

## El escenario y los personajes

Los mismos del [curso de Git](../curso-git-template/README.md):

- **Marko** — 19 años, recién titulado en SMR. Técnico junior en **Boochan Networks S.L.** Ya documenta con Git; ahora le toca aprender la terminal, porque en un servidor no hay ratón.
- **Boochan Networks S.L.** — PYME ficticia de 12 empleados que da soporte de infraestructura. Tiene un servidor con Active Directory, VPN y almacenamiento por departamentos.
- **Carlos** — técnico *senior*. Lo sabe todo y **nunca documenta nada**. Suelta la respuesta correcta a medias y vuelve a su monitor.
- **Lucía** — **responsable de IT**. Es quien encarga el trabajo, quien lo revisa y quien no acepta un *"ya está hecho"* sin pruebas.

**Cada ejercicio arranca de un encargo real de la empresa**, no de un enunciado abstracto. No hay ni un solo *"cree un directorio llamado prueba1"*.

---

## Entorno: una VM con Ubuntu **Desktop**

Todo el curso se hace en una **máquina virtual con Ubuntu Desktop** sobre VirtualBox. La montas tú en el primer ejercicio (`EJ-01-01-01`).

**Desktop y no Server, a propósito:** todavía no estás administrando un servidor, estás aprendiendo a hablar con el sistema. Tener navegador y escritorio al lado te quita fricción. El Server llega en el Bloque 2.

> [!warning] La instantánea no es opcional
> Vas a provocar averías reales: un `fstab` roto que deja la máquina en modo emergencia, permisos que se cargan un acceso, ficheros que desaparecen. **Todo eso es el ejercicio, no un accidente.** Por eso el curso te hace tomar instantáneas de VirtualBox antes de cada operación de riesgo. Hazlas.

---

## Cómo está montado el curso

**Siete fases**, cada una con una idea central. La numeración de los ejercicios es `EJ-0F-NN-MM` = **fase · nivel · número**, igual que en el curso de Git.

### Los cinco niveles

| Nivel | Nombre | Qué es |
| :--- | :--- | :--- |
| **N1** | Mínimo | Lo imprescindible. Sin esto no se puede seguir. |
| **N2** | Básico | El uso normal del día a día. |
| **N3** | Medio | Donde empieza el criterio técnico. |
| **N4** | Avanzado | Lo que separa administrar de ejecutar comandos. |
| **N5** | Reto | **Sin procedimiento.** Se da el objetivo y tú eliges el camino. |

Los **retos N5** son la parte que de verdad evalúa: no traen pasos numerados, traen un encargo de Lucía y unas pruebas que hay que superar.

---

## Índice de fases

> [!danger] 🛑 EMPIEZA POR AQUÍ: **[🐧 Índice general del curso](00_INDICE.md)**
> Ahí tienes el mapa completo: las siete fases, cómo funciona cada ejercicio y **los tres pasos previos que hay que dar antes de la Fase 1**.
>
> Y esos tres pasos, por orden:
> 1. **[🛠️ Antes de empezar](01_ANTES_DE_EMPEZAR.md)** — traer el curso a tu ordenador y dejar listo dónde guardas todo. **15 minutos.**
> 2. **[📦 Entregables](02_ENTREGABLES.md)** — qué se entrega, cómo se llama y cómo se sube. **5 minutos.**
> 3. Y ya sí, la [Fase 1](fase-1-terminal-y-ficheros/README.md).
>
> Ahí está **dónde van tus apuntes, cómo se llama cada entrada, qué lleva dentro y cómo se sube**. Y hay una razón para leerlo ahora y no luego:
>
> **Cada ejercicio produce TRES entregables** —una entrada de apuntes, un vídeo y el `push` que la sube—, y **la entrada se abre al empezar el ejercicio, no al terminarlo**.
>
> Si te pones a hacer ejercicios y dejas los apuntes para el final, o los escribes de memoria —y se nota— o los pierdes. Las dos cosas cuentan como **no entregado**.



| Fase | Carpeta | Idea central | Aterriza en |
| :--- | :--- | :--- | :--- |
| **1** | [fase-1-terminal-y-ficheros](fase-1-terminal-y-ficheros/README.md) | Saber dónde estás y moverte sin miedo | Todo el itinerario |
| **2** | [fase-2-identidad-y-permisos](fase-2-identidad-y-permisos/README.md) | Quién eres y qué puedes hacer | Boochan **F5 y F6** |
| **3** | [fase-3-tuberias-y-texto](fase-3-tuberias-y-texto/README.md) | Encadenar comandos y preguntar lo que quieres saber | Las verificaciones de **todas** las fases |
| **4** | [fase-4-sistema-vivo](fase-4-sistema-vivo/README.md) | Diagnosticar en vez de reiniciar a ciegas | Boochan **F1–F4** |
| **5** | [fase-5-discos-y-montajes](fase-5-discos-y-montajes/README.md) | Dónde viven los datos y por qué desaparecen | Boochan **F6** |
| **6** | [fase-6-acl](fase-6-acl/README.md) | Cuando tres casillas de permisos no llegan | Boochan **F7** |
| **7** | [fase-7-scripts](fase-7-scripts/README.md) | Leer el bash que hasta ahora era magia negra | Los `verificar_faseN.sh` |

**65 ejercicios** en total, más siete cierres de fase.

### Por qué estas siete fases y no otras

No están inventadas: salen de **barrer las ocho fases del Bloque 2, la Auditoría Final y los siete `verificar_faseN.sh`**, y sacar el inventario completo de comandos y construcciones que el alumno tiene que ejecutar o leer. A eso se le añadió lo que el material **da por sabido y no está enseñado en ninguna parte** (`man`, rutas relativas, `ls -l` leído entero, stdout frente a stderr, comillas, procesos).

El criterio de agrupación es que **cada fase tenga una idea, no una lista de comandos**. Y el orden es de dependencia real: no se puede entender una ACL sin entender permisos clásicos, ni un `fstab` sin entender rutas, ni un verificador sin entender tuberías.

> [!info] 🔗 Cada ejercicio dice dónde se usa
> Todos los ejercicios llevan un callout **🔗 Dónde lo vas a usar** que apunta a la fase concreta de Boochan donde aparece eso. No es decoración: es lo que convierte el curso en un repaso útil en vez de teoría suelta.

---

## 📹 Grabación y entrega (LÉEME — aplica a TODOS los ejercicios)

Igual que en la Fase 0 y en el curso de Git, **cada ejercicio se graba entero con OBS**, de principio a fin. No es un repaso al final: se ve **cómo lo haces tú**. Cada ejercicio trae su caja **📹 Grabación** y un **Paso 0** para prepararte y arrancar.

> [!important] Las 5 reglas de grabación
> 1. **Grabación completa con OBS**, sin cortes, hablando lo que haces.
> 2. **Preséntate al empezar** y **muestra tu identidad** en pantalla (Teams, correo `@alu.edu.gva.es` o tu perfil de GitHub). Di qué vas a hacer.
> 3. **Timestamps SIEMPRE** en la descripción: `00:00 Presentación` y **uno por cada paso** (`mm:ss`).
> 4. **Nombre del vídeo:** `SF.N.M · <título>` — donde `F.N.M` = **fase . nivel . ejercicio**. Ejemplo: `B0.S.6.3.1 · Marko descubre la máscara`.
> 5. **Súbelo a tu playlist del curso** como **"No listado"**.

> [!info] La `S` del principio
> El curso de Git usa `B0.G.1.1.1`. Este usa **`B0.S.1.1.1`** — `S` de *Shell* — para que un vídeo suelto se sepa de qué curso sale sin abrirlo. Son dos cursos distintos del mismo Bloque 0 y sus vídeos conviven en el mismo canal.

> [!info] 🎬 UNA sola playlist para todo el curso
> Se llama **`B0_Curso_Shell`** — igual que tu carpeta de apuntes y que la carpeta del material. La creas una vez, al principio, y ahí van **todos** los vídeos del curso.
>
> **No hagas una playlist por fase.** El vídeo ya lleva la fase en su nombre (`B0.S.1.2.1`), así que dentro de la playlist salen ordenados solos.

> [!warning] Entrega ÚNICA (no se duplica casa/centro)
> Igual que en el curso de Git: se graba y se sube el vídeo **una sola vez**. Los entregables escritos (scripts, informes, notas) van a tu **repositorio de apuntes**, dentro de la entrada de cada ejercicio.

---

## Qué hay que entregar, además del vídeo

Cada ejercicio pide dos cosas más:

- **Apuntes:** **una entrada por ejercicio** en `00_Apuntes/Trimestre_1/B0_Curso_Shell/`, con el nombre que te da el propio ejercicio en su Paso 0 (`shell-1.2.1-se-mueve-por-el-arbol.md`). **No son capturas de pantalla:** son salidas de comandos pegadas y explicadas con tus palabras. La estructura obligatoria está en **[📦 Entregables](02_ENTREGABLES.md)**.
- **Ficheros de trabajo:** a partir de la Fase 3 empiezas a generar informes (`auditoria.txt`, `inventario.txt`) y a partir de la Fase 7, scripts (`verificar-v2.sh`). Todo va al repositorio.

> [!question] Las preguntas no se responden copiando
> Todos los ejercicios acaban con preguntas del tipo *"con tus palabras"*, *"un ejemplo tuyo distinto"*, *"predice qué pasaría"*. Están escritas así a propósito: si la respuesta se puede copiar del enunciado, no demuestra nada.

---

## No todo es obligatorio para todos

- El **núcleo** son las Fases 1, 2 y 3: sin eso no se sigue el Bloque 2.
- Las Fases **5 y 6** son la preparación directa de las Fases 6 y 7 de Boochan, que es donde se atasca la gente. Si vas justo de tiempo, **estas dos no se saltan**.
- La Fase **7** (scripts) es la que convierte al alumno en alguien que **lee** lo que ejecuta. Es ampliación, y es la que más se nota.

El profesor indicará qué parte toca en cada momento.

---

> [!tip] Por dónde se empieza
> Por el **[🐧 Índice general](00_INDICE.md)**, que te lleva a los tres pasos previos. **No abras la Fase 1 directamente:** sin el paso 1 no tienes dónde guardar el trabajo.
