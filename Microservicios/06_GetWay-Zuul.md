# Zuul puerta de enlace 

Zuul es un componente del proyecto Spring Cloud que proporciona capacidades de enrutamiento y filtrado de solicitudes para construir puertas de enlace (gateways) en aplicaciones basadas en microservicios. En el contexto de Spring Boot, Zuul actúa como un enrutador y un filtro de solicitudes HTTP.

La función principal de Zuul es dirigir las solicitudes entrantes a los microservicios correspondientes en función de la ruta y otros criterios de enrutamiento definidos. Además del enrutamiento, Zuul también permite aplicar filtros a las solicitudes y respuestas HTTP. Estos filtros son componentes que se ejecutan antes o después de que se procese una solicitud, lo que permite realizar tareas como la autenticación, autorización, registro de solicitudes, transformación de solicitudes y respuestas, entre otras.

Al utilizar Zuul en una aplicación Spring Boot, puedes centralizar el enrutamiento y la lógica de filtrado en una puerta de enlace, lo que simplifica la arquitectura de tu sistema y proporciona beneficios como la seguridad, el monitoreo y la capacidad de escalar y gestionar tus microservicios de manera más eficiente.

Zuul se integra estrechamente con otros componentes de Spring Cloud, como Eureka (servidor de descubrimiento), Ribbon (balanceo de carga) y Hystrix (tolerancia a fallas), lo que permite construir sistemas distribuidos robustos y escalables utilizando Spring Boot y Spring Cloud.

En resumen, Zuul en Spring Boot es una solución para implementar puertas de enlace en aplicaciones basadas en microservicios, ofreciendo enrutamiento y filtrado de solicitudes para simplificar la comunicación entre los diferentes componentes de un sistema distribuido.


![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/44dca83f-b580-473b-b579-aa531736efd2)


## 1. Crear el proyecto servicio-zuul

A continución se tiene la configuración del proyecto de zuul

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/edf6f48a-ac94-4994-a056-d9a98ab09e47)

## 2. Ajustar versiones de depencia

Zuul solo funciona hasta la versión 2.4 de spring boot. Por lo tanto, se debe hacer un ajuste manual. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/e24b08be-4f2c-49af-b27f-c31a9f99f272)

## 3. Activar zuul

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/267734c4-8e59-4262-b6d2-10c00a37e4fe)

## 4. Configuración de application.properties

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/3ace5115-aba3-49c1-ae67-5acc95f46fac)

## 5. Consulta en postma con zuul

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/d77428ae-c20a-4f08-b7c4-c5c3ef6be87f)

<br>
<br>
<br>

## 7. Filtro zuul 

Crear filtro para calcular cuanto es el tiempo que toma zuul para atender una petición y enrutarla. Se crear la clase **PreTiempoTranscurridoFilter**

![image](https://user-images.githubusercontent.com/31961588/236098237-0a6da82d-d1ba-4178-baf9-5fa760f3cf4a.png)

Se crea la clase PostTiempoTranscurridoFilter

![image](https://user-images.githubusercontent.com/31961588/236098316-c363b2e4-160b-46f9-b7fe-d1553b6edc00.png)

<br>
<br>
<br>

## 7 Aplicar timeout en zuul 

Esto permite que no genere timeout si se demora mas tiempo en resolver el routing. 

![image](https://user-images.githubusercontent.com/31961588/236098667-f7f9a33c-445b-4d6b-bb02-c2ae7bbd1ec1.png)


