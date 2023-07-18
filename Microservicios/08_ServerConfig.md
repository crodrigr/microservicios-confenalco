# Servidor de configuración

<br>
<br>

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/f55c4a7d-b14a-4158-8af8-a26bc72bbdf5)


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

En resumen, **Spring Cloud Config** es una herramienta de Spring Cloud que permite la gestión centralizada de la configuración en entornos de microservicios. Proporciona un servidor de configuración y capacidades de actualización dinámica de la configuración, lo que facilita la gestión flexible y dinámica de las configuraciones de las aplicaciones distribuidas.

**Nota**: para la implemtación de **config-server** se debe tener instalado el **git**
<br>
<br>


## 1. Configuración del proyecto

En el spring-initializr se hace la configuración del proyecto con las depedencias; **Config server**, y **DevTools**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/2ac50bef-66ec-43ce-9dcd-28e4e71149c2)

<br>
<br>
<br>


## 2. EnableConfigServer

En la clase **ConfigApplication** se de activar el config server a través de la anotación **@EnableConfigServer**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/6558e5e2-9058-45dc-b8ef-902f6f650e47)

<br>
<br>
<br>

## 3. Application.properties

Los archivos de configuración se puede guardar de forma local o remoto (cloud). En esta configuración se esta guardando de forma local en el directorio **config**. En el **application.properties** se realiza la configuración del proyecto. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/defba764-b498-4b36-b087-52800d302765)

## 4. Servicio-items.properties

Iniciamos creando un archivo de configuración para uno de los microservicios. En esta caso con **servicio-items**, en el directdorio **config** se crea **servicio-items.properties**. Se tiene dos variables configuradas: server.port y configuracion.text.

#### 4.1 servicio-items

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/00c60b2b-7f11-471c-adc7-d825f227478b)

<br>

#### 4.2 Git init

Iniciamente el directorio **config** no tiene inicializado el **git**, por lo tanto, al verificar que rama tiene este repositorio retorna error. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/74deb42f-2268-4ba3-be73-44d8a0c54ea9)

<br>

Se debe crear el repositorio en el directorio **git** con el comando **git init**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/5db96230-0a91-4179-ac69-6a457162f087)

<br>

Agregar cambios y hacer commit. Con el comando **git add .** valida todos los archivos que tiene el directorio **config** con cambios pendientes, luego de pasan al states que es un estado pendiente para ir al commit y para hacerlo se hace a través del comando **git commit -m "configuración de servicio-items"**

<br>

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/85df6b6f-1c10-4757-86ad-f426f8c7a406)

<br>

#### 4.3 Servicio-items dependencias

En el proyecto **servicio-items** se debe agregar la dependencia de **confi-client**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/f11ca135-f61a-494a-bd8c-3128df7f8d47)


<br>

#### 4.4 Application vs bootstrap

El archivo "application.properties" es el archivo de configuración principal de una aplicación Spring Boot. Contiene propiedades que se aplican a la propia aplicación y a los componentes específicos de Spring Boot. Aquí se pueden configurar propiedades como el puerto en el que la aplicación se ejecutará, la configuración de la base de datos, la configuración de la seguridad, entre otras.

El archivo **bootstrap.properties**, por otro lado, es un archivo de configuración especial que se utiliza cuando se está utilizando Spring Cloud Config junto con Spring Boot. Se utiliza para configurar el comportamiento del contexto de inicio y la configuración inicial de las aplicaciones que se conectan a un servidor de configuración centralizado.

Las principales diferencias entre "application.properties" y "bootstrap.properties" son:

   - **Orden de carga:** En una aplicación Spring Boot sin Spring Cloud Config, solo se carga el archivo "application.properties" y se utiliza para configurar la aplicación. Sin embargo, cuando se utiliza Spring Cloud Config, se carga primero el archivo "bootstrap.properties" antes del archivo "application.properties". Esto permite configurar propiedades específicas de Spring Cloud Config antes de que se inicialicen otros componentes de la aplicación.

   - **Propósito:** El archivo "application.properties" se utiliza para configurar la aplicación y sus componentes internos de Spring Boot. Por otro lado, el archivo "bootstrap.properties" se utiliza para configurar el proceso de inicio de la aplicación y, en el caso de Spring Cloud Config, para la configuración inicial de la conexión al servidor de configuración centralizado.

  - **Alcance:** El archivo "application.properties" afecta a toda la aplicación Spring Boot, mientras que el archivo "bootstrap.properties" se utiliza principalmente para configurar la inicialización del contexto y la conexión con el servidor de configuración centralizado en el caso de Spring Cloud Config.

En resumen, el archivo "application.properties" es el archivo de configuración principal de una aplicación Spring Boot y se utiliza para configurar la aplicación y sus componentes internos. El archivo "bootstrap.properties" es un archivo de configuración especial utilizado en conjunto con Spring Cloud Config, y se utiliza para configurar el proceso de inicio y la configuración inicial de la conexión al servidor de configuración centralizado

<br>

#### 4.5 Servicio-items configurar bootstrap

Se crea un archivo **bootstrap.properties** con la configuración que va tomar del **server-config**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/686bdbe2-5b68-42a4-bfc4-fb0f1ee76492)



<br>

#### 4.5 Test server-config

En **config** se tiene solo **servicio-items.properties** que sería el ambiente por defult de configuración. 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/3905a928-543a-4fc4-a42d-cc6f538f0053)

<br>

#### 4.6 Servicio-items handler

En el **ItemController** se define una variable de entorno y método hadler para obtener la configuración que está definido en el archivo **servicio-item.properties** a través del **config-server**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/e1748a2d-64f4-4177-8bbc-b91dc4c3505b)


<details><summary>Mostrar código</summary>
<p>

```java
 @Value("${configuracion.texto}")
    private String texto;

@GetMapping("/obtener-config")
	public ResponseEntity<?> obtenerConfig(@Value("${server.port}") String puerto){
		
		log.info(texto);
		
		Map<String, String> json = new HashMap<>();
		json.put("texto", texto);
		json.put("puerto", puerto);
				
		return new ResponseEntity<Map<String, String>>(json, HttpStatus.OK);
	}

  ```  
</p>
</details>

<br>

#### 4.7 Servicio-items varios ambientes

En un entorno de trabajo se puede tener vario ambientes de configuración, como test, dev, y prod, por lo tanto, para cada  uno se debe tener su propio archivo de configuración. A continuación para **servicio-items** se crearon tres ambientes:

   - servicio-items.properties: configuración por defecto
   - servicio-items-dev.properties: configuración desarrollo
   - servicio-items-prod.properties: configuración produción

Todos los cambios y los nuevos archivos en **config** se deben hacer **commit** para que el **config-server** tome los cambio.s 

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/7dd1bb2b-567b-4c42-a47d-90ee7c0434ab)

**prod**

```properties
server.port=8007
configuracion.texto=Configurando ambiente de Produccion

```
**dev**

```properties
configuracion.texto=Configurando entorno Desarrollo ...
configuracion.autor.nombre=Camilo Rodriguez
configuracion.autor.email=camilo.rodrigueaz@correo.com
```

**default**

```properties
server.port=8005
configuracion.texto=Configurando ambiente por defecto

```
<br>

#### 4.8 Servicio-items perfiles

A continuación se va configurar **servicio-items** para que pueda aplicar a varios perfiles de configuración que se tiene configurado. 

<br>

**Configuración bootstrap**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/1808adab-6f68-4a91-a287-eb8f1d88b32e)

<br>

**ItemController /obtener-config**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/1fae2078-c789-475e-9350-1ed8da180476)

<br>

**Postman**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/90582616-6663-439f-9d0d-410a1626c9af)


#### 4.9 Servicio-items refeshScope

En un escenario productivo muchas veces tener que bajar un servicio para que tome una nueva configuración puede llegar a ser my critica. Con el **RefreshScope** se puede hacer cambiar la configuración de los **properties** del  **config-server** sin necesidad de reinicar los servicios. 

Para esto se debe utilizar **Actuator** que es una dependencia de spring-boot para monitorear la salud de un microservicio. Se debe colocar al dependencia en el pom.xml. Esta dependencia ya se incluyo 





