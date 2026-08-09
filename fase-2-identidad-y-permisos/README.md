# FASE 2 — Identidad y permisos clásicos

**Duración estimada:** 5 h · **Idea central:** Quién eres y qué puedes hacer

Marko ya se mueve. Ahora tiene que entender por qué a veces el sistema le dice que no. Esta fase va de identidad —usuarios y grupos— y del modelo de permisos de Unix, hasta sus límites.

**La idea central de la fase:** los permisos no se dan a personas, se dan a usuarios y grupos, y hay que saber leerlos en los dos idiomas: letras y números.

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

- [`EJ-02-01-01`](EJ-02-01-01.md) — Marko averigua quién es para el sistema
- [`EJ-02-01-02`](EJ-02-01-02.md) — Marko entiende `sudo` y por qué nadie trabaja como root

### 🔵 N2 — Básico (3 ejercicios)

- [`EJ-02-02-01`](EJ-02-02-01.md) — Marko lee `ls -l` entero, carácter a carácter
- [`EJ-02-02-02`](EJ-02-02-02.md) — Marko cambia el dueño y el grupo con `chown`
- [`EJ-02-02-03`](EJ-02-02-03.md) — Marko descubre que la `x` de una carpeta es un peaje, no un permiso de ejecución

### 🟡 N3 — Medio (2 ejercicios)

- [`EJ-02-03-01`](EJ-02-03-01.md) — Marko cambia permisos en numérico (`chmod 750`)
- [`EJ-02-03-02`](EJ-02-03-02.md) — Marko cambia permisos en simbólico (`chmod g+w`)

### 🟠 N4 — Avanzado (3 ejercicios)

- [`EJ-02-04-01`](EJ-02-04-01.md) — Marko descubre el setgid: la `s` de `drwxrws---`
- [`EJ-02-04-02`](EJ-02-04-02.md) — Marko protege la carpeta común con el sticky bit
- [`EJ-02-04-03`](EJ-02-04-03.md) — Marko traduce permisos en las dos direcciones, incluidos los cuatro dígitos

### 🔴 N5 — Reto (1 ejercicio)

- [`EJ-02-05-01`](EJ-02-05-01.md) — RETO — Marko implanta la estructura de permisos de Boochan

---

### 🏁 Cierre

- [`Cierre_Fase_2`](Cierre_Fase_2.md) — repaso, preguntas y tabla de verificación **antes de pasar a la siguiente fase**.

---

> [!info] 🎬 Grabación
> Todos los ejercicios de esta fase se graban y se suben a la playlist **`B0_Curso_Shell`**, como *No listado*. El nombre del vídeo es `S2.N.M · título`. Las obligaciones completas están en cada ejercicio y en el [README del curso](../README.md).

[← Volver al índice del curso](../README.md)
