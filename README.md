# Despliegue de WordPress con Docker Compose

Este proyecto utiliza Docker Compose para desplegar una instancia de WordPress con MySQL y phpMyAdmin.

## Estructura

El archivo `docker-compose.yml` define los siguientes servicios:

* **mysql:** Una instancia de MySQL para la base de datos de WordPress.
* **wordpress:** La aplicación WordPress en sí.
* **phpmyadmin:** Una interfaz web para administrar la base de datos MySQL.

## Requisitos

* Docker
* Docker Compose

## Instalación

1.  Clona este repositorio:

    ```bash
    git clone [https://github.com/cran/DELTD](https://github.com/cran/DELTD)
    cd [nombre del repositorio]
    ```

2.  Ejecuta Docker Compose para levantar los servicios:

    ```bash
    docker-compose up -d
    ```

## Configuración

* **MySQL:**
    * La contraseña de root de MySQL es `root`.
    * La base de datos se llama `bitnami_wordpress`.
    * El usuario de la base de datos es `bn_wordpress` y la contraseña es `bitnami`.
* **WordPress:**
    * La base de datos de WordPress se conecta a `mysql`.
    * El usuario administrador de WordPress es `user` y la contraseña es `bitnami`.
    * El correo electrónico del administrador es `miguel@despliegue.com`.
* **phpMyAdmin:**
    * phpMyAdmin se conecta a `mysql`.
    * La contraseña de root de MySQL es `root`.

## Acceso

* **WordPress:** Abre tu navegador y ve a `http://localhost`.
* **phpMyAdmin:** Abre tu navegador y ve a `http://localhost:8081`.

## Redes

* **frontend-network:** Conecta WordPress y phpMyAdmin.
* **backend-network:** Conecta WordPress y MySQL.

## Volúmenes

* **wordpress_data:** Persiste los datos de WordPress.
* **mysql_data:** Persiste los datos de MySQL.

## Notas

* Este es un despliegue básico para desarrollo. En producción, considera usar contraseñas más seguras y configurar HTTPS.
* Puedes modificar las variables de entorno en el archivo `docker-compose.yml` para personalizar la configuración.
