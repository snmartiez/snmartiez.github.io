---
layout: post
title: "Crear una API REST"
date: 2024-10-21
---

## Guía para crear una API REST utilizando Express

### Introducción

**Express** es un framework de Node.js que facilita la creación de servidores web y APIs RESTful. Nos permite gestionar rutas, middleware y controladores de manera eficiente y con una estructura limpia. En esta guía, aprenderás cómo configurar un servidor Express, cómo manejar rutas y controladores, y cómo estructurar tu proyecto en múltiples archivos.

### Requisitos previos

- Conocimientos básicos de JavaScript y Node.js.
- Tener instalado Node.js y npm (Node Package Manager).
Puedes descargar [Node.js](https://nodejs.org) desde su sitio oficial.

### 1. Crear un servidor con Express

Lo primero que necesitamos es instalar Express y configurar el servidor. Sigue estos pasos:

#### **Paso 1: Inicializa un proyecto Node.js**
En tu terminal, ejecuta los siguientes comandos para crear un nuevo proyecto:
-  Creamos un directorio o carpeta
-  Accedemos al directorio
-  Generaramos un archivo package.json con la configuración básica del proyecto.
{% highlight bash %}
   mkdir api-rest
   cd api-rest
   npm init -y
{% endhighlight %}

### Paso 2: Instala Express
Ahora instala Express:
{% highlight bash %}
npm install express
{% endhighlight %}

### Paso 3: Crea el archivo principal del servidor
Crea un archivo llamado index.js en la raíz de tu proyecto. Este archivo será el punto de entrada de nuestra API. Aquí es donde configuraremos el servidor con Express.

{% highlight javascript %}
// server.js
const express = require('express');
const app = express();
const PORT = 3000;

app.use(express.json()); // Middleware para manejar JSON

// Ruta principal
app.get('/', (req, res) => {
  res.send('¡Bienvenido a la API!');
});

// Iniciar el servidor
app.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});

{% endhighlight %}

### Explicación:
- express(): Crea una instancia de Express.
- app.use(express.json()): Middleware que permite que nuestra API maneje peticiones con cuerpos en formato JSON.
- app.get('/', ...): Define una ruta GET en la raíz del servidor. Al acceder a esta ruta, responderá con "¡Bienvenido a la API!".
- app.listen(PORT, ...): Inicia el servidor en el puerto 3000 y espera solicitudes.
  
Para iniciar el servidor, ejecuta:
{% highlight bash %}
   node index.js
{% endhighlight %}
Visita http://localhost:3000 y deberías ver el mensaje "¡Bienvenido a la API!".
<hr>


### 2. Qué es una Ruta en Express

Una ruta es una dirección URL específica que se define en nuestro servidor y está asociada con una acción o respuesta. En Express, las rutas son definidas mediante funciones que se ejecutan cuando se accede a ellas a través de ciertos métodos HTTP.

Tipos de Rutas:
- **GET:** Para obtener datos.
- **POST:** Para enviar datos y crear nuevos recursos.
- **PUT:** Para actualizar recursos existentes.
- **DELETE:** Para eliminar recursos.

### Ejemplo básico de rutas
Supongamos que queremos manejar Item en nuestra API. Podemos definir el id y el nombre.

{% highlight javascript %}
let items = [
  { id: 1, name: 'Item 1' },
  { id: 2, name: 'Item 2' }
];

// Obtener todos los ítems
app.get('/items', (req, res) => {
  res.json(items);
});

// Obtener un ítem específico por ID
app.get('/items/:id', (req, res) => {
  const item = items.find(i => i.id === parseInt(req.params.id));
  if (!item) return res.status(404).send('El ítem no fue encontrado.');
  res.json(item);
});

// Crear un nuevo ítem
app.post('/items', (req, res) => {
  const newItem = {
    id: items.length + 1,
    name: req.body.name
  };
  items.push(newItem);
  res.status(201).json(newItem);
});

// Actualizar un ítem existente
app.put('/items/:id', (req, res) => {
  const item = items.find(i => i.id === parseInt(req.params.id));
  if (!item) return res.status(404).send('El ítem no fue encontrado.');

  item.name = req.body.name;
  res.json(item);
});

// Eliminar un ítem
app.delete('/items/:id', (req, res) => {
  const itemIndex = items.findIndex(i => i.id === parseInt(req.params.id));
  if (itemIndex === -1) return res.status(404).send('El ítem no fue encontrado.');

  const deletedItem = items.splice(itemIndex, 1);
  res.json(deletedItem);
});

{% endhighlight %}




###  3. Controladores: Qué son y para qué se utilizan
Los controladores son funciones que manejan la lógica detrás de cada ruta. Sirven para organizar el código y separar la lógica de la ruta propiamente dicha, haciendo que tu código sea más modular y fácil de mantener.

### Por qué usar controladores:
- **Modularidad:** Los controladores permiten mover la lógica de negocio fuera de las rutas, manteniendo las rutas limpias y centradas en la configuración de las URLs.
- **Reutilización:** Si necesitas usar la misma lógica en varias rutas, puedes reutilizar el controlador sin repetir código.

### Ejemplo de un controlador
En lugar de tener la lógica directamente dentro de las rutas, podemos moverla a funciones en un archivo separado. Crea una carpeta controllers y un archivo userController.js:

  

