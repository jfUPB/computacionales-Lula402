### Explica qué ocurre al copiar un objeto en C++ y en C#. ¿Qué diferencias encuentras?
En C++ al copiar un objeto lo que se está copiando es su contido uno por uno, pero la copia y el original tienen referencias diferentes aunque compartan el mismo contenido. Cuando uno cambia el contenido de la copia, el contenido del original NO cambia.Este objeto vive en el Stack y se limpia al terminar la función.

En C# al copiar un objeto lo que realmente se está copiando es la dirección del Heap, es decir la copia y el original apuntan a lo mismo. Entonces, cuando uno modifica el contenido al que apunta copia, tambien esta modificando el original porque es el mismo contenido al que apunta. Este objeto fue creado con "NEW" por lo que vive en el Heap y el GC se encarga de limpiarlo.

### ¿Qué es copia en C++ y en C#? ¿Es una copia independiente de original?
Una copia en C++ es un duplicado del objeto con su propia dirección, es decir un nuevo objeto.
Una copia en C# es un nuevo objeto apuntando a la misma dirección que el original, es decir mismo objeto.
