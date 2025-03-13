### ¿Por qué la versión de swapPorValor no logra intercambiar los valores de x e y en el main()?
Porque crea variables locales momentáneas para poder swapear el valor de ***X*** y ***Y***, al salir de la función a y b ya no existen globalmente entonces ***X*** y ***Y*** siguen con los mismos valores iniciales.

### ¿Cómo y por qué logran las otras dos funciones (por referencia y por puntero) modificar las variables originales?
Las otras dos funciones logran modificar el valor de la variables ***X*** y ***Y***, ya que las acceden por medio de su dirección o alias (en caso del de referencia). Al acceder a las direcciones de ***X*** y ***Y*** por medio de las variables momentáneas ***a*** y ***b***, entonces el valor si queda modificado permanentemente aunque salga de la función. Me explico mejor, al modificar usando un puntero estamos accediendo a la memoria (o más bien apuntando a ella), entonce aunque el programa salga de la función ya la memoria quedó modificada con los nuevos valores.

### ¿Cuáles son las ventajas y consideraciones de usar referencias versus punteros en este caso?
Las ventajas es que al usar un alias nos arroamos poner el *a para acceder valor de la variable al que apunta el puntero.
La consideración principal es que puede llegar a ser confuso, ya que si vemos un swap por puntero, sabremos de una que es eso, pero si vemos un swap por referencia puede llegar a ser confuso con el de swap por valor. Esta consideración hace que tengamos que ser cuidadosos y mejor ir a buscar la función para entender que tipo de swap es.

```cpp
#include <iostream>
using namespace std;

void swapPorValor(int a, int b) {
    int c;
    cout << "Dentro de swapPorValor, valor inicial a: " << a << " valor inicial b: " << b << endl;
    c = a;
    a = b;
    b = c;
    cout << "Dentro de swapPorValor, valor modificado a: " << a << " valor modificado b: " << b << endl << endl;
}

void swapPorReferencia(int& a, int& b) {
    int c;
    cout << "Dentro de swapPorReferencia, valor inicial a: " << a << " valor inicial b: " << b << endl;
    c = a;
    a = b;
    b = c;
    cout << "Dentro de swapPorReferencia, valor modificado a: " << a << " valor modificado b: " << b << endl << endl;
}

void swapPorPuntero(int* a, int* b) {
    int c;
    cout << "Dentro de swapPorPuntero, valor inicial a: " << a << " valor inicial b: " << b << endl;
    c = *a;
    *a = *b;
    *b = c;
    cout << "Dentro de swapPorPuntero, valor modificado a: " << a << " valor modificado b: " << b << endl << endl;
}

int main()
{
    int x = 5;
    int y = 10;
    cout << "Valor inicial de x : " << x << endl;
    cout << "Valor inicial de y : " << y << endl << endl << endl;

    swapPorValor(x, y);
    cout << "valor modificado de x : " << x << " valor modificado  de y: " << y << endl << endl << endl;

    swapPorReferencia(x, y);
    cout << "valor modificado de x : " << x << " valor modificado  de y: " << y << endl << endl << endl;

    swapPorPuntero(&x, &y);
    cout << "valor modificado de x : " << x << " valor modificado  de y: " << y << endl << endl << endl;
}
```
