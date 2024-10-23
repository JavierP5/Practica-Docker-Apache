# Practica-Docker-Apache

Práctica de Docker con Apache. A continuación, se detallan los pasos realizados con los comandos utilizados y una breve descripción de cada uno.

## 1. Descargar la imagen "httpd"
- **Comandos utilizados:**
    ```bash
    docker pull httpd:2.4
    docker images
    ```
- **Descripción:**
    - Se descarga la imagen "httpd" desde Docker Hub.
    - Se verifica que la imagen se haya descargado correctamente con `docker images`.

## 2. Crear un contenedor con el nombre 'dam_web1'
- **Comandos utilizados:**
    ```bash
    docker run -d --name dam_web1 -p 8000:80 httpd:2.4
    ```
- **Descripción:**
    - Se crea el contenedor 'dam_web1', que se ejecuta en segundo plano.
    - El puerto 80 del contenedor se mapea al puerto 8000 de la máquina local.

## 3. Montar un bind mount y acceder desde el navegador
- **Comandos utilizados:**
    ```bash
    mkdir -p ~/apache-web/htdocs
    docker run -d --name dam_web1 -p 8000:80 -v ~/apache-web/htdocs:/usr/local/apache2/htdocs httpd:2.4
    ```
- **Descripción:**
    - Se monta un directorio local en el contenedor para persistencia de datos.
    - Se puede acceder al servidor en `http://localhost:8000`.

## 4. Crear otro contenedor 'dam_web2' en un puerto diferente
- **Comandos utilizados:**
    ```bash
    docker run -d --name dam_web2 -p 9080:80 -v ~/apache-web/htdocs:/usr/local/apache2/htdocs httpd:2.4
    ```
- **Descripción:**
    - Se crea otro contenedor con el mismo bind mount, pero mapeando al puerto 9080.

## 5. Modificar la página y verificar los dos servidores
- **Comandos utilizados:**
    ```bash
    echo "<html><body><h1>Hola Mundo Modificado</h1></body></html>" > ~/apache-web/htdocs/index.html
    ```
- **Descripción:**
    - Se modifica el contenido del archivo HTML y se comprueba que los cambios se reflejan en ambos servidores.

## 6. Comandos adicionales utilizados para verificar el estado
- **Comandos utilizados:**
    ```bash
    docker ps
    docker logs dam_web1
    docker logs dam_web2
    ```
- **Descripción:**
    - Se verifican los contenedores en ejecución y se consultan los registros para asegurar que están funcionando correctamente.
