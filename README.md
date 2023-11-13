## 1. Explica métodos para 'abrir' una consola/shell a un contenedor que se está ejecutando.

Es posible utilizando el comando:

    docker exec -it contenedor bash

También se puede hacer hacer click derecho sobre el contenedor y dándole a "attach shell".

## 2. En el contenedor anterior con que opciones tiene que haber sido arrancado para poder interactuar con las entradas y salidas del contenedor.

Para interactuar con las entradas y salidas debe arrancarse con "-it".

## 3. ¿Cómo sería un fichero docker-compose para que dos contenedores se comuniquen entre si en una red solo de ellos?

Se debe añadir los contenedores a una red propia utilizando "networks"

## 4. ¿Qué hay que añadir al fichero anterior para que un contenedor tenga la IP fija?