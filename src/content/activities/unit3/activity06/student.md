### <p align=center> EXPERIMENTO 5 </p>
#### ¿Qué ocurre? 
En el main, cuando el ciclo for llama ambas funciones sucede lo siguiente.
1. La función con estática, suma +1 en cada iteración.
2. La función sin estática, no suma +1 en cada iteración. 

#### ¿Por qué?
1. Porqué? porque es como una variable global solo que solo se puede acceder a ella por medio de la función, el main si está accediendo correctamente a ella porque está llamando la función. Esta variable está almacenada en la memoria global, entonces solo se inicializa 1 vez y por eso es capaz de seguir sumando a apartir de eso.
2. Porque? porque es una variable local, no global, entonces cuando el main llama esta función que contiene la contiene, esta no cambia. Esta variable cobra vida en el stack, y al salir de la función se destruye, entonces se inicializa en = 100 cada vez que se llame a la función.
   
### <p align=center> EXPERIMENTO 6 </p>
#### ¿Qué ocurre? 
El programa corre pero, se genera la siguiente excepción: "Se produjo una excepción no controlada: infracción de acceso de lectura." cuando intento mostrar la dirección [0] del Array.

#### ¿Por qué?
Se refiere a infracción del acceso a lectura porque basicamente estoy intentando mostrar por consola memoria que ya fue liberada. 

```int* arrayHeap = new int[tam];``` Cuando hago esto estoy guardando en el Heap el Array

```delete[] arrayHeap;``` Cuando hago esto liberando el especio de memoria en el que tenía guardado el Array
