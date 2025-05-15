#### <p align=center> Qué es una cola y cómo funciona el principio FIFO. </p>
Una cola es una lista enlazada compuesta por nodos, y luego esos nodos pueden ser lo que tu quieres que sean.
Entonces vamos por partes, primero te voy a poner la siguiente analogía:

Estás haciendo la fila del supermercado para pagar, hay varias personas esperando. La primera persona que paga es la que ya se puede ir, luego pasa el siguiente y asi sucesivamente.

Ahora comparemos eso: 
- La lista enlazada es la fila de personas.
- Cada persona es un nodo.
- El orden en que las personas llegan y se van, representa FIFO.

***Por que se dice que está enlazada?*** porque cada nodo tiene guarda la dirección del siguiente nodo. Volvemos a la analogía, cada persona en la fila sabe donde está ubicada la persona que tiene al frente. A eso se le llaman punteros, porque apuntan a una dirección, en el dibujo lo rojo son los punteros.

![Imagen de WhatsApp 2025-05-14 a las 19 11 14_c765532d](https://github.com/user-attachments/assets/7924098a-70fd-4c70-8db7-30523ecef12e)

***Que es FIFO?*** FIFO significa first in - first out, es decir, el que entró de primeras es el que se va de primeras. Siguiendo la lógica del ejemplo, el que está al frente de la fila es porque llegó primero, como paga de primeras es el que se va de una.


#### <p align=center> Cómo se implementa enqueue() y dequeue() en una cola. </p>

enqueue(): agrega un nodo al final de la cola. Acá también se verifica si la cola ya alcanzó su tamaño maximo. Basicamente, es la persona que asigna a cada cliente en una caja para que lo atiendan, entonces pone más personas atrás en la fila. A la fila le ponen un cartelito de que la caja esta llena a partir de tal persona. Cuando pasa eso se llama al dequeue(), para que quite la primera persona de la fila y ya pueda volver a entrar otra.
Acá tambien se actualiza quien es la nueva nalga de la fila, es como si llegara otra persona a hacer la fila y le dijera "bueno, ahora te toca a ti ser la nalga de esta fila, yo ya no lo soy"

dequeue(): borra el elemento que en ese momento es first in. Actualiza quien es la cabeza de la fila y quien es la nalga de la fila.

![Imagen de WhatsApp 2025-05-14 a las 19 31 02_74cbf943](https://github.com/user-attachments/assets/a791c80d-5a64-4e93-9bcf-bb815516e6ff)

#### <p align=center> Un error común en la implementación y cómo evitarlo. </p>

Un error común es que en el momento de hacerlo uno se enrede y pierda ese orden de FIFO, lo evitas siempre preguntandote quien entra y quien sale, además de mantener siempre el dibujito del supermercado.

Otro error común es no poner ***delete*** cuando ya ese nodo muere, delete es necesario para que no haya fugas de memoria, o como me gusta decir, para que no se queden por ahí flotando en la memoria.
