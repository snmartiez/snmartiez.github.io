---
layout: post
title: "Crear una API REST"
date: 2024-10-21
---

## Guía para crear una API REST utilizando Express

### Introducción

**Express** es un framework minimalista para **Node.js** que facilita la creación de aplicaciones web y APIs REST. 
En esta guía, aprenderás cómo crear una API REST desde cero utilizando Express, con una estructura de carpetas organizada para proyectos de mayor escala.

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
Crea un archivo llamado index.js en la raíz del proyecto. Aquí es donde configuraremos el servidor.

{% highlight javascript %}
// server.js
const express = require('express');
const app = express();
const PORT = 3000;

// Middleware para parsear JSON
app.use(express.json());

// Ruta principal
app.get('/', (req, res) => {
  res.send('¡Hola, mundo!');
});

// Iniciar el servidor
app.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});

{% endhighlight %}

### Explicación:
- express(): Crea una nueva aplicación Express.
- app.use(express.json()): Middleware que permite manejar solicitudes con cuerpos en formato JSON.
- app.get(): Define una ruta de tipo GET (más sobre tipos de rutas a continuación).
- app.listen(): Inicia el servidor y escucha en el puerto especificado.
  
Para iniciar el servidor, ejecuta:
