---
layout: post
title: "Conceptos básicos - Desarrollar una Web API RESTFull"
date: 2024-10-19
categories: [Express, Node.js, Desarrollo Web]
---

## Conceptos básicos - Desarrollar una Web API RESTFull

### Node.js
Node.js es un entorno de ejecución de JavaScript que se ejecuta en el lado del servidor. Está basado en el motor V8 de Chrome, lo que le permite ejecutar código JavaScript fuera del navegador. Su principal ventaja es su arquitectura no bloqueante y orientada a eventos, lo que lo hace eficiente para manejar aplicaciones escalables y de alto rendimiento, como servidores web.

### Express
Express es un framework web minimalista para Node.js que facilita la creación de aplicaciones web y APIs. Express simplifica la gestión de rutas, la manipulación de solicitudes HTTP, y la gestión de middlewares, permitiendo a los desarrolladores crear servidores con menos código y más eficiencia.

### Nodemon
Nodemon es una herramienta que ayuda a los desarrolladores a mejorar su flujo de trabajo mientras están desarrollando aplicaciones con Node.js. Nodemon monitorea los archivos del proyecto y automáticamente reinicia el servidor cada vez que detecta cambios en el código, ahorrando tiempo al no tener que reiniciar manualmente la aplicación en cada cambio.

### Sequelize
Sequelize es un ORM (Object-Relational Mapping) para Node.js que facilita la interacción con bases de datos relacionales como MySQL, PostgreSQL, SQLite y MSSQL. Sequelize permite a los desarrolladores interactuar con la base de datos utilizando objetos JavaScript en lugar de escribir consultas SQL directamente, lo que simplifica la gestión de las bases de datos en las aplicaciones Node.js.

### API (Application Programming Interface)
Una API es un conjunto de definiciones y protocolos que permiten que diferentes sistemas de software se comuniquen entre sí. Las APIs exponen funcionalidades o datos de una aplicación para que otras aplicaciones puedan interactuar con ellas sin necesidad de conocer los detalles internos del sistema. Una API actúa como un puente que permite la integración entre diferentes aplicaciones o servicios.

### REST (Representational State Transfer)
Es un estilo arquitectónico para diseñar APIs que aprovecha los métodos del protocolo HTTP para realizar operaciones CRUD (Crear, Leer, Actualizar, Borrar) sobre recursos. En REST, los recursos son identificados mediante URL, y las operaciones se realizan usando los métodos HTTP como GET, POST, PUT, DELETE, etc. Una API basada en REST es conocida como una API RESTful, y su objetivo es ser ligera, escalable y fácil de mantener.

### Web API
Es un tipo específico de API que se expone a través de la web utilizando el protocolo HTTP. Las Web APIs pueden estar diseñadas siguiendo el estilo REST o SOAP (otro protocolo para servicios web), pero en general, cuando hablamos de una Web API, nos referimos a una API que permite la interacción a través de solicitudes HTTP. Las Web APIs son muy comunes en aplicaciones modernas, ya que permiten que aplicaciones web y móviles se conecten a servidores para obtener o enviar datos.
