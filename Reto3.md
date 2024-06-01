`RETO 3`: Despliegue de una Aplicación Web con Docker Compose

Descripción

Este proyecto despliega la aplicación web Teemii utilizando Docker Compose. Teemii es una plataforma para lectores de manga que permite leer y administrar una colección de manga.

Recursos Proporcionados

- Imagen de Docker del front-end (FE): `dokkaner/teemii-frontend:develop`
- Imagen de Docker del back-end (BE): `dokkaner/teemii-backend:develop`

Pasos para desplegar la aplicación:

1. Crear el archivo `docker-compose.yml`

`yaml`
`version: '3'`

`services:`
  `teemii-backend:`
    `image: dokkaner/teemii-backend:develop`
    `ports:`
     `- "3000:3000"`
    `volumes:`
      `- teemii-backend-data:/data`
    `networks:`
      `- teemii-network`

  `teemii-frontend:`
    `image: dokkaner/teemii-frontend:develop`
    `ports:`
      `- "8080:80"`
    `networks:`
      `- teemii-network`

`volumes:`
  `teemii-backend-data:`

`networks:`
  `teemii-network:`

2.   Iniciar los contenedores con Docker Compose cdm:

`docker-compose up -d`

3. Verificar que los contenedores están corriendo:

   `docker ps`

4. Acceder a la aplicación:

`Visita http://localhost:8080 en tu navegador web.`

5. Verificar la persistencia de datos

  1. Añadir algunos mangas a tu colección (por ejemplo, "One Piece").

  2. Detén y elimina el contenedor del backend:

En el cmd:

`docker-compose stop teemii-backend`
`docker-compose rm teemii-backend`

  3.Vuelve a crear el contenedor del backend:

En el cmd:

`docker-compose up -d teemii-backend`


Dato a recordar

Asegúrate de tener Docker y Docker Compose instalados en tu sistema.

Si encuentras algún problema, verifica los logs de los contenedores utilizando `docker-compose logs.`

