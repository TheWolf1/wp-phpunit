# WP PLUGIN

Este es un proyecto totalmente vacio listo para poder utilizar preparado para hacer un plugin de WordPress desde cero, utilizando Docker, wp-env y con su respectiva configuración lista para hacer test de integración y unitarios.

## Requisitos

1. Docker
2. npm
3. Git (Recomendado)

### Pasos de la instalación.

1. Instalar `npm -g install @wordpress/env` de esta manera instalamos wp-env de forma global en nuestro equipo.

2. Lanzamos el comando `wp-env start` con esto automaticamente npm creará contenedores de docker donde nos proporciona servicios para poder trabajar en un entorno de wordpress.

3. Instalamos las dependencias del plugin `wp-env run tests-cli --env-cwd=wp-content/plugins/my-plugin composer update -W`

4. Lanamos los test con el comando `wp-env run tests-cli --env-cwd=wp-content/plugins/my-plugin ./vendor/bin/phpunit`


En tal caso de que nos de un fallo lanzamos el inicializador de los test con los siguientes dos pasos.

1. Ingresamos al contenedor de wp-cli y nos dirigimos a la carpeta de nuestro plugin `cd /var/www/html/wp-content/plugins/[my-plugin]`

2. Lanzamos el siguiente comando dentro del contenedor `bin/install-wp-tests.sh tests-wordpress root password [container_name] latest` con este comando se instalan todo lo necesario para que el plugin pueda ejecutar los test. Test
