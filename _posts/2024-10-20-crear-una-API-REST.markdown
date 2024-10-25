---
layout: post
title: "Express - Rutas"
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

// Incluimos el módulo de Express
const express = require('express');

// Creamos una instancia de la aplicación Express
const app = express();

// Definimos el puerto en el que el servidor escuchará (puerto 80)
const port = 80;

// Middleware para analizar las solicitudes JSON entrantes
app.use(express.json());

// Ruta raíz
app.get('/', (req, res) => {
    // Respuesta para la ruta raíz con un mensaje de bienvenida
    res.send('¡Bienvenido a mi Api Web');
});

// Iniciar el servidor y hacer que la aplicación escuche en el puerto especificado
app.listen(port, () => {
    // Imprimir en la consola que el servidor está corriendo
    console.log('Servidor escuchando en http://localhost');
});

{% endhighlight %}

### Explicación:
- express(): Crea una instancia de Express.
- app.use(express.json()): Middleware que permite que nuestra API maneje peticiones con cuerpos en formato JSON.
- app.get('/', ...): Define una ruta GET en la raíz del servidor. Al acceder a esta ruta, responderá con "¡Bienvenido a la API!".
- app.listen(PORT, ...): Inicia el servidor en el puerto 80 y espera solicitudes.
  
Para iniciar el servidor, ejecuta:
{% highlight bash %}
   node index.js
{% endhighlight %}
Visita http://localhost:80 y deberías ver el mensaje "¡Bienvenido a la API!".
<hr>


### 2. Qué es una Ruta en Express

Una ruta es una dirección URL específica que se define en nuestro servidor y está asociada con una acción o respuesta. En Express, las rutas son definidas mediante funciones que se ejecutan cuando se accede a ellas a través de ciertos métodos HTTP.

Tipos de Rutas:
- **GET:** Para obtener datos.
- **POST:** Para enviar datos y crear nuevos recursos.
- **PUT:** Para actualizar recursos existentes.
- **DELETE:** Para eliminar recursos.

### Ejemplo básico de rutas
Supongamos que queremos manejar productos en nuestra API. Podemos definir un array de objetos donde estos tendrán las siguientes propiedades:  id, categoría, nombre.

{% highlight javascript %}

// Incluimos el módulo de Express
const express = require('express');

// Creamos una instancia de la aplicación Express
const app = express();

// Middleware para analizar las solicitudes JSON entrantes
app.use(express.json());

// Array de productos para simular una base de datos
let produtos = [
    { id: 1, categoria: 'Frutas', Nombre: 'Manzana' },
    { id: 2, categoria: 'Frutas', Nombre: 'Uvas' },
    { id: 3, categoria: 'Frutas', Nombre: 'Mangos' }
];

// Ruta raíz
app.get('/', (req, res) => {
    // Respuesta para la ruta raíz con un mensaje de bienvenida
    res.send('¡Bienvenido a mi Api Web');
});

// ########### Rutas para Gestión de Productos ###########

// 1) Ruta para listar todos los productos
app.get('/productos', (req, res) => {
    // Responde con un JSON de todos los productos
    res.json(produtos);
});

// 2) Ruta para listar un producto por su ID
app.get('/producto/:id', (req, res) => {
    // Busca el producto por su ID en el array de productos
    let producto = produtos.find(i => i.id === parseInt(req.params.id));
    // Si no se encuentra el producto, responde con un 404
    if (!producto) return res.status(404).send('Producto no existe');
    // Responde con el producto encontrado en formato JSON
    res.json(producto);
});

// 3) Ruta para crear un nuevo producto
app.post('/producto', (req, res) => {
    // Crea un nuevo producto con los datos del cuerpo de la solicitud
    const newproducto = {
        id: produtos.length + 1,
        categoria: req.body.categoria,
        Nombre: req.body.Nombre
    };
    // Añade el nuevo producto al array de productos
    produtos.push(newproducto);
    // Responde con el nuevo producto creado y un estado 201 (creado)
    res.status(201).json(newproducto);
});

// 4) Ruta para editar un producto existente
app.put('/editar/:id', (req, res) => {
    // Busca el producto por su ID en el array de productos
    let producto = produtos.find(i => i.id === parseInt(req.params.id));
    // Si no se encuentra el producto, responde con un 404
    if (!producto) return res.status(404).send('Producto no existe');
    // Actualiza la categoría y nombre del producto con los datos del cuerpo de la solicitud
    producto.categoria = req.body.categoria;
    producto.Nombre = req.body.Nombre;
    // Responde con el producto actualizado en formato JSON
    res.json(producto);
});

// 5) Ruta para eliminar un producto por su ID
app.delete('/eliminar/:id', (req, res) => {
    // Encuentra el índice del producto por su ID en el array de productos
    const producIdex = produtos.findIndex(i => i.id === parseInt(req.params.id));
    // Si no se encuentra el producto, responde con un 404
    if (producIdex === -1) return res.status(404).send('El producto no existe');
    // Elimina el producto del array de productos
    const deleteProducto = produtos.splice(producIdex, 1);
    // Responde con el producto eliminado en formato JSON
    res.json(deleteProducto);
});

// Iniciar el servidor y hacer que la aplicación escuche en el puerto especificado
app.listen(80, () => {
    // Imprimir en la consola que el servidor está corriendo
    console.log('Servidor escuchando en http://localhost');
});


{% endhighlight %}


<hr>

## Videos 

<hr>
### Express - Rutas - Metodo GET
<iframe width="560" height="315" src="https://www.youtube.com/embed/Wa4CGe-OuCg?si=uZmtJwpSVQhHCxoz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<hr>
### Express - Rutas - Metodos POST, PUT
<iframe width="560" height="315" src="https://www.youtube.com/embed/Hn-Wx8c86FA?si=7rE8I93monSgtwhN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<hr>
### Express - Rutas - Metodos DELETE
<iframe width="560" height="315" src="https://www.youtube.com/embed/ASsoLOj3WcU?si=IaNtklgVveW80vdC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


  

