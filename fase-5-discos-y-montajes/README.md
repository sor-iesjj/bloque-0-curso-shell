# FASE 5 — Discos, montajes y fstab

**Duración estimada:** 5 h · **Idea central:** Dónde viven los datos, y por qué a veces desaparecen

En Linux los discos no tienen letra: se enganchan a una carpeta. Esta fase va de fabricar volúmenes, montarlos, hacerlo permanente y sobrevivir al fichero fantasma y al modo emergencia.

**La idea central de la fase:** una ruta no siempre apunta a donde crees. Comprobarlo es un comando.

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

- [`EJ-05-01-01`](EJ-05-01-01.md) — Marko mira cuánto espacio queda: `df` y `du`
- [`EJ-05-01-02`](EJ-05-01-02.md) — Marko entiende qué significa "montar" un sistema de ficheros

### 🔵 N2 — Básico (2 ejercicios)

- [`EJ-05-02-01`](EJ-05-02-01.md) — Marko fabrica un disco con `dd` y lo formatea con `mkfs.ext4`
- [`EJ-05-02-02`](EJ-05-02-02.md) — Marko monta a mano y descubre que al reiniciar desaparece

### 🟡 N3 — Medio (2 ejercicios)

- [`EJ-05-03-01`](EJ-05-03-01.md) — Marko lo hace permanente con `/etc/fstab`
- [`EJ-05-03-02`](EJ-05-03-02.md) — Marko provoca el modo emergencia y aprende a salir

### 🟠 N4 — Avanzado (2 ejercicios)

- [`EJ-05-04-01`](EJ-05-04-01.md) — Marko descubre el fichero fantasma
- [`EJ-05-04-02`](EJ-05-04-02.md) — Marko inspecciona el almacenamiento: `stat`, `blkid` y `lsblk`

### 🔴 N5 — Reto (1 ejercicio)

- [`EJ-05-05-01`](EJ-05-05-01.md) — RETO — Marko reproduce el almacenamiento completo de Boochan

---

### 🏁 Cierre

- [`Cierre_Fase_5`](Cierre_Fase_5.md) — repaso, preguntas y tabla de verificación **antes de pasar a la siguiente fase**.

---

> [!info] 🎬 Grabación
> Todos los ejercicios de esta fase se graban y se suben a la playlist **`B0_Curso_Shell`**, como *No listado*. El nombre del vídeo es `S5.N.M · título`. Las obligaciones completas están en cada ejercicio y en el [README del curso](../README.md).

[← Volver al índice del curso](../README.md)
