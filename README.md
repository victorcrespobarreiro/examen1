## 1. Explica métodos para 'abrir' una consola/shell a un contenedor que se está ejecutando.

Es posible utilizando el comando:

    docker exec -it contenedor bash

También se puede hacer hacer click derecho sobre el contenedor y dándole a "attach shell".

## 2. En el contenedor anterior con que opciones tiene que haber sido arrancado para poder interactuar con las entradas y salidas del contenedor.

Para interactuar con las entradas y salidas debe arrancarse con "-it".

## 3. ¿Cómo sería un fichero docker-compose para que dos contenedores se comuniquen entre si en una red solo de ellos?

Se debe añadir los contenedores a una red propia utilizando "networks"

## 4. ¿Qué hay que añadir al fichero anterior para que un contenedor tenga la IP fija?

Se debe añadir el "ipv4_address" para que el contenedor tenga la IP fija.

## 5. ¿Que comando de consola puedo usar para saber las ips de los contenedores anteriores? Filtra todo lo que puedas la salida.

Para saber las ips de los contenedores se puede utilizar el comando:

    docker network inspect bind9_subnet 

## 6. ¿Cual es la funcionalidad del apartado "ports" en docker compose?

La función de "ports" en docker compose es la de mapear los puertos del contenedor con los del equipo.

## 7. ¿Para que sirve el registro CNAME? Pon un ejemplo.

El registro CNAME permite crear el alias de un dominio.  

Ejemplo para que owncloud sea un CNAME de www: 

owncloud	IN	CNAME	www

## 8. ¿Como puedo hacer para que la configuración de un contenedor DNS no se borre si creo otro contenedor?

Con la opción de volúmenes persistentes puedes mapear nuevos directorios del host con los directorios del contenedor.

## 9. Añade una zona tiendadeelectronica.int en tu docker DNS que tenga:

Añadimos la zona:

    nano /etc/bind/zones/tiendadeelectronica.int


###    www a la IP 172.16.0.1

Al archivo le añadimos: 

    www	IN	A	172.16.0.1

###    owncloud sea un CNAME de www

Añadimos:

    owncloud	IN	CNAME	www

###    un registro de texto con el contenido "1234ASDF"

Añadimos:

     txt	IN	TXT	“1234ASDF”

###   Comprueba que todo funciona con el comando "dig"

Comprobamos con los comandos:

    dig @localhost www.tiendadeelectronica.int
    dig @localhost owncloud.tiendadeelectronica.int
    dig @localhost -t TXT tiendadeelectronica.int


###   Muestra en los logs que el servicio arranca correctamente

Para mostrar los logs de servicio podemos hacer click en "view logs" o utilizar el comando:

    docker logs dns-server
