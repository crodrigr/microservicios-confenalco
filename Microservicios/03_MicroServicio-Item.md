# Microservicios  producto y item


## 1. Microservicio Producto

En este escenario se van a tener dos microservicios: producto y item. Items consume los servicios de productos a través de RestTemplate o Feing. Los cual se puede tener dos configuración. 

El balanceo se puede hacer por medio de Ribbon. No es necesario de instalar ninguna dependencia. Se va configura dos instancias de producto para que desde item consuma a traves del algoritmo de balanceo que sea la mejor opción para consumir el microservicio de producto disponible. En la siguiente sección sepuede hacer balanceo por Eureka. La configuración de rabbion se hace en item en applicaciont.propertis para indicar el host.port de las instancias que se van ha tener. Con esta opción no es nada dinamica, siempre se debe iniciar los micros de productos con la misma configuraión de host.port. 

![image](https://user-images.githubusercontent.com/31961588/236026238-fd8cb039-06c3-4080-b75c-e18ddc9fbdae.png)

