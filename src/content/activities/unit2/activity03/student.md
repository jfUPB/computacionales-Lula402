### por qué son equivalentes.
Los programas anteriores son equivalentes porque ambos representan un ciclo, con la ayuda de un contador (i) y un acumulador (sum). La condición es que el ciclo va a seguir en loop hasta que i<=100, por lo que en ambos cada vez se le suma +1.

### Conviersión de la versión del for a ensamblador
```asm
 0 @0 
 1 D=A 
 2 @1 
 3 M=D 
 4 @1 
 5 D=A 
 6 @2 
 7 M=D 
 8 @1 
 9 D=M 
10 @2 
11 D=D+M 
12 @1 
13 M=D 
14 @2 
15 D=M 
16 @1 
17 D=D+A 
18 @2 
19 M=D 
20 @2 
21 D=M 
22 @100 
23 D=D-A 
24 @8 
25 D;JLE 
26 @0 
27 0;JMP 
```

### Versiones en ensamblador del while y del for. ¿Qué puedes concluir?
Comparando las versiones en ensamblador del while y del for puedo concluir que 
