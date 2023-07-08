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

# 7. ItemController.java

Se crea el controlador de Item con los dos servicios: listar y detalle

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/b8a569fd-86b4-44d9-adaa-ff780f7fc190)

# 8. Configuración de propiedades del proyecto

Todo microservicio debe tener su nombre que lo identifique. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/7b58c11e-1f90-4f57-a425-e6e95914917d)


# 9. Implementación con feing

## 9.1 Agregar la depedencia de openFeing al proyecto

Se debe seleccionar a través del add startes la dependencia **openFeing** la cual agrega dos dependencias en el **pom.xml**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/a111784e-12d7-4f4a-9c6b-10c037baf16f)

## 9.2 Depedencias en pom.xml

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/10149177-6148-4892-8179-1601ff6178d5)

## 9.3 EnableFeing en el aplicaction

Se debe activar en el proyecto el feing para que se pueda utilizar. Esto se hace en la clase principal de proyecto la **Application**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/33302543-365b-425f-8cd6-d5ae34949ca1)

## 9.4 Se crea la interfaz de feing

Dentro el proyecto se crea un directorio **clientes**, en dicho directorio van a ir todas la interfazces de feing que van a consumir servicios de otros componentes. En este caso se define para el proyecto **servicio-productos** y tenemos los dos llamados a los endpoints de productos: 

- **/listar**
- **/ver/{id}**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/4d964d24-6859-4abf-a6cc-50df5f968021)

## 9.5 Definición de implementacion de feing

En esta clase se hace la implementación de feing, implementa la interfaz **ItemService**. Ahora el **ItemController** tiene dos implementaciones de la interfaz **ItemService**, y cual debería usar. Para esto se usa el **@Primary** que indica que ser var usar **ItemServiceFeing** por defecto. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/557d08e3-55e4-47db-a07b-896b47ca8dd8)


# 10. Balanceo de carga con ribbon

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/12a4359d-67cb-4ee4-a3fd-f840c3545ddb)




## 10.1 Ajustar las dependencias

Rebbion funciona hasta la version 2.3.12

## 10.2 Ajustar version spring y java
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/5b12f4e2-7868-4de0-a423-f99b5a360c37)

## 10.3 agregar la dependencia ribbon
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/e6766955-84a2-445e-999b-e9735017db32)

## 10.4 Configuración de application.properties

Se agrega la configuración para items pueda enviar a las instancias de productos. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/a4ce0825-f034-4328-a8e4-a6a4979e92cb)

## 10.5 ItemApplication se activa ribbon

En este caso es un solo serivicio que desde Item consume, en este caso, productos. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/9ed5793c-f415-4c2c-9cdf-7e17b05aea49)

## 11.6 Iniciamos dos instancias servicio-productos

Nuestro proyecto esta configurado en el **aplication.properties** para que el puerto por defecto sea el **8001**. Como se hace para iniciar otra instancia del proyecto servicio-productos con el puerto **9001** que es el otro puerto configurado para usar ribbon. Para esto lo hacemos ejecutando el **.jar** del proyecto y pasando como variable **-Dserver.port=9001** de esta forma el va iniciar con este puerto. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/1f01a6bc-fff3-42f9-8420-c41f67d408ff)

**Iniciando con el puerto 9001**
![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/529884d1-9acb-4099-b992-d63c14ce2bfa)

## 10.7 Verificar el balanceo por el puerto que resonde

Se debe agregar un atributo en producto puerto de tipo **@Transient** para no guardar en la base de datos. En ***servicio-producto Producto.java**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/06f53e7f-7a37-4413-ae6b-02150bf5d734)

### 10.7.1 Se ajusta el ProductoController.java

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/60a51f0b-92d6-4ac4-8943-89c7535a3bcf)

### 10.7.2 Se agrega atributo por en servcio-items en Producto.java

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/58b4a1b2-2947-44bb-a2b2-5e4491ac6e83)

### 10.7.3 En serivico-items en ProductoClienteRest.java

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/895579f3-d46f-4620-acfe-6d10a9c42449)

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/da4d3f71-350b-4f41-9495-22ea55538e2f)

### 10.7.4 Se prueba en postam

Se inicia dos instancias de servici-productos con los puertos: 8001 y 9001 y se sube una instancia de servicio-items. Se aplica el balanceo con ribbon. }

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/632f93f3-7de8-48a6-b18d-250544f393bf)

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/4f737a33-350e-47c1-8e6e-ab542d1d9606)



