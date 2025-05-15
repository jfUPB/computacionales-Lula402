P pinta & B borra
```asm
// Inicio una variable para guardar un puntero a la pantalla.
    @16384 
    D=A 
    @16 
    M=D 

// Guardo la tecla que leo en la posición 2 de la memoria RAM
    
(LOOP)
    @24576 
    D=M 
    @2
    M=D

  // Leo la tecla almacenada en la posición 2 de la RAM
    @2
    D=M       // D = valor almacenado en la dirección 2 (nuestro parámetro)

    @112
    D=D-A        // Resta 112 al valor en D: D = (valor en R2) - 112
    @draw
    D;JEQ       // Si el resultado en D es 0, salta a la etiqueta "pinta"

    @2
    D=M          // D = valor almacenado en la dirección 2 (nuestro parámetro)
    @98
    D=D-A        // Resta 98 al valor en D: D = (valor en R2) - 112
    @borrar
    D;JEQ       // Si el resultado en D es 0, salta a la etiqueta "borra"
    @LOOP 
    0;JMP 
    
(borrar)
    @16 
    D=M 
    @16384 
    D=D-A 
    @LOOP 
    D;JLE 

    @16 
    AM=M-1 
    M=0 
    @LOOP
    0;JMP 
    
(draw)
    @16 
    D=M 
    @24576 
    D=D-A 
    @LOOP 
    D;JGE   // Si ya recorrí toda la pantalla voy a preguntar de nuevo por un tecla nueva

    @16 
    A=M 
    M=-1 
    @16 
    M=M+1 
    @LOOP 
    0;JMP 
```
