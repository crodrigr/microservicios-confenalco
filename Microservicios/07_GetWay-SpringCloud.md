# Spring Cloud Getway

<br>

Spring Cloud **Gateway** y **Zuul** son dos gateways/API gateways utilizados en el ecosistema de Spring Cloud para enrutar y filtrar solicitudes en arquitecturas de microservicios. A continuación, se presenta una comparación entre ambos:

**Spring Cloud Gateway:**

  - Spring Cloud Gateway es el gateway/API gateway desarrollado específicamente para Spring Cloud.
  - Está construido sobre Spring WebFlux y el modelo de programación reactivo.
  - Utiliza una arquitectura funcional y reactiva, lo que permite un alto rendimiento y escalabilidad.
  - Proporciona una configuración basada en rutas y un enfoque orientado a predicados y filtros.
  - Ofrece una mayor flexibilidad y extensibilidad gracias a su enfoque funcional y la posibilidad de escribir lógica personalizada utilizando funciones lambda y el operador Reactor.

**Zuul:**

  - Zuul es un gateway/API gateway desarrollado originalmente por Netflix y ampliamente adoptado en el ecosistema de Spring Cloud.
  - Se basa en el modelo de programación Servlet.
  - Utiliza una arquitectura más tradicional basada en filtros.
  - Proporciona una configuración basada en rutas y un enfoque orientado a filtros predefinidos y personalizados.
  - Tiene un ecosistema más maduro y una amplia comunidad de usuarios, con características y extensiones adicionales disponibles.
  
  Algunas diferencias clave entre Spring Cloud Gateway y Zuul son:

  - **Modelo de programación:** Spring Cloud Gateway utiliza un modelo de programación funcional y reactivo, mientras que Zuul utiliza un modelo basado en Servlet.
  - **Rendimiento:** Debido a su enfoque reactivo y al uso de Spring WebFlux, Spring Cloud Gateway puede ofrecer un mejor rendimiento en comparación con Zuul.
  - **Flexibilidad:** Spring Cloud Gateway proporciona una mayor flexibilidad y extensibilidad gracias a su enfoque funcional y reactivo.
  - **Ecosistema:** Zuul tiene un ecosistema más maduro y ha sido ampliamente adoptado, con una mayor cantidad de características y extensiones disponibles.
    
En resumen, tanto Spring Cloud Gateway como Zuul son opciones viables para implementar gateways/API gateways en el ecosistema de Spring Cloud. Spring Cloud Gateway se destaca por su enfoque reactivo y funcional, así como su flexibilidad y escalabilidad. Por otro lado, Zuul tiene un ecosistema más establecido y ofrece una opción más madura y ampliamente adoptada. La elección entre ambos dependerá de los requisitos específicos del proyecto y las preferencias técnicas.

Que son los predicatos y filtros:

  - **Predicados:** Los predicados se utilizan para tomar decisiones de enrutamiento basadas en características específicas de la solicitud entrante, como la ruta, los encabezados, los parámetros, etc. Los predicados determinan si una ruta en particular se debe aplicar a una solicitud entrante. Algunos ejemplos de predicados son los predicados de ruta, de encabezado, de método y de parámetro de consulta.

  - **Filtros:** Los filtros se utilizan para realizar transformaciones y operaciones en las solicitudes y respuestas que pasan a través del Gateway. Los filtros pueden modificar, agregar o eliminar encabezados, modificar la solicitud o respuesta, realizar autenticación, agregar métricas, entre otras operaciones. Spring Cloud Gateway proporciona una variedad de filtros predefinidos que se pueden configurar y también permite crear filtros personalizados según tus necesidades.
