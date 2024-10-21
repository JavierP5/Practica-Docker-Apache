# Practica-Docker-Apache

#Descargar la imagen 
sudo docker pull httpd:2.4

#Verificar qie la imagen se ha descargado
sudo docker images | grep httpd

#Crear el contenedor dam_web1
sudo docker run -d --name dam_web1 httpd:2.4

#Ejecutar el contenedor con el puerto mapeado
sudo docker run -d --name dam_web1 -p 8000:80 httpd:2.4

#Crear un directorio en la máquina local
mkdir ~/apache_html

#Montar el directorio con bind mount
sudo docker run -d --name dam_web1 -p 8000:80 -v ~/apache_html:/usr/local/apach>

#Crear un archivo Hola Mundo en HTML
echo "<html><body><h1>Hola Mundo</h1></body></html>" > ~/apache_html/index.html

#Comprobar acceso en el navegador

#Abre tu navegador y ve a http://localhost:8000

#Crear el contenedor dam_web2 en el puerto 9080
sudo docker run -d --name dam_web2 -p 9080:80 -v ~/apache_html:/usr/local/apach>

#Modificar el archivo Hola Mundo
echo "<html><body><h1>Hola Mundo Modificado</h1></body></html>" > ~/apache_html>
