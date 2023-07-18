# Servidor de configuraión

<br>
<br>

Spring Cloud Config es una herramienta de Spring Cloud que proporciona un servicio de configuración centralizada para aplicaciones distribuidas basadas en microservicios. Permite gestionar de manera centralizada la configuración de múltiples servicios en entornos de nube y facilita la actualización y distribución de la configuración sin necesidad de reiniciar las aplicaciones.

Spring Cloud Config se basa en el principio de que la configuración de una aplicación debe estar separada de su código fuente. En lugar de incluir la configuración directamente en el código de la aplicación, se almacena en un repositorio centralizado, como Git, SVN o un sistema de archivos.

Algunas características y conceptos clave de Spring Cloud Config son:

   1. **Servidor de configuración:** Es un componente de Spring Cloud Config que actúa como un repositorio central para la configuración. Los servicios de la aplicación se conectan al servidor de configuración para obtener su configuración en tiempo de ejecución.

   2. **Repositorio de configuración:** Es el lugar donde se almacena la configuración de las aplicaciones. Puede ser un repositorio Git, un sistema de archivos o cualquier otro origen de configuración compatible.

   3. **Propiedades configurables:** Spring Cloud Config permite configurar propiedades específicas para cada servicio. Estas propiedades se definen en archivos de configuración específicos para cada entorno, como "application.properties" o "application.yml".

   4. **Actualización dinámica de la configuración:** Spring Cloud Config proporciona capacidades para actualizar la configuración en tiempo de ejecución sin necesidad de reiniciar los servicios. Esto permite una gestión flexible y dinámica de la configuración en entornos distribuidos.

   5. **Encriptación y seguridad:** Spring Cloud Config ofrece soporte para encriptar valores sensibles en la configuración y asegurar la comunicación entre el servidor de configuración y los servicios de la aplicación.

   6. **Integración con otros componentes de Spring Cloud:** Spring Cloud Config se integra con otros componentes de Spring Cloud, como el descubrimiento de servicios (Eureka), el enrutamiento (Zuul) y el equilibrio de carga (Ribbon), para proporcionar una solución completa para el desarrollo de microservicios.

En resumen, Spring Cloud Config es una herramienta de Spring Cloud que permite la gestión centralizada de la configuración en entornos de microservicios. Proporciona un servidor de configuración y capacidades de actualización dinámica de la configuración, lo que facilita la gestión flexible y dinámica de las configuraciones de las aplicaciones distribuidas.
