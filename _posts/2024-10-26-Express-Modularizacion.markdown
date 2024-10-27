---
layout: post
title: "Express - Modularización"
date: 2024-10-22
---

<hr>
Modularizar es un enfoque en el desarrollo de software que consiste en dividir una aplicación o sistema en partes más pequeñas, llamadas módulos. Cada módulo es una sección de código que realiza una función específica y autónoma dentro de la aplicación y puede ser reutilizado en diferentes contextos. La modularización facilita el mantenimiento, la comprensión y la escalabilidad de la aplicación al separar sus responsabilidades.

### En qué consiste la modularización
**La modularización implica:**

- Separación de responsabilidades: cada módulo tiene una única función o responsabilidad, lo que evita que el código esté sobrecargado de tareas no relacionadas.
- Reutilización de código: al crear módulos independientes, estos pueden ser reutilizados en distintas partes de la aplicación o incluso en otros proyectos.
- Facilidad de mantenimiento y pruebas: al estar separado, cada módulo se puede mantener, probar y depurar de manera independiente, lo que acelera la identificación y corrección de errores.
- Escalabilidad: al añadir nuevas funciones o características, la modularización permite agregar módulos sin afectar otras partes de la aplicación.
  
**Ejemplo práctico**

En una aplicación web, podríamos modularizar la funcionalidad en tres componentes principales:

- **Controladores:** manejan la lógica de negocio.
- **Rutas:** definen los endpoints de la API y redirigen a los controladores.
- **Modelos:** representan la estructura de los datos y gestionan la comunicación con la base de datos.
Cada uno de estos componentes funciona de manera independiente y se integra con los otros, permitiendo modificar o extender funcionalidades sin afectar a toda la aplicación.

### Video de ejemplo - modularización
<iframe width="560" height="315" src="https://www.youtube.com/embed/UE7unfDdi_g?si=8mbZ34zq6rdYtZEZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


