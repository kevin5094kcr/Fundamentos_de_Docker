# Fundamentos_de_Docker

`Teemii`

Teemii es una aplicación web optimizada diseñada para los lectores amantes del manga. Ofrece una plataforma sencilla y eficiente para leer y administrar una colección de manga.

Despliegue con Docker

`Este proyecto utiliza Docker para desplegar la aplicación completa, incluyendo el frontend y el backend.`

Requisitos

`Docker Desktop`

Pasos para desplegar la aplicación

1. Abre el Command Prompt (cmd) y creamos una red Docker para que los contenedores se comuniquen entre si con el comando:

`docker network create teemii-network`

2. Ejecutamos el contenedor del backend y asigna el volumen para la persistencia de datos.:

`docker run -d --name teemii-backend --network teemii-network -p 3000:3000 -v teemii-backend-data:/data dokkaner/teemii-backend:develop`

3. Ejecutamos el contenedor del frontend y conectamos a la misma red Docker.:

`docker run -d --name teemii-frontend --network teemii-network -p 8080:80 dokkaner/teemii-frontend:develop`

4. Verificamos que los contenedores están corriendo:

`docker ps`

5. Accedemos a la aplicación en nuestro navegador en:

`http://localhost:8080.`
