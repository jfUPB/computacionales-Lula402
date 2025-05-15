**¿En qué direcciones de memoria se implementan las variables i, sum?**

i se implementa en la dirección de RAM 16
sum se implementa en la dirección de RAM 17

**¿Cuál es la diferencia entre la dirección de una variable y su contenido?**

La diferencua es que la dirección de una variable funciona como un puntero, es para indicar donde está almacenada la variable. El contenido de una variable es el valor que tiene asignado.
Funciona así: con la dirección de la variable voy y la busco en la RAM, cuando encuentre la variable entonces podré saber su contenido, osea el valor que esta tiene almacenado.

**Explica cómo se implementa la condición i <= 100**

En este while ensamblador la condición i <= 100 se implementa usando el salto D;JGT, que se asegura que el Loop se rompa cuando se cumpla la condición de i-100>0. 

Si i=102 entonces 102-100=2 y como 2>0, la idea es solo sumar los número hasta el 100, entonces ahí se rompe el Loop.
