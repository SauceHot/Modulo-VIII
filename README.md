# Modulo-VIII
comandos modulo VIII

date
sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

sudo dnf install docker-ce docker-ce-cli containerd.io 

sudo systemctl start docker

sudo systemctl enable docker

sudo systemctl status docker

sudo mkdir -p /home/website

sudo docker  pull nginx 

sudo docker run -d -p 8888:80 -v  /home/website:/usr/share/nginx/html --name nginx_server nginx

sudo nano /home/website/index.html

<html>
<head>

        <title>mi pagina prueba </title>
</head>
<body>
        <h1>Mombre: Mario Abreu</h1>
        <h1>Matricula: 2024-2369</h1>

</body>
</html>
~       

sudo docker ps 

ifconfig 

192.168.100.128:8888

sudo docker stop bf5

date


date
Paso 1: Descargar la imagen de Portainer desde Docker Hub
Ejecuta el siguiente comando en tu terminal para descargar la imagen de Portainer:

docker pull portainer/portainer-ce

Paso 2: Crear un contenedor desde la imagen y mapear los puertos
Para crear el contenedor y mapear el puerto interno  al puerto externo  en el host, utiliza el siguiente comando:

docker run -d -p 9000:9000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce

estos parametros son para sincronizar el portainer con el docker si no lo haces no te aparecera la maquina al entrar al portainer

Este comando crea y ejecuta el contenedor en segundo plano () mientras mapea el puerto .

Paso 3: Acceder a la interfaz de administración de Portainer
Abre tu navegador web y visita la siguiente dirección para acceder a la interfaz de administración de Portainer:

http://127.0.0.1:9000

date

date 
sudo dnf install docker-compose-plugin -y

sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose 

sudo chmod +x /usr/local/bin/docker-compose

sudo nano docker-compose.yml

version: '3.0'

services:
  db:
    image: mysql:5.7 # Imagen de MySQL para la base de datos
    container_name: mysql_db # Nombre del Contenedor de MySQL
    environment:
      MYSQL_ROOT_PASSWORD: 130227 # Contraseña para el usuario root de MySQL
      MYSQL_DATABASE: wordpress # Nombre de la base de datos de WordPress
      MYSQL_USER: psc # Usuario de la base de datos de WordPress
      MYSQL_PASSWORD: 130227 # Contraseña del usuario de WordPress
    volumes:
      - db_data:/var/lib/mysql # Volumen para persistir datos

  wordpress:
    image: wordpress:latest # Imagen de WordPress
    container_name: wordpress_app # Nombre del contenedor de WordPress
    environment:
      WORDPRESS_DB_HOST: mysql_db:3306 # Dirección del servicio de base de datos (host:puerto)
      WORDPRESS_DB_NAME: wordpress # Nombre de la base de datos
      WORDPRESS_DB_USER: psc # Usuario de la base de datos
      WORDPRESS_DB_PASSWORD: 130227 # Contraseña del usuario de la base de datos
    ports:
      - "8080:80" # Mapea el puerto 80 del contenedor al puerto 8080 del host
    depends_on:
      - db # Asegura que MySQL esté listo antes de iniciar WordPress

volumes:
  db_data:
    # Volumen para la base de datos MySQL

networks:
  wordpress_network: # Red personalizada para que los contenedores se comuniquen


guarda el archivo y luego ingresa

sudo docker compose up -d 

configura el wordpress y listo









