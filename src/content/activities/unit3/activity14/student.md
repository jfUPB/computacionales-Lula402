#### Escribe un texto, tratando de recordar de memoria, donde expliques lo que aprendiste en esta unidad argumentando con ejemplos concretos, qué conceptos comprendiste y por qué los comprendiste.

En esta unidad entendí cómo funciona la memoria en C++, sobre todo la diferencia entre stack y heap. Por ejemplo, si creo un objeto con new, ese objeto se guarda en el heap, pero el puntero vive en el stack. También el uso de static, como cuando puse static int total;, que sirve para que ese dato sea compartido por todos los objetos de esa clase, no importa cuántos objetos cree. Me quedaron más claros los destructores y el delete, porque vi que si no libero memoria, puedo tener leaks. En conclusión entender todo eso me ayudó a organizar mi código y pensar en cómo se va manejando todo por detrás.

#### ¿Cuáles fueron los conceptos más desafiantes de la unidad? ¿Por qué?
La diferencia entre paso por valor, referencia y puntero. Porque fue bastante confuso entender que en unos estoy creando un duplicado y en otros sigo trabajando con el original, entonces fue desafiante porque uno podía dañar el código muy facil sino entendía eso.
En especial paso por referencia como tiene que ver con direcciones y usualmente con el heap era muy enredado.

#### ¿Qué estrategias utilizaste para comprender esos conceptos desafiantes?
Practicar y cada vez volverme a narrrar que es lo que está pasando por debajo de todo eso.

#### ¿Qué estrategias te resultaron más efectivas?
Narrarme con analogías y ponerle como roles a las cosas para asi tener una imagen mental de como es.

#### ¿Qué harás en las próximas unidades para mejorar tu comprensión de los conceptos más desafiantes? Para esta pregunta formula un plan de acción concreto, no lo enuncies como un deseo, sino como un plan con pasos concretos.

1. equivocarme para saber que algo falla
2. identificar especificamente que es lo que no entiendo
3. pedirle al profe o a chatg que me tutoreen con que es eso
4. hacer experimentos?
5. practicar 
