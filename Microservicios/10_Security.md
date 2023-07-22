# Securty

### Imagen 1

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/70facb7b-c53d-4b17-84f2-0ea573080a24)

### Imagen 2

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/7866d151-e00d-41fa-b1d3-fa94d7ef1979)

### Imagen 3

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/723d9b7d-4dd3-4e8c-990f-547cf9fb73fb)


En esta configuración, estás definiendo los detalles de un cliente OAuth 2.0 para tu servidor de autorización. En particular, estás utilizando el almacenamiento en memoria para registrar el cliente y sus detalles. Veamos qué hace cada parte de la configuración:

1. `clients.inMemory()`: Estás configurando el cliente en memoria, lo que significa que los detalles del cliente se mantendrán en la memoria de la aplicación en lugar de utilizar un mecanismo de almacenamiento persistente.

2. `withClient(env.getProperty("config.security.oauth.client.id"))`: Estableces el ID del cliente OAuth 2.0. Estás obteniendo este valor de una propiedad configurada en tu entorno, lo que te permite configurar diferentes clientes para diferentes entornos o situaciones.

3. `.secret(passwordEncoder.encode(env.getProperty("config.security.oauth.client.secret")))`: Estás estableciendo el secreto del cliente. Al igual que con el ID del cliente, estás obteniendo este valor de una propiedad configurada en tu entorno. Es importante notar que el secreto debe ser codificado antes de ser almacenado en el servidor de autorización. Aquí estás utilizando un `PasswordEncoder` para codificar el secreto.

4. `.scopes("read", "write")`: Estás definiendo los alcances (scopes) a los que este cliente tiene acceso. Los alcances definen qué acciones puede realizar el cliente en nombre del usuario, por ejemplo, "read" para leer datos y "write" para escribir datos.

5. `.authorizedGrantTypes("password", "refresh_token")`: Estás especificando los tipos de concesiones de autorización que se pueden utilizar para obtener tokens de acceso. En este caso, estás permitiendo el uso de los flujos de autorización "password" (concesión de contraseña) y "refresh_token" (concesión de token de actualización).

6. `.accessTokenValiditySeconds(3600)`: Estás estableciendo la duración en segundos del token de acceso generado para este cliente. En este caso, el token de acceso tendrá una validez de 3600 segundos (1 hora).

7. `.refreshTokenValiditySeconds(3600)`: Estás estableciendo la duración en segundos del token de actualización generado para este cliente. El token de actualización se utiliza para obtener nuevos tokens de acceso cuando el token original expira. En este caso, el token de actualización tendrá una validez de 3600 segundos (1 hora).

En resumen, con esta configuración estás definiendo un cliente OAuth 2.0 que puede acceder a los alcances "read" y "write" utilizando los flujos de autorización "password" y "refresh_token". El cliente tendrá un token de acceso válido por 1 hora y un token de actualización válido por la misma duración. El ID del cliente y el secreto del cliente se obtendrán de propiedades configuradas en el entorno, lo que te permite configurar diferentes clientes para diferentes entornos sin modificar el código.
