# Producto commons

Entre los proyectos **servicio-productos** y **servicio-items** se tiene en común los objetos de tipo **producto**. Se hace una abstracción en un compoente **servicio-produtos-commons**, el cual, tiene la misma clase para los otros componentes.  

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/b9901c8f-521d-4664-89a6-d009a101b727)

## 1. Crear servicio-producto-commons

En spring intializr se crea el proyecto con la siguiente configuración. La entity **Producto** tiene anotaciones de **spring-jpa**, por lo tanto, se debe colocar dicha dependencia, pero para que no nos de error de base de datos, se coloca la dependencia **H2 Database**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/41d092e7-9272-4b79-9b58-709fbc2989e6)


## 2. Se elimina el método main

En la clase **ProductoApplication** se elimina el método main, por que, este proyecto es de libreria, nunca se lanza. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/67b0fce2-1c79-4840-8726-6fe847d34a28)


## 3. Se quita el plugins de maven

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/5803e520-e119-4cb8-bebb-9528dda85db2)

## 4. Se copia Producto.java de servicio-productos

Se copia la clase entity **Producto.java** del proyecto **servicios-productos** en el paquete **models -> entites**. Es importante ajustar el pequete por que ya no está en el proyecto de **sevicios-productos**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/64efac70-453e-4117-8980-8e7180fde053)

