## Docker-Trabajando-con-volumenes

### 1 Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Para descargar la imagen httpd debemos usar el siguiente comando.

> docker pull httpd

Si queremos comprobar que se ha instalado de manera correcta debemos usar el comando

> docker images

### 2 Crea un contenedor con el nombre asir_httpd

Para crear el contenedor debemos usar el siguiente comando.

> docker run -d --name asir_httpd -p 8080:80 httpd