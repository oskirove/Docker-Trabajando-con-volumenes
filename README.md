## Docker-Trabajando-con-volumenes

### 1 Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Para descargar la imagen httpd debemos usar el siguiente comando.

> docker pull httpd

Si queremos comprobar que se ha instalado de manera correcta debemos usar el comando

> docker images

### 2 Crea un contenedor con el nombre asir_httpd

Para crear el contenedor debemos usar el siguiente comando.

> docker run -d --name asir_httpd -p 8080:80 httpd

### 3 Mapea el puerto 80 del contenedor con el puerto 8000 de tu máquina.

Si deseamos mapear el puerto 80 del contenedor al puerto 8000 de la máquina host en primer lugar debemos detenerlo utilizando el comando. 

> docker stop asir_httpd

Una vez ejecutamos el comando anterior procedemos a realizar el mapeo de puertos utilizando:

> docker run -d --name asir_httpd -p 8000:80 httpd

### 4 Utiliza bind mount para que el directorio del apache2 'htdocs' este montado en un directorio que tu elijas.  

**Utiliza: _-v "$PWD"/htdocs:/usr/local/apache2/htdocs/_**

> docker run -d --name asir_httpd -p 8000:80 -v "$PWD/htdocs":/usr/local/apache2/htdocs/ httpd

### 5 Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador.

Si realizamos dentro del directorio htdocs un documento **(index.html)** como el siguiente:

> <html>
>   <body>
>       <p> Hola mundo </p>
>   </body>
> </html>

Ahora si escribimos en el navegador la URL localhost:8000 podremos observar que el documento creado aparece en el navegador como una página web.
### 6 Crea un contenedor 'asir_web1' que use este mismo directorio para 'htdocs' y el puerto 8000

Para crear este contenedor realizaremos un archivo **docker-compose.yml** e incluiremos los siguientes parámetros:

>services:
>  asir_contenedor1:
>    image: httpd:2.4
>    ports:
>      -"8000:80"
>    volumes:
>      - /home/oscar/Desktop/asir2/sri/apache/paginas:/usr/local/apache2/htdocs
>    container_name: asir_web1

Una vez terminemos lo anterior usaremos el siguiente comando para ponerlo en marcha:

> docker compose up -d