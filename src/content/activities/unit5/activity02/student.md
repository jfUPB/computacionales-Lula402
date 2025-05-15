### <p align=center> Pregunta 1 </p>
#### ¿Qué esperas ver en memoria (hipótesis)? Ejecuta el código y muestra una captura de pantalla del objeto en la memoria. 

Espero que al depurar el .cpp en la función de draw que es donde se supone que se debe estar usando el ofApp. En memoria debería ver el objeto tipo ofApp * que es la dirección de memoria del objeto a la que apunta this.

<img width="400" alt="image" src="https://github.com/user-attachments/assets/71848944-b768-4929-9580-7c4c188aa3b7" />


<img width="600" alt="image" src="https://github.com/user-attachments/assets/16455730-b157-492c-8173-ed5e8383a4f0" />


#### ¿Qué puedes observar? 
El momento en el que se crea un objeto de tipo ofApp y se le asigna una dirección de memoria.

#### ¿Qué información te proporciona el depurador? 
La dirección en la que empieza el objeto.

#### ¿Qué puedes concluir?
Que this apunta a un objeto tipo ofApp


### <p align=center> Pregunta 2 </p>

<img width="400" alt="image" src="https://github.com/user-attachments/assets/ed19c13c-a238-41e7-950f-e8f63c89d442" />

Entonces creería que lo siguiente es todo el objeto:

<img width="295" alt="image" src="https://github.com/user-attachments/assets/8346a064-81d5-4f4d-9f50-2e36f55da9ef" />


<img width="600" alt="image" src="https://github.com/user-attachments/assets/70ea287a-22df-4b25-b9ef-2b398a5e4200" />

#### Explosión de tipo 0, que es la circular:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/0ec2b915-2d8d-4d6b-a150-99088b18776c" />

#### ¿Qué puedes observar en la memoria? 
Que hasta que en el canvas no de un click, la memoria me advierte "No disponible cuando se está ejecutando el código que está siendo depurado." pero cuando presiono click y creo una particula, ahí si de una la memoria empieza a mostrar los objetos.

#### ¿Qué información te proporciona el depurador? 

<img width="600" alt="image" src="https://github.com/user-attachments/assets/d609f5b2-7e17-4aaa-b937-893513e89b38" />

Me dice a donde apunta this, me muestra las paraticulas y sus tipos (como rising o circular). Me muestra el tipo de explisión (si es 0, 1 o 2). Numparticles que es un valor randomizado entre 20 y 30, que luego se va a usar en el ciclo en el que se determina el tipo de explosión.

#### ¿Qué puedes concluir? NO OLVIDES tener a la mano todas la jerarquía de clases que componen a CircularExplosion. De esta manera podrás identificar cada parte del objeto en memoria.
Concluyo que CircularExplosion hereda de ExplosionParticle, y que ExplosionParticle hereda de Particle. 

### <p align=center> Pregunta 3 </p>
Entonces primero le di click al canvas, creé una particula. En variables salió lo siguiente, de ahí agarré la dirección de this (particle) y tambien me fije que si fuera explosion=0 (circular)

<img width="820" alt="image" src="https://github.com/user-attachments/assets/699a424b-9f46-4a84-bd38-556d67113a6a" />

Luego busqué esa dirección en memoria. Si se supone que cuando se crea una particula y se usa un método virtual, lo primero que aparece en el objeto en memoria es el _vtable. En este caso creo que lo que resalté con azul es el _vtable.

<img width="332" alt="image" src="https://github.com/user-attachments/assets/abe85c78-9f12-4eda-a69a-aea60ac946dd" />

Con little endian _vtable es 0x0000000140555260, la busco en memoria. No sabría cual pertenece a cual, pero se supone que cada una de esas lineas de memoria es la dirección a la funcion que se llamó.

<img width="325" alt="image" src="https://github.com/user-attachments/assets/35d0bd42-1b4b-4d70-bd96-a2affb6eddca" />

Ahí solo creé 1 particula que es rising particle y que en tipo de explosion dice circular. Me metí a particles, esta es la [0] y dentro de _vfprt están las funciones, que segun eso usó 7 funciones para tan solo esa particula.
Mi tabla de funciones se ve así: 

<img width="862" alt="image" src="https://github.com/user-attachments/assets/d35d99d3-e510-4171-bb7c-4901c97f9fdf" />

### <p align=center> Pregunta 4 </p>
Intenté muchooo como hacer que me saliera especificamente un objeto StarExplosion. Puse breakpoints en el update, use la ventana de inspección, hasta puse que me saliera un mensaje por cosola, el cual si sale pero sigo sin encontrar el objeto StarExplosion.

Esta fue con circular, que tampoco encontré como:

<img width="438" alt="image" src="https://github.com/user-attachments/assets/10550270-923f-4470-9ef9-d3f5409c62bc" />


<img width="848" alt="image" src="https://github.com/user-attachments/assets/6e990586-a67b-4e2d-9b87-4fe3e68311cb" />

### <p align=center> Pregunta 5 </p>
#### Qué puedes ver? 
Puedo ver que se deja claro que es una StarExplosion o una CircularExplosion.
Puedo ver que los nombres de las funciones son las mismas.
Puedo ver que la dirección de memoria donde están las funciones es diferente para cada objeto.

#### ¿Qué puedes concluir? 
Que si hay un polimorfismo ahí.

#### ¿Qué relación existe entre la tabla de funciones y los métodos virtuales?  
Cuando coloco que un método es virtual, en c++, el compilador ya sabe que lo primero que va a tener al crear un objeto es el _vtable.  _vtable es un puntero a esa tabla de funciones.

Cuando yo uso un método en una clase hija y se llama igual a la del padre, por ejemplo update, yo tengo ese mismo nombre pero les tengo comportamientos diferentes; lo que hace es que al ponerle método virtual, el compilador ya saber que va a tener que ir a buscar ese puntero a la tabla, buscar la tabla y ahí va a estar la dirección a la funcion con el comportamiento que si es de la clase hija.

#### ¿Para qué crees que pueda servir una tabla de funciones virtuales?
Para heredar funciones de mi clase padre, pero yo las uso como quiera, osea, yo les asigno un comportamiento diferente aunque se llamen igual. Eso permite más creatividad o más personalización de cada clase que hereda.


### <p align=center> Pregunta 6 </p>
No permite compilar, saca el siguiente error:

<img width="749" alt="image" src="https://github.com/user-attachments/assets/2c9fdbd9-1468-4a10-9759-28e2f6cbf85f" />

El error lo marca en la línea 23 que dice ```std::cout << obj.secret1 << std::endl;``` , es justo donde en el main se intenta imprimir secret1, pero claramente no se puede porque es privado, osea esta como con candadito.

### <p align=center> Pregunta 7 </p>
Ahora si funciona e imprime por consola los 3 secrets. Puedo concluir que dentro de la clase todos los métodos tienen acceso a los otros métodos independientemente que nivel de seguridad tengan. Como main llama al método público y el público puede extraer la info del privado entonces no hay problem.

<img width="398" alt="image" src="https://github.com/user-attachments/assets/32a4d8fc-d55f-4606-9a78-6d35aace40b5" />

### <p align=center> Pregunta 8 </p>
Encapsulamiento es ponerle diferentes tipos de cerraduras a mis funciones dentro de una clase. Es importante porque puedo tener control sobre la seguridad y más orden, como en el ejemplo anterior, que aunque yo cambie algo en el private no va a afectar o dañar directamente a main o al public.
Si yo tengo un publico es como una cerradura que no necesita llave, si tengo un protegido es porque solo algunos tienen la llave y si tengo uno privado es porque solo YO tengo la llave.

### <p align=center> Pregunta 9 </p>
(Profe voy a seguir usando su imagen porque sigo sin saber como hacer eso especificamente)

CircularExplosion es un objeto, que por dentro en realidad lleva la estructura de ExplosionParticle, y ExplosionParticle por dentro lleva la estructura de Particle. 

En los campos de memoria usa los mismos que tiene ExplosionParticle y should explode y draw de Particle, basicamente CircularExplosion no añade nada más sino que solo cambia el comportamiento de lo que heredó.

### <p align=center> Pregunta 10 </p>
Se implementa con dos punticos

``` class ExplosionParticle : public Particle ```
``` class CircularExplosion : public ExplosionParticle ```

