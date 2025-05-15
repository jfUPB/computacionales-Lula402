### Qué hace el programa?
Este programa se encarga de que al presionar una tecla, la pantalla se pinte de negro y cuando se suelte la tecla se limpie y vuelva a estar en blanco.

### Cómo funciona este programa?
-> Lee la posición de la pantalla y las entradas del teclado. 

-> Si lo que entra por el teclado es diferente de 0, osea que sí se esta presionando una tecla, la pantalla empieza a pintarse desde arriba a la izquierda. 

-> Cada ronda del Loop, se compara la posición del último pixel pintado con la posición del teclado, Si esta resta da mayor o igual a 0 es porque la pantalla ya esta completamente pintada. Esto es porque la pantalla termina cuando empieza el teclado, entonces si 24576 (pantalla)-24576(teclado)=0(se terminó de pintar). Cuando se termina de pintar salta a una linea donde M[16], direccipon donde se guarda lo de la pantalla, y ahí M=0 para limpiar la pantalla.

-> Si el teclado se está presionando y luego se suelta, pero la pantalla no ha terminado de pintarse, entonces el código se asegura que lo que entre sea diferente de 0, si es igual a 0, entonces salta a la línea del código donde se limpia la pantalla. Esto se hace cuando: 
``` asm
@16         ;Es la dirección de memoria donde se empieza a guardar la posición de la pantalla.      
AM=M-1      ;Se guarda en A y en M la siguiente posición a borrar
M=0         ;Acá se limpia esa posición que se guardó en el A de la línea anterior
```
