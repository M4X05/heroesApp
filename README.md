# HeroesApp

Esta es una aplicación web completa construida con **Angular 16**. Es una aplicación de gestión (CRUD) que permite a los usuarios navegar, buscar, agregar, editar y eliminar superhéroes. La aplicación utiliza un módulo de autenticación para proteger las rutas y un backend simulado con `json-server`.

---

## Características Principales

* **Autenticación:** Módulo de inicio de sesión (`login.component.ts`) y registro que utiliza un servicio (`auth.service.ts`) para gestionar el estado del usuario.
* **Protección de Rutas (Guards):** Utiliza `AuthGuard` para proteger las rutas del módulo `heroes`, asegurando que solo los usuarios autenticados puedan acceder.
* **Gestión CRUD de Héroes:**
    * **Listar Héroes:** Muestra un listado completo de héroes en tarjetas (`listado.component.html`).
    * **Ver Detalles:** Muestra una página dedicada con la información de un solo héroe (`heroe.component.html`).
    * **Crear y Editar:** Un formulario reactivo (`agregar.component.html`) permite crear nuevos héroes o actualizar los existentes.
    * **Eliminar Héroe:** Incluye un diálogo de confirmación (`confirmar.component.html`) antes de eliminar un registro.
* **Búsqueda con Autocompletado:** Una página de búsqueda (`buscar.component.html`) que consume el servicio `getSugerencias` para mostrar resultados de autocompletado de Angular Material.
* **Pipe Personalizado:** Incluye un pipe (`imagen.pipe.ts`) para resolver y mostrar la imagen correcta de cada héroe o una imagen por defecto.
* **Diseño Responsivo:** Utiliza `@ngbracket/ngx-layout` (Flex Layout) y Angular Material para un diseño adaptable.

---

## Tecnologías Utilizadas

* **Framework:** Angular 16
* **UI:** Angular Material
* **Layout:** @ngbracket/ngx-layout (Flex Layout)
* **Estilos:** Bootstrap 5
* **Backend:** `json-server`

---

## Instalación y Puesta en Marcha

Este proyecto requiere **dos** terminales para ejecutarse: una para el backend y otra para el frontend.

### 1. Prerrequisitos

Tener instalado [Node.js].

### 2. Instalación de Dependencias

1.  Instala las dependencias de npm:
    ```bash
    npm install
    ```

### 3. Ejecutar el Backend (JSON-Server)

La aplicación está configurada para conectarse a `http://localhost:3000` para obtener los datos.

1.  Si no tienes `json-server` instalado globalmente, instálalo:
    ```bash
    npm install -g json-server
    ```
2.  En una terminal, inicia el servidor de `json-server` apuntando al archivo `db.json`:
    ```bash
    json-server --watch heroesApp2/db.json
    ```
3.  Deja esta terminal abierta. El servidor de datos estará corriendo en `http://localhost:3000`.

### 4. Ejecutar el Frontend (Angular)

1.  En una **segunda terminal**, ejecuta el script `start`:
    ```bash
    ng serve -o
    ```
2.  Esto levantará el servidor de desarrollo de Angular.
3.  Abre tu navegador y navega a `http://localhost:4200/`.

---

## Scripts

Estos scripts están definidos en el archivo `package.json`:

* **`npm start`**: Inicia el servidor de desarrollo en modo "watch".
* **`npm run build`**: Compila la aplicación para producción en el directorio `dist/heroes-app`.
* **`npm run watch`**: Compila en modo desarrollo y observa los cambios.
* **`npm test`**: Ejecuta las pruebas unitarias a través de Karma.

---

## Estructura del Proyecto

* **`src/app/auth`**: Contiene todo lo relacionado con la autenticación (login, registro, guard, servicio).
* **`src/app/heroes`**: Módulo principal de la aplicación.
    * **`components`**: Componentes reutilizables (tarjeta del héroe, diálogo de confirmación).
    * **`interfaces`**: Define la estructura de datos `Heroe` y `Publisher`.
    * **`pages`**: Los componentes principales de cada ruta (Listado, Agregar, Buscar, Heroe, Home).
    * **`pipes`**: Pipes personalizados.
    * **`services`**: Servicio `HeroesService` para manejar la comunicación HTTP.
* **`src/app/material`**: Módulo que importa y exporta todos los componentes de Angular Material.
* **`src/app/shared`**: Componentes compartidos, como la página de error (`ErrorPageComponent`).
* **`src/assets`**: Contiene las imágenes de los héroes y la imagen `no-image.png`.
* **`src/environments`**: Contiene las variables de entorno, como la `baseUrl` del backend.
* **`heroesApp2/db.json`**: Archivo de base de datos simulada para `json-server`.
