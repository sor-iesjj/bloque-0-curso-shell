# Curso de Shell de Linux — 2.º SMR (práctica independiente)

> **Módulo:** SOR — Sistemas Operativos en Red · **Profesor:** Pedro Navarro Miralles · IES Jorge Juan (Alicante)
> **Autor y propietario:** © 2026 Pedro Navarro Miralles. **Licencia:** [CC BY-NC-SA 4.0](LICENSE) — atribución obligatoria, uso no comercial.

## Qué es este curso (y por qué existe)

Es un **curso de terminal de Linux autocontenido**, en forma de simulación: sigues a **Marko**, un técnico junior ficticio, y aprendes a administrar un sistema **desde cero**, en tu propia máquina virtual.

Y existe por una razón muy concreta.

> [!danger] 🎯 El problema que este curso resuelve
> Más adelante, en el **Bloque 2**, construirás el servidor de **Boochan**. Boochan Networks S.L. es la empresa ficticia que usamos como historia del curso. Ese servidor requerirá tareas de red, usuarios y almacenamiento que aquí solo aprenderás a reconocer. **Aún no tienes que saber hacerlas.**
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

Son los mismos personajes del curso de Git que guardas en `SOR/Boveda_Marko/B0_Curso_Git/`:

- **Marko** — 19 años, recién titulado en SMR. Técnico junior en **Boochan Networks S.L.** Ya documenta con Git; ahora le toca aprender la terminal, porque en un servidor no hay ratón.
- **Boochan Networks S.L.** — PYME ficticia de 12 empleados que da soporte de infraestructura. Tiene un servidor con Active Directory, VPN y almacenamiento por departamentos.
- **Carlos** — técnico *senior*. Lo sabe todo y **nunca documenta nada**. Suelta la respuesta correcta a medias y vuelve a su monitor.
- **Lucía** — **responsable de IT**. Es quien encarga el trabajo, quien lo revisa y quien no acepta un *"ya está hecho"* sin pruebas.

**Cada ejercicio arranca de un encargo real de la empresa**, no de un enunciado abstracto. No hay ni un solo *"cree un directorio llamado prueba1"*.

---

## Recorridos actuales y entorno

Todo el recorrido disponible se realiza en una VM con Ubuntu Server y SSH. Fase 0 prepara el entorno; Fase 1 enseña terminal y ficheros. Cada guía de Casa es autónoma y no presupone que se haya hecho Cole.

- [Fase 0 · Cole](fase-0-preparar-laboratorio/Cole/README.md) → [Fase 1 · Cole](fase-1-terminal-y-ficheros/Cole/README.md)
- [Fase 0 · Casa](fase-0-preparar-laboratorio/Casa/README.md) → [Fase 1 · Casa](fase-1-terminal-y-ficheros/Casa/README.md)

Las prácticas del alumno viven fuera de la carpeta real `SOR` para evitar que una orden ejecutada por despiste dañe los apuntes reales. Cada contexto mantiene su propia bóveda, repositorio de apuntes, VM, tarea de Teams y playlist. Los repositorios del profesor se clonan solo para consultar.

## Organización y entrega

La Fase 0 contiene cuatro prácticas y la Fase 1 nueve ejercicios. En cada contexto, se guarda una bitácora persistente y evidencias a medida que se avanza; Git versiona el trabajo del proyecto, no los comandos pasajeros de la VM.

Cada fase/contexto tiene una tarea independiente y una playlist propia. Al cerrar la fase, se entrega un solo vídeo final de esa fase y dos enlaces de ese mismo contexto: el repositorio de apuntes y su playlist. No se solicita un vídeo por ejercicio. Las guías indican cómo grabar los pasos, guardar evidencias y cerrar la entrega.

Fases 2–7 conservan material anterior todavía no adaptado a las bóvedas y repositorios independientes. No están disponibles como continuación de estos recorridos.

[Índice general del curso](00_INDICE.md)
