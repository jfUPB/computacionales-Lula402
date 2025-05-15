#### <p align=center> Explicación del ciclo de vida de un objeto en el stack. </p>
1. El objeto cobra vida en el Stack cuando se crea un objeto tipo punto en este caso y se inicializa. Lo que está por detrás es que realmente cobra vida con el constructor, que es el que crea el objeto con esos atributos entregados como tal. Es como si al crear el objeto estoy haciendo una masita con todo lo que quiero que tenga cuando se la doy al constructor es el quien coge el molde (clase) y hace la galleta full.

2. Durante el bloque el objeto que cree sigue existiendo tranquilo.

3. Cuando el código sale del bloque, automáticamente se llama al destructor, porque ese objeto lo cree dentro de un bloque osea que siempre estuvo vivo en el stack. Al llamar el destructor este mata mi objeto y puf, ya no existe.


Cuando se crea y mientras estoy dentro del bloque

<img width="350" alt="image" src="https://github.com/user-attachments/assets/fd23690f-1eee-4348-b08f-573cc1ce83d4" />

Cuando salgo del bloque

<img width="350" alt="image" src="https://github.com/user-attachments/assets/5cfd6806-6ab7-40d3-9985-5c70bd66240c" />

#### <p align=center> Explicación del ciclo de vida de un objeto en el heap. </p>

1. El objeto cobra vida en el Heap cuando digo ***new punto***. el constructor se encarga de crear este punto y además de una vez estoy guardando la dirección de este punto en un puntero, porque luego la necesitaré.

2. Durante todo el tiempo que yo quiera objeto sigue vivo.

3. Cuando llamo a delete, es porque le estoy diciendo al destructor "ey, ya quiero que limpies esto", entonces viene el destructor y mata mi objeto que estaba en el Heap. La dirección la necesitabamos almacenar para eso, para que el compilador sepa en que parte del Heap está mi objeto y poder ir a matarlo.


Cuando no se le ha dado vida

<img width="350" alt="image" src="https://github.com/user-attachments/assets/5a2f6868-e885-49f6-993b-0832b5d67087" />

Cuando se le da vida

<img width="350" alt="image" src="https://github.com/user-attachments/assets/57b40276-123b-4fdc-ac8f-6405f7241a9d" />

y ahí se puede ver que lo que guarda es la dirección del punto creado en el Heap 

<img width="350" alt="image" src="https://github.com/user-attachments/assets/969b19d3-c195-401c-a6f6-f90cdce85f8e" />


#### <p align=center> ¿Compila? ¿Por qué?  </p>
No compila, por una razón muy mini, porque estoy intentando usar algo que ya no existe.

En el bloque 2 estoy creando un punto en el Heap, hasta ahí vamos bien, porque aunque salga del bloque ese punto seguirá vivo porque no he decidido que se muera.

El problemita está porque estoy guardando la dirección de ese punto en una variable llamada ***pBloque2*** y donde se crean estas variables? yep en el Stack. Cuando salgo de este bloque el punto sigue vivo pero esta variable que guarda su dirección se muere.

Cuando intento imprimir o borrar el punto, no se donde está viviendo en el Heap, porque ya no tengo su dirección, basicamente ***punto*** está viviendo en el limbo y no lo puedo encontrar para usarlo.

#### <p align=center> Modificando pBloque2 ¿Qué ocurre? ¿Por qué?  </p>
Ahora compila sin ningún problema.
Porque estoy creando la variable puntero ***pBloque2*** fuera del bloque y guarda la dirección de "nada" por el momento.

Dentro del bloque le estoy ahora si diciendo que apunte al new punto. 

Al salir del bloque ambos quedan vivos.

#### <p align=center> ¿Por qué el objeto pBloque se destruye al salir del bloque y pBloque2 no?  </p>
Porque pBloque vive en el Stack entonce al salir del bloque muere, mientras que pBloque2 no se está declarando dentro del bloque sino afuera, entonces al salir del bloque no le pasa nada.

#### <p align=center> Recuerda de nuevo, pBloque2 es un objeto o es una referencia a un objeto?  </p>
pBloque2 es una referencia a el objeto punto, es decir, guarda su dirección.

#### <p align=center> ¿En qué parte de la memoria se almacena pBloque2?  </p>
pBloque2 se está almacenando en el Stack, porque es una variable (puntero) común y corriente, creada dentro de la función Main.

#### <p align=center> ¿En qué parte de la memoria se almacena el objeto al que apunta pBloque2? </p>
El objeto al que apunta pBloque2 se almacena en el Heap, porque es creado con ***"New"*** y eliminado con ***"delete"***.
