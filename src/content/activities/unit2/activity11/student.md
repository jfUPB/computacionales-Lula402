### <p align="center">Conceptos</p>
**1. Punteros:** Los punteros sirven para guardar la dirección de memoria de alguna variable, es decir donde se vaya a guardar la variable, esa posición o dirección queda guardada o señalada por el puntero.
Aprendí como sacarle el mejor provecho a los punteros y lo útiles que son para recrear condicionales, ciclos y funciones en ensamblador. Los podemos usar para recorrer la dirección que corresponde al teclado y las direcciones de la pantalla.
```asm
@16384    // Dirección de la pantalla
D=A       
@16       // será el puntero de la pantalla
M=D       // Almacenamos la dirección dondo inició en RAM 16
```
**2. Saltos Condicionales:** Los saltos condicionales son representados con 3 siglas ya pre establecidas en el lenguaje ensamblador. Estas sirven para que el programa salte a leer cierta linea de código determinada si sí se cumple la condición, si no se cumple, la lectura de las línea sigue en el orden que ya iba. Estos saltos nos permiten simular los if's del lenguaje de alto nivel.
```asm
@112        // Significa P
D=D-A       // Compara el valor almacenado en D con 112
@pinta      // Salta a la línea de código donde se pinta la pantalla
D;JEQ       // Si D es 0 (es decir, si el valor era 112), salta a "pinta"
```
**3. Loops:** se hacen con saltos incondicionales y condicionales. Esto permite repetir un bloque de instrucciones mientras se cumpla una condición determinada. Permite simular lo que serían acumuladores y contadores en lenguaje de alto nivel.
```asm
(LOOP)
// Instrucciones ROM
@LOOP       // Dirección a la que va a saltar
0;JMP       // Salto incondicional para repetir el ciclo
```
**4. Retornos:**  se pueden simular subrutinas guardando la dirección a la que queremos retornar antes de saltar a la función. Al finalizar la subrutina, se recupera esa dirección que guardamos para continuar la ejecución en el punto correcto.
```asm
@retorno       // punto de retorno
D=A
@2
M=D           // Guarda la dirección de retorno en R2
@pantalla
0;JMP         // Salta a la subrutina "pantalla"

(pantalla)    //Acá saltó
@2            // dirección de retorno en R2
A=M           // trae la dirección en R2 y la guarda en A
0;JMP         // Regresa al punto de retorno
```
