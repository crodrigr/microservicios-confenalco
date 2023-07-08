# Eurka 

Spring **Eureka** es un componente del framework Spring Cloud que proporciona capacidades de descubrimiento de servicios y balanceo de carga para aplicaciones basadas en microservicios. Permite a los microservicios registrarse automáticamente y descubrirse entre sí en un entorno distribuido.

Las características principales de Spring Eureka son:

  1. **Servidor de registro:** Spring Eureka proporciona un servidor de registro centralizado donde los microservicios pueden registrarse. Este servidor de registro se encarga de mantener un registro actualizado de los servicios disponibles y su información relevante, como la dirección IP y el puerto.

  2. **Cliente de descubrimiento:** Los microservicios actúan como clientes de descubrimiento y se registran en el servidor de registro de Eureka. También pueden consultar el servidor de registro para obtener información sobre otros servicios disponibles. Esto permite que los servicios se descubran dinámicamente sin necesidad de conocer las ubicaciones exactas de otros servicios de antemano.

  3. **Balanceo de carga:** Spring Eureka ofrece balanceo de carga básico al distribuir las solicitudes de los clientes entre varias instancias de un servicio registrado. Esto se logra utilizando un algoritmo de round-robin para distribuir las solicitudes de manera equitativa.

  4. **Alta disponibilidad:** Spring Eureka admite la configuración de múltiples instancias de servidor de registro, lo que proporciona alta disponibilidad y tolerancia a fallos. Si una instancia de servidor de registro se vuelve inaccesible, los clientes pueden comunicarse con otras instancias disponibles sin interrupción del servicio.

La integración de **Spring Eureka** en una aplicación Spring Boot es bastante sencilla. Solo se necesita agregar las dependencias necesarias, configurar el servidor de registro o el cliente de descubrimiento en el archivo de configuración y anotar los servicios adecuados con las anotaciones proporcionadas por Spring Cloud.

Al utilizar Spring Eureka, se facilita la construcción de arquitecturas de microservicios escalables y flexibles. Permite la implementación dinámica de nuevos servicios, el equilibrio de carga entre las instancias y el descubrimiento automático de servicios, lo que simplifica la administración y el despliegue de aplicaciones distribuidas basadas en microservicios.

# 1 Crear el proyecto eureka

Se crea el proyecto de Eureka con las siguiente configuración

## 1.1 Configuración proyecto

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/a2176c11-503d-46d9-b7a1-aae09ff6d382)


## 1.2 Estructura del proyecto
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/c86058db-0607-4c68-87c3-ba9bd5feed36)

# 2 Depenencias

Se observa que en el pom.xml que se tiene la depenencia de eureka server

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/71aeaabb-8c58-41bd-9828-fd06bea904ac)

# 3. Configuración del application.properties

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/ff969e8a-74f1-4b6c-af05-86af471cdc52)

# 4. dependencia para jdk 11 o superior.

Si estamos usando un jdk superior a 11 se debe adicionar esta dependencia

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/3ab39e1d-b6dd-4eb0-9cf3-5f6e2325a777)

