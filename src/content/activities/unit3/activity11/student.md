#### <p align=center> ¿Qué puedes concluir de los miembros estáticos y de instancia de una clase en C++? ¿Cómo se gestionan en memoria? ¿Qué ventajas y desventajas tienen? ¿Cuándo es útil utilizarlos? </p>

**static int total;** es un miembro estático (atributo estático), como habiamos visto en actividades anteriores el ***"static"*** permite que sea global y que lo puedan acceder todos. Por eso es que cuando cada objeto tipo contador es creado y modifica el valor de ***total**, todos modifican la misma variable.

**int valor;** es un miembro de instancia (atributo). Este es un atributo personal que cada objeto tipo contador tiene. Cada que un objeto hace una modificación a la variable **valor**, esta modificando SU PROPIA variable valor.

En memoria se gestionan de la siguiente manera:

El miembro estático le pertenece al paquetico de datos de la CLASE, porque no le pertence solo a alguno de los objetos, sino a la clase.
Cada miembro de instancia, como su nombre lo dice está en cada instancia de la clase. Entonces Valor le pertenece a cada paquetico de datos de cada OBJETO.

**Las deventajas:**
El miembro estático no puede existir en cada instancia de la clase, solo existe una versión y la comparten todos.
El miembro de instancia, ocupa un pedacito de memoria cada que se cree un nuevo objeto.

**Las ventajas:**
El miembro estático todos los objetos lo pueden acceder sin restricciones.
El miembro de instancia, permite que cada objeto tenga sus cositas y las cambie como quiera sin afectar a los demás.

------------------------------------------------------------------------------------------------------------------------------

#### <p align=center> En el programa, en qué segmento de memoria se están almacenando c1, c2, c3 y Contador::total? Ten especial cuidado con la respuesta que das para el caso de c3, piensa de nuevo, qué es c3 y qué está almacenando. Ahora, responde de nuevo, en qué segmento de la memoria se está almacenando c3 y en qué segmento de la memoria se está almacenando el objeto al que apunta c3. </p>

**c1 ->** segmento stack

**c2 ->** segmento stack

**c3 ->** segmento heap

**Contador::total ->** segmento variables static y globales

Me equivoqué, respondiendo de nuevo:

**c3 ->** segmento stack

Porque c3 es una variable que guarda una dirección de un objeto tipo contador, cual objeto? el que **SÍ** se está creando en el Heap "new Contador(15);"
