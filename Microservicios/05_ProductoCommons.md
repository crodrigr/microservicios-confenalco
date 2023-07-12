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

## 4. Generar .jar

Con el comando **mvn install** se genera el jar del proyecto. El cual, se guarda en el repositorio **.2m** local, esto va permitir que se pueda importar como de pendencia en otros proyectos. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/fecdf5d6-23f6-4868-86c2-5eb860c1db07)

## 5. Se quita H2 Database

Se quita la dependencia **H2 Database** no es necesaria. Se genera nuevamen el .jar con **mvn install**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/e176b52f-2406-43f1-837c-b85247e818ae)

### 5.1 Se exclude el DataSourceAutoConfiguration

El proyecto se excluye la configuración de la base de datos. Si no se hace, entoces nos pide un driver de conexión a la base datos como H2 o Mysql. Se genear nuevamente el .jar

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/cfd5099f-f49e-4657-a1b0-954de4606ee6)

## 6. Import producto-commons en servicios-producto y servicios-item

### 6.1 Copiar groupId, artifactId y version de producto-commons

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/988194fc-6be9-46e4-ad53-c933814d9bc2)

### 6.2 Colocar la dependencia en servicios-producto

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/6cabc71b-17cf-4277-9d4d-a75be2c8aec2)

### 6.3 Ajustar las referencias import de producto

Se debe cambiar el import del #1 al #2 para que apunte al producto del commons y no al de repositories. Elimine la clase **Reposotories -> Producto** y  genera error por que no encuentra el **com.demo.confenalco.demo.repositories.entities.Producto**, debe colocar **com.comfenalco.microservicios.commons.producto.models.entities.Producto** que corresponde a producto commons, todas las clases que use **Producto**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/c262b24b-e1b2-4ad7-ba77-fb6e82787f5e)

### 6.4 En la clase applicacion colocar EntityScan

Como el proyecto servicio-producto la estructura de paquetes es diferente al commons y esta por fuera de la estructura base, entonces no va encontrar el paquete, por eso se usa la anotación @EntityScan con el path de paquetes donde están la clase **Producto.java** en **producto-commons**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/9fe0338e-b309-4c37-bfee-3fabff5d2ee4)
