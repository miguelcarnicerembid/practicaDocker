# Práctica Docker: WordPress con MySQL y phpMyAdmin

Este repositorio contiene un ejemplo de configuración de Docker Compose para desplegar una aplicación WordPress junto con una base de datos MySQL y phpMyAdmin para la administración de la base de datos.

## Estructura del Proyecto

El proyecto se define en el archivo `docker-compose.yml` y consta de los siguientes servicios:

* **MySQL:**
    * Imagen: `mysql:latest`
    * Contenedor: `mysql`
    * Puerto: `3306:3306`
    * Volumen: `mysql_data:/var/lib/mysql`
    * Red: `backend-network`
    * Variables de entorno:
        * `MYSQL_ROOT_PASSWORD`: `root`
        * `MYSQL_DATABASE`: `bitnami_wordpress`
        * `MYSQL_USER`: `bn_wordpress`
        * `MYSQL_PASSWORD`: `bitnami`

* **WordPress:**
    * Imagen: `bitnami/wordpress:6.7.2-debian-12-r7`
    * Contenedor: `wordpress`
    * Puerto: `80:80`
    * Volumen: `wordpress_data:/bitnami`
    * Red: `frontend-network`
    * Dependencia: `mysql`
    * Variables de entorno:
        * `WORDPRESS_DATABASE_HOST`: `mysql`
        * `WORDPRESS_DATABASE_USER`: `bn_wordpress`
        * `WORDPRESS_DATABASE_PASSWORD`: `bitnami`
        * `WORDPRESS_DATABASE_NAME`: `bitnami_wordpress`
        * `WORDPRESS_BLOG_NAME`: `User's blog`
        * `WORDPRESS_USERNAME`: `user`
        * `WORDPRESS_PASSWORD`: `bitnami`
        * `WORDPRESS_EMAIL`: `miguel@despliegue.com`

* **phpMyAdmin:**
    * Imagen: `phpmyadmin/phpmyadmin`
    * Contenedor: `phpmyadmin`
    * Puerto: `8081:80`
    * Redes: `frontend-network`, `backend-network`
    * Dependencia: `mysql`
    * Variables de entorno:
        * `PMA_HOST`: `mysql`
        * `MYSQL_ROOT_PASSWORD`: `root`

## Requisitos

* Docker y Docker Compose instalados.

## Cómo ejecutar

1.  Clona este repositorio:
    ```bash
    git clone [https://github.com/miguelcarnicerembid/practicaDocker.git](https://www.google.com/search?q=https://github.com/miguelcarnicerembid/practicaDocker.git)
    ```
2.  Navega al directorio del proyecto:
    ```bash
    cd practicaDocker
    ```
3.  Ejecuta Docker Compose:
    ```bash
    docker-compose up -d
    ```

## Acceso a la aplicación

* WordPress: [http://localhost](http://localhost)
* phpMyAdmin: [http://localhost:8081](http://localhost:8081)

## Configuración adicional

* Puedes modificar las variables de entorno en el archivo `docker-compose.yml` para personalizar la configuración de los servicios.
* Los datos de WordPress y MySQL se almacenan en volúmenes persistentes, lo que significa que no se perderán al detener o eliminar los contenedores.

## Contribución

¡Las contribuciones son bienvenidas! Si encuentras algún problema o tienes alguna sugerencia, no dudes en abrir un issue o enviar un pull request.
