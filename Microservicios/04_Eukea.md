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

# 5. Activamos el Eureka Server

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/4ae7933a-e40a-4ae4-9197-b6aabe47c0ca)

# 7. Vamos a http://localhost:8761

Esta arriba el servidor de eureka. Ahora configurar los clientes de eureka.

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/56c4d1e7-74f8-4652-8ad4-a882169d2940)

# 8. En servicio-items desactivamos ribbon

Se quita la anotación **@RibbonClient(name = "servicio-productos")**


- pom.xml:
    -  cambiar la version spring
    -  quitar la dependencia ribbon
    -  colcoar la version de spring-cloud
-  ItemApplicacion quitar rebbion
-  AppConfiguracion quitar balanceloar
-  application.properties quitar la lista de instancias de servicio-productos
-  en cliente ProductoClienteRest color la url para que no genere error. 
   

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/c30d57e9-53ce-422d-8de0-f7828f6e572f)

# 9 Configura Eureka cliente Items

En el proyecto servicio-items se agrega la dependencia de **eureka client**. Se agrega con el **Add Starte** y se adiciona en el **pom.xml**

## 9.1 Add startes
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/db57bc4e-acfe-4077-8b71-bbf159957747)

**Depedencia pom.xml**
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/64052499-c405-49dc-a44f-d5192ad042c1)

## 9.2 Configuración applicaction.properties

En el archivo de **aplicaction.properties** se configura el proyecto **servicio-items** para que se registre en el **eureka-server** como un cliente

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/c79e083e-3d79-4e86-b61f-4b8dc558cbce)

## 9.3 Se activa el Eureka Client

En el **ItemApplicaction** se coloca la anotación **@EnableEurekaClient** para activar el cliente de eureka en este proyeccto. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/8b17f2ae-0e6c-4cb5-9c8a-c1aa8ef4c314)

# 10 Configurar Eureka Client en Productos

Se configura el proyecto **servicio-productos** para que se cliente de eureka. 

### 10.1 Se Add Starte Eureka Cliente
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/fd11368a-db32-4548-9638-42acc2e94af2)

### 10.2 La dependencia de Eureka Cliente en el pom.xml
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/939d256b-96e3-4e0b-abb5-2179eaecb833)

### 10.3 Se configura el properties.application
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/5a92234d-c228-4383-afb8-4cc963d99d48)

### 10.4 Se activa eureka cliente en el proyecto**
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/4d390674-9167-4fe5-8708-a60d814af5f2)






