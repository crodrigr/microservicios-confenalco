# CRUD de producto

<br>
<br>

El proyecto **servicio-productos** solo tenia dos servicios: listar y ver. En esta sección se va completar con **crear**, **modificar** y **eliminar** producto. 

<br>


## 1. Servicio-producto capa services

En la capa de services en  la interfaz **ProductoService** y en la implementación de la interfaz en **ProductoServiceImpl** se define los métodos **save** y **delete**

<br>

### 1.1 ProductoService

En la interfaz **ProductoService** se defini los métdos: save y deleteById. Para crea un producto y eliminar producto por Id

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/2e0cd5d2-c51d-40d2-8f1a-35deca6de0e2)


<br>

### 1.2 ProductoServiceImpl

Se hace la implementación de los metodos **save** y **deleteById**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/3ad99de1-e778-4702-914f-8b5f9268e668)

<br>

### 1.3 ProductoController

En el **ProductoController** se crea los **endpoint** se **crear**, **editar** y **eliminar**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/2e03d2d6-2e68-4c45-9474-be49d8610ad3)


### 1.4 Crear producto

Este un ejemplo de como se podría probar en postman la creación de un producto. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/6363ce0c-53c8-409b-935f-b5ef6f2311ac)

<br>
<br>
<br>

## 2. Servicio items 

En el **servicio-items** en la capa **servicio** y **controller** se van adecuar para que desde servicio-items se pueda crear, modificar y eliminar productos. 

<br>

### 2.1 Servicio items en service

En la interfaz **ItemService** se adiciona los métodos: save, update y delete que van a permiter crea un producto, 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/c439db49-bf56-4fbe-b3ee-53732f8c9186)

<br>

### 2.2 Servicio items en implements 

En la implementación de **ItemService** que se realiza en **ItemServicieImpl** se define los métodos: **save**, **update**, y **delete**. Recuerde que en el **ItemServiceImpl** se usa el **RestTemplate** para cosumer los servicios que están en el **servicio-producto**. En otra sección se va realizar con **feing** en **ItemServiceFeing**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/d8190777-f091-42ea-a9e4-1c4b410c4d96)


<br>

### 2.2 Servicio items en controller

En **ItemController** se crean los endpoind que se ha utilizar para los servicios para el crud de produco: **crear**, **update** y **eliminar**. 

Aspectos a tener encuenta. En el **ItemController** va usar **ItemServiceImpl** que utilizar **RestTemplate**. Por lo tanto, debe validar que el **@Qualifier("serviceRestTemplate")**. Por otra parte en el **AppConfigure** debe tener activo el **@LoadBalanced**

<br>

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/8e0386f3-127b-4115-8c69-735ab8726500)

<br>

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/ee5b11b4-a91d-4f4d-bc9f-1c10063db652)


