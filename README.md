# 🧪 Reto Técnico — Frontend Senior (Microfrontends + React)

## Postulación: Desarrollador Frontend Senior

Este reto técnico evalúa tus habilidades en **desarrollo frontend con React**, **arquitectura modular y microfrontends**, **manejo de estado y data fetching**, **buenas prácticas de desarrollo** y **experiencia de usuario**, mediante la implementación de una aplicación **funcional y escalable**.

El alcance ha sido diseñado para ser **simple y de rápida implementación**, pero lo suficientemente **robusto** como para evaluar un **perfil senior**, priorizando **calidad técnica**, **claridad arquitectónica** y **criterio de diseño**.

---
⏳ Tiempo Máximo de Desarrollo (Obligatorio)

La prueba debe ser desarrollada y entregada en un plazo máximo de:

2 días calendario desde el inicio del reto.

Se evaluará el cumplimiento funcional dentro del tiempo límite, así como la calidad técnica del resultado.

---
## 🚀 1. Objetivo del Reto

Implementar una solución **Frontend** basada en **Microfrontends** que incluya:

- Login y sesión de usuario.
- Home con categorías (tipos) y listado de Pokémon.
- Buscador con modal fullscreen e infinite scroll.
- Detalle de Pokémon (Microfrontend 1).
- Historial de Pokémon visitados (Microfrontend 2).
- Tema claro / oscuro.
- Toast al recargar con el último Pokémon visitado.

---

## 🏗️ 2. Arquitectura General

La solución consta de **3 aplicaciones**:

### 1. Shell (Host)
- Login.
- Home.
- Layout general.
- Navegación.
- Buscador (modal fullscreen).
- Manejo de theme.
- Usuario logueado con dropdown (cerrar sesión).
- Toast global.

### 2. Microfrontend 1 — Detalle de Pokémon
- Muestra el detalle del Pokémon seleccionado.
- Se abre desde Home o desde el buscador.

### 3. Microfrontend 2 — Historial
- Muestra el historial de Pokémon visitados.
- Conteo de visitas por Pokémon.
- Persistencia de datos.

---

## 🔌 3. Puertos (Obligatorio)

- Shell (Host): http://localhost:3000
- Microfrontend 1: http://localhost:3001
- Microfrontend 2: http://localhost:3002

---

## 🧰 4. Stack y Librerías

### Requerido
- React ≥ 16
- Vite
- Module Federation (Microfrontends)

### Estilos (elige)
- CSS
- CSS Modules
- Tailwind CSS
- Styled Components

### Estado / Data Fetching (elige)

**State Management (elige 1):**
- Redux
- Redux Toolkit
- Zustand

**Data Fetching (elige 1):**
- RTK Query
- TanStack Query
- SWR
- Axios

> Si se utiliza Axios, se espera manejo correcto de loading, error y estados de red.

---

## 🌐 5. Integración con PokeAPI

### Obtener Pokémon por categoría (Tipo)
**GET** `https://pokeapi.co/api/v2/type/{type}`  
Ejemplo: **GET** `https://pokeapi.co/api/v2/type/fire`

- Listar Pokémon por categoría.
- Mostrar **10 Pokémon por categoría** en Home.

---

### Listado inicial del buscador
**GET** `https://pokeapi.co/api/v2/pokemon?limit=30&offset=0`

- Mostrar **30 Pokémon por defecto** al abrir el modal.
- Implementar **scroll infinito**, cargando 30 más al llegar al final (`offset += 30`).

---

### Búsqueda de Pokémon por nombre (Exact Match)
**GET** `https://pokeapi.co/api/v2/pokemon/{name}`  
Ejemplo: **GET** `https://pokeapi.co/api/v2/pokemon/pikachu`

**Reglas:**
- El nombre debe coincidir **exactamente** con el usado por la API.
- Todo en **lowercase**.
- Sin espacios ni acentos.
- No es búsqueda por fragmento.

**Comportamiento:**
- Si existe → mostrar **solo ese Pokémon**.
- Si no existe → mostrar estado **“No encontrado”**.

---

### Detalle del Pokémon
**GET** `https://pokeapi.co/api/v2/pokemon/{id}`  
Ejemplo: **GET** `https://pokeapi.co/api/v2/pokemon/4`

- Usar la información retornada para el detalle del Pokémon.
- Renderizar la imagen preferentemente en **SVG sin fondo** cuando esté disponible.

---

## 🧾 6. Microfrontend 1 — Detalle de Pokémon

Debe mostrar como mínimo:
- Imagen del Pokémon (preferentemente SVG sin fondo).
- Nombre.
- Tipos.
- Stats básicos.

---

## 🕒 7. Microfrontend 2 — Historial

Debe mostrar:
- Lista de Pokémon visitados.
- Imagen.
- Nombre.
- Conteo de visitas por Pokémon.

Persistencia obligatoria (ej: localStorage).

---

## 🧠 8. Estrategia de Historial

Se debe implementar una estrategia para:
- Guardar los Pokémon visitados.
- Incrementar el contador de visitas al abrir el detalle.
- Evitar duplicados.
- Mantener persistencia entre recargas.

Ejemplo de estructura referencial:
```ts
{
  name: string;
  image: string;
  visits: number;
}
```
La decisión debe estar documentada en el README.

## 🔔 9. Toast al Recargar

- Al recargar la página:
  - Si existe un último Pokémon visitado, mostrar un toast.
- El toast debe tener botón **Cerrar**.
- Si el usuario lo cierra:
  - No debe volver a mostrarse hasta que exista una nueva visita a un Pokémon.

---

## ✨ 10. Recomendaciones (Se valorará)

- Tema claro / oscuro bien implementado.
- Transiciones y animaciones fluidas.
- Diseño responsive.
- Manejo correcto de loading, error y empty states.
- Buen rendimiento y UX cuidada.

---

## 🧪 11. Criterios de Evaluación

### Arquitectura (30%)
- Separación de responsabilidades.
- Uso correcto de microfrontends.
- Integración limpia con el Shell.

### Funcionalidad (30%)
- Home con categorías.
- Buscador con infinite scroll.
- Búsqueda exacta por nombre.
- Detalle funcional.
- Historial persistente.
- Toast al recargar.

### Calidad de Código (20%)
- Organización.
- Legibilidad.
- Buen manejo de estado y data fetching.

### UX / UI (20%)
- Navegación clara.
- Tema.
- Transiciones.
- Feedback visual.

---

## 🖼️ 12. Pantallas Referenciales

A continuación se muestran **pantallas referenciales** que sirven como guía visual del resultado esperado del reto.

> Estas imágenes son solo de referencia y **no representan un diseño obligatorio**.  
> El candidato es libre de proponer su propia solución visual siempre que cumpla con los requerimientos funcionales.

### Login | Home | Buscador (Modal Fullscreen) | Toast Último Pokémon Visitado
<!-- Inserta aquí la imagen -->
<!-- ![Login](screenshots/login.png) -->
![shell3000](https://github.com/user-attachments/assets/9eec060a-bfb3-4e2e-99a3-21cef8ba1881)

### Detalle de Pokémon
<!-- Inserta aquí la imagen -->
<!-- ![Pokemon Detail](screenshots/pokemon-detail.png) -->
![MF1](https://github.com/user-attachments/assets/e6fa119a-79af-474e-8eb6-9a85f5616fc8)

### Historial
<!-- Inserta aquí la imagen -->
<!-- ![History](screenshots/history.png) -->
![MF2](https://github.com/user-attachments/assets/77590b96-f07b-4ba4-888a-27acd0fa16e6)


---

## 📬 13. Entrega Final

El candidato debe entregar:

- Código fuente completo en repositorio (GitHub o GitLab).
- README documentado con:
  - Pasos de instalación.
  - Scripts.
  - Cómo levantar Shell y Microfrontends.
  - Decisiones técnicas.
- (Opcional) Deploy demo.

---

## 🎯 14. Resultado Esperado

Una aplicación **Frontend** basada en **Microfrontends**, funcional y bien estructurada, que demuestre experiencia real en **React**, arquitectura modular y buenas prácticas profesionales.
