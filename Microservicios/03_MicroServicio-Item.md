# Microservicios  producto y item


# 1. Microservicio Producto e item

En este escenario se van a tener dos microservicios: producto y item. Items consume los servicios de productos a través de RestTemplate o Feing. Los cual se puede tener dos configuración. 

El balanceo se puede hacer por medio de Ribbon. No es necesario de instalar ninguna dependencia. Se va configura dos instancias de producto para que desde item consuma a traves del algoritmo de balanceo que sea la mejor opción para consumir el microservicio de producto disponible. En la siguiente sección sepuede hacer balanceo por Eureka. La configuración de rabbion se hace en item en applicaciont.propertis para indicar el host.port de las instancias que se van ha tener. Con esta opción no es nada dinamica, siempre se debe iniciar los micros de productos con la misma configuraión de host.port. 

![image](https://user-images.githubusercontent.com/31961588/236026238-fd8cb039-06c3-4080-b75c-e18ddc9fbdae.png)


# 2. Crear el microservicio Items

Creamos el proyecto con la siguente parametriaciones

## 2.1 spring initializra
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/21d8c983-ea77-4890-92a0-60c3b5c7fae5)

# 3. Estructura del proyecto

El proyecto va tener los siguiente paquetes principales: controller, services y models.  En este proyecto no se va ha tener clase de tipo entidad que se mape con la base de datos, la clase item no se va persistir, pero se relaciona con producto, dicha clase se persiste en el microservicio-producto. 

## 3.1 Paquetes proyecto
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/532b719e-c89a-414d-bbe4-ef7f80bdd88c)

# 4. Clase model Producto y Item

Esta clase se relaciona con item, por que un item va tener un producto, y está se persiste en el microservicio-producto, en este componente solo se define como una clase de tipo model, es decir, que solo se utiliza en memoria. 

## 4.1 Producto.java
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/ed2ff68d-be09-4c62-b804-4d83441eb9a6)

La clase item no se va persistir, sus atributos son: producto y cantidad. Este le permite calcular el total del producto

## 4.2 Item.java
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/f0a6f555-b7f2-467e-b969-b9d55c8f8ca1)

# 5. Crear un RestTemplate

Para que un microservicio comsuma los servicios de otro se puede hacer de dos formas: **1. ResTemplate** y **2.Feing**. Hacer lo con **RestTemplate** se debe crear un Bean **RestTemplate** se va hacer a través de de un método por eso se crea una clase **AppCofigure** con la anotación **@Configuration** el cual, va permitir tener métodos con la anotación **@Bean** para hacer inyección de dependencia. 


![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/a4ea8565-bb85-481c-955c-ea3bdb09b307)

# 6. Se crea los servicios

## 6.1 ItemService.java

Esta clase vamos a tener dos métodos: listar y detalle.  Listar trae la lista de listado de items y ver detalle trae un item en particular

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/33e2a0d9-2f9b-453f-878b-d589679b4216)

## 6.3 ItemServiceImpl.java

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/aa0e930a-028b-4d41-830e-4a596ae8e52f)

## 7. ItemController.java

Se crea el controlador de Item con los dos servicios: listar y detalle

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/b8a569fd-86b4-44d9-adaa-ff780f7fc190)

# 8. Configuración de propiedades del proyecto

Todo microservicio debe tener su nombre que lo identifique. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/7b58c11e-1f90-4f57-a425-e6e95914917d)
