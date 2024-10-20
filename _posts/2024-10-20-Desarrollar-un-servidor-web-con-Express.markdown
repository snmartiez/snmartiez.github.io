---
layout: post
title: "Express"
date: 2024-10-19
categories: [Express, Node.js, Desarrollo Web]
---

## Creando un servidor web básico con Express

En este tutorial, aprenderemos a crear un servidor web básico con **Express**, un popular framework de **Node.js**. Sigue estos pasos para comenzar tu propio proyecto.

### 1. Requisitos previos

Asegúrate de tener instalado lo siguiente en tu sistema:

- **Node.js** (versión 18 o superior). Puedes descargarlo desde [nodejs.org](https://nodejs.org).
- **NPM** (viene con Node.js).

Verifica si tienes ambos instalados ejecutando en la terminal:

{% highlight bash %}
node -v
npm -v
{% endhighlight %}

### 2. Crear un nuevo proyecto de Node.js

Primero, crea una carpeta para tu proyecto y navega dentro de ella:

{% highlight bash %}
mkdir mi-proyecto-express
cd mi-proyecto-express
{% endhighlight %}

Inicializa un proyecto de Node.js con el siguiente comando:

{% highlight bash %}
npm init -y
{% endhighlight %}

Esto generará un archivo `package.json` que administrará las dependencias de tu proyecto.

### 3. Instalar Express

Instala **Express** como una dependencia del proyecto:

{% highlight bash %}
npm install express
{% endhighlight %}

Esto añadirá **Express** al archivo `package.json`.

### 4. Crear un servidor con Express

Ahora, crea un archivo llamado `app.js` en la carpeta de tu proyecto y añade el siguiente código para configurar un servidor básico:

{% highlight javascript %}
const express = require('express');
const app = express();

// Definir la ruta principal
app.get('/', (req, res) => {
  res.send('¡Hola, Mundo! Este es mi primer servidor con Express.');
});

// Configurar el servidor en el puerto 3000
const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Servidor ejecutándose en http://localhost:${PORT}`);
});
{% endhighlight %}

### 5. Ejecutar el servidor

Para ejecutar tu servidor, ve a la terminal y usa el siguiente comando:

{% highlight bash %}
node app.js
{% endhighlight %}

Verás un mensaje que indica que el servidor está ejecutándose:

