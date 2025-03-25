### <p align=center> EXPERIMENTO 1 </p>
#### ¿Qué ocurre? 
Se genera una "excepción no controlada" porque dice que cometí una Infracción de acceso al escribir en la ubicación 0x00007FF6B83212DA. Me está diciendo que esa infracción es por escribir en una ubicación de solo lectura.

#### ¿Por qué?
Porque estoy intentando modificar algo que está en la zona de memoria que es SOLO de lectura, ahí se guarda el segmento de código, las instrucciones y **funciones**, MAIN en este caso es una función.

### <p align=center> EXPERIMENTO 2 </p>
#### ¿Qué ocurre? 
Me informa una excepción: "Se produjo una excepción no controlada: infracción de acceso de escritura.
ptr fue 0x7FF61425AC10"

#### ¿Por qué?
Porque al yo decir "const char* const mensaje_ro = "Hola, memoria de solo lectura";" estoy diciendo que el contenido de la variable es constante y ADEMÁS que la dirección de esa variable que es un char, va a ser también contante. Con lo anterior el compilador dice que entonces si todo eso va a ser constante lo manda para el segmento de solo lectura, porque no lo modificaré.
Entonces aunque yo lo quiera modificar por medio de ptr, al haber dicho const char*, hice que esa dirección fuera constante osea que no cambia.

