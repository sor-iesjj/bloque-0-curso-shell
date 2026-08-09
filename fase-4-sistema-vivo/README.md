# FASE 4 — El sistema vivo: servicios, paquetes y red

**Duración estimada:** 5 h · **Idea central:** Diagnosticar en vez de reiniciar a ver si suena la flauta

Un servidor no tiene ventanas. Sus programas son servicios, su red se consulta con comandos y sus fallos están escritos en los logs. Esta fase enseña a preguntarle al sistema qué le pasa.

**La idea central de la fase:** ante un fallo, cada comprobación sirve para **descartar** una capa. Eso es un diagnóstico; lo demás es probar cosas.

---

> [!important] ✍️ Cada ejercicio de esta fase son TRES entregables
> | | |
> | :--- | :--- |
> | 📝 **Una entrada de apuntes** | En `00_Apuntes/Trimestre_1/B0_Curso_Shell/`. **El nombre exacto te lo da cada ejercicio en su Paso 0** |
> | 📹 **Un vídeo** | En la playlist `B0_Curso_Shell` (No listado), con timestamps |
> | ⬆️ **El `push`** | Que sube la entrada a tu repositorio |
>
> **La entrada se abre ANTES de empezar el ejercicio**, no al terminarlo. La plantilla y qué va dentro: **[📦 Entregables](../02_ENTREGABLES.md)**.

---

## Índice de ejercicios

### 🟢 N1 — Mínimo (2 ejercicios)

- [`EJ-04-01-01`](EJ-04-01-01.md) — Marko arranca y para un servicio con `systemctl`
- [`EJ-04-01-02`](EJ-04-01-02.md) — Marko distingue `enable` de `start` (y lo comprueba reiniciando)

### 🔵 N2 — Básico (2 ejercicios)

- [`EJ-04-02-01`](EJ-04-02-01.md) — Marko lee los logs de un servicio caído con `journalctl`
- [`EJ-04-02-02`](EJ-04-02-02.md) — Marko instala, comprueba y purga software con `apt` y `dpkg`

### 🟡 N3 — Medio (2 ejercicios)

- [`EJ-04-03-01`](EJ-04-03-01.md) — Marko mira la red: `ip`, `ping` y `hostname -I`
- [`EJ-04-03-02`](EJ-04-03-02.md) — Marko averigua quién escucha en cada puerto con `ss`

### 🟠 N4 — Avanzado (2 ejercicios)

- [`EJ-04-04-01`](EJ-04-04-01.md) — Marko separa "hay camino" de "hay DNS"
- [`EJ-04-04-02`](EJ-04-04-02.md) — Marko mira los procesos y mata uno

### 🔴 N5 — Reto (1 ejercicio)

- [`EJ-04-05-01`](EJ-04-05-01.md) — RETO — Marko diagnostica un servidor "que no funciona"

---

### 🏁 Cierre

- [`Cierre_Fase_4`](Cierre_Fase_4.md) — repaso, preguntas y tabla de verificación **antes de pasar a la siguiente fase**.

---

> [!info] 🎬 Grabación
> Todos los ejercicios de esta fase se graban y se suben a la playlist **`B0_Curso_Shell`**, como *No listado*. El nombre del vídeo es `S4.N.M · título`. Las obligaciones completas están en cada ejercicio y en el [README del curso](../README.md).

[← Volver al índice del curso](../README.md)
