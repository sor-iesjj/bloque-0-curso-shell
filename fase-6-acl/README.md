# FASE 6 — ACL: cuando los permisos clásicos no bastan

**Duración estimada:** 6 h · **Idea central:** Cuando tres casillas de permisos no llegan

Los permisos clásicos tienen un dueño, **un** grupo y los demás. Cuando hacen falta tres grupos con tres niveles distintos sobre la misma carpeta, se acaban. Esta fase es la preparación directa de la Fase 7 de Boochan, que es donde más gente se atasca.

**La idea central de la fase:** una ACL es una lista, y las listas no tienen límite de nombres. Pero tienen máscara, herencia y orden de evaluación.

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

- [`EJ-06-01-01`](EJ-06-01-01.md) — Marko topa con el muro: los permisos clásicos solo tienen UN grupo
- [`EJ-06-01-02`](EJ-06-01-02.md) — Marko instala `acl` y lee su primera lista con `getfacl`

### 🔵 N2 — Básico (2 ejercicios)

- [`EJ-06-02-01`](EJ-06-02-01.md) — Marko da acceso a un segundo grupo con `setfacl -m`
- [`EJ-06-02-02`](EJ-06-02-02.md) — Marko quita una ACL: `setfacl -x` y `setfacl -b`

### 🟡 N3 — Medio (2 ejercicios)

- [`EJ-06-03-01`](EJ-06-03-01.md) — Marko descubre la máscara: el permiso que figura y no funciona
- [`EJ-06-03-02`](EJ-06-03-02.md) — Marko hace que lo nuevo herede: la ACL por defecto (`-d`)

### 🟠 N4 — Avanzado (2 ejercicios)

- [`EJ-06-04-01`](EJ-06-04-01.md) — Marko comprueba desde la piel del usuario (y descubre el orden de evaluación)
- [`EJ-06-04-02`](EJ-06-04-02.md) — Marko aplica en bloque y audita toda una estructura

### 🔴 N5 — Reto (1 ejercicio)

- [`EJ-06-05-01`](EJ-06-05-01.md) — RETO — Marko implanta la matriz de permisos completa de Boochan

---

### 🏁 Cierre

- [`Cierre_Fase_6`](Cierre_Fase_6.md) — repaso, preguntas y tabla de verificación **antes de pasar a la siguiente fase**.

---

> [!info] 🎬 Grabación
> Todos los ejercicios de esta fase se graban y se suben a la playlist **`B0_Curso_Shell`**, como *No listado*. El nombre del vídeo es `S6.N.M · título`. Las obligaciones completas están en cada ejercicio y en el [README del curso](../README.md).

[← Volver al índice del curso](../README.md)
