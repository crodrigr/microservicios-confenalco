# Crud de Producto

## 1. Diseño paquetes proyecto producto

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/2f8079f1-a291-4d31-b36f-b14b47bce0dd)


## 2. Proyecto su paquetes

El proyecto de productos debe tener tres paquetes donde se van agrupar nuestras clases en java

- controller: todas las clases de tipo controlador, las que tiene las anotación **@RestController**
- services: todas las clases de servicio, es como la capa de dominio, las funcionalidad de nuestro api.
- repositories: todo lo relacionado con la capa de persistencias nuestras clases repository y entity.

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/8d0f7a42-debb-41c3-b46a-0efdfa6aa217)

## 3. Clase entity de producto

Esta clase tiene la anotación Entity, la cual, marca la clase de tipo entidad que se va ha mapear con base de datos. Estas son algunas anotaciones:

- @Entity: define la clase de tipo entitie
- @Table: configuración que debe tomar la clase entity en relación a la tabla de base datos
- @Id: definie el atributo que va hacer la llave primaria en la tabla de la base de datos


[Documentación - Definición JPA Entity](https://www.baeldung.com/jpa-entities)


En esta clase Producto se define los siguientes atributos. Son private por que se aplica **encapsulamiento**

- private Long id
- private String nombre
- private String codigo
- private String descripcion

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/bc569369-b836-44d2-b4cd-6c7c62b094fb)
