### 1. ¿Qué ocurre después de llamar a la función cambiarNombre? 
Cuando se llama la función por el momento los campos de P y Nuevo Nombre están vacios.
<img width="450" alt="image" src="https://github.com/user-attachments/assets/0bde5af7-07a8-4eb5-9e77-7030a8a4efc7" />


Cuando se ejecuta, ahora si cambian los campos. El nombre de P se hizo = al nuevo nombre, que es "cambiado". Tambien desde que se llamó la función se dijo que P iba a ser como el original, por eso conserva el 70 , 80.
<img width="450" alt="image" src="https://github.com/user-attachments/assets/60ace9b9-dc89-48b4-8536-a675eb839d58" />

### 2. ¿Por qué aparece el mensaje Destructor: Punto cambiado(70, 80) destruido.?
Despues de llamar a la función cambiarNombre, este mensaje aparece porque se ejecuta el pedacito de código del destructor. 
Por que el destructor se ejecuta? porque al terminar con la función cambiarNombre, el objeto "p" queda volando, entonce el compilador sabe que yo especifique un destructor y va y lo usa para limpiar a "p".

### 3. ¿Por qué original sigue existiendo luego de llamar cambiarNombre?
Original sigue existiendo porque se creó dentro del Main, y durante la ejecución hasta el final, pues el Main no ha terminado. Es decir, como Original está en el stack y pertenece al Main, hasta que la función Main no termine Original sigue vivo.

### 4. ¿En qué parte del mapa de memoria se encuentra original y en qué parte se encuentra p? ¿Son el mismo objeto? (recuerda usar siempre el depurador para responder estas preguntas).
Original se encuentra en el Stack. Así se ve cuando es creado:
<img width="450" alt="image" src="https://github.com/user-attachments/assets/e4db9625-80b7-47f5-8d1e-de2cc018b392" />

Al final del Main hay un ***Return***, entonces lo que le dice ese return a la función es como "bueno terminamos el trabajo acá" y trin, cierra la cajita (función). Como la cajita se va a cerrar, los objetos del Stack, en este caso "original", van a quedar fuera del alcance (scope), entonces por eso se va al destructor para que no quede por ahi volando nada (memory leak).
<img width="450" alt="image" src="https://github.com/user-attachments/assets/c6a0e601-bfc2-4c5b-a194-a255a1cd398f" />

------------------------------------------------------------------------------------------------------------------------------

P se encuentra en el Stack también, al salir de ***cambiarNombre*** se muere.

------------------------------------------------------------------------------------------------------------------------------
No son el mismo objeto, cuando yo llamo la fucnión  ***cambiarNombre*** y le digo que para el objeto "P" tipo punto que necesita, tome el "original", lo que estoy haciendo es decirle a ***cambiarNombre***: "Mira, te paso por valor el objeto original, pero eso significa que creé una copia para ti y yo me quedo con la original".

Y de hecho esto se puede comprobar con las direcciones de la Memory:

<p align=center> Dirección del objeto Original </p>
<p align=center>
<img width="450" alt="image" src="https://github.com/user-attachments/assets/0e6de8ed-ba3b-42d0-8ad6-4cdbb773a9b6" />
</p>

<p align=center> Dirección del objeto P (Copia del original) </p>
<p align=center>
<img width="450" alt="image" src="https://github.com/user-attachments/assets/6b3f482f-8918-42d3-95a3-185861916c41" />
</p>

### 5. ¿Qué ocurre ahora? ¿Por qué?
Ahora lo que ocurre es que si se está afectando el punto original. Al entrar a cambiarNombre con ***"Punto& p"*** se está pasando por referencia, entonces NO se está creando una copia y NO es un puntero, es una referencia. Basicamente es "Oye cambiarNombre te voy a pasar este punto llamado "original", pero mientras tu lo tengas le vas a poner un apodo (alias) y le vas a decir P". Como la función me va a devolver ese mismo objeto que yo le presté, por eso es que los cambios si afectan el original. 

<p align=center> Original -> pasa a llamarse -> cambiado </p>
<img width="450" alt="image" src="https://github.com/user-attachments/assets/a1ce0110-fe1d-40d7-919e-8130c0beb94c" />
<img width="450" alt="image" src="https://github.com/user-attachments/assets/9ff21ec5-1b26-42cd-adde-a6a819ffe6a1" />

Además de todo eso, el destructor no se ejecuta pues porque a la final no estoy creando nada nuevo, entonces no hay nada para borrar.

### 6. ¿Qué ocurre ahora? ¿Por qué?
Ahora lo que ocurre es que le estoy pasando a la función cambiarNombre la dirección del original al decirle ***"&Original"***.

Lo que la función espera en ese campo en efecto es una dirección, porque dice: ***Punto(*) p**, lo que significa que **P** es una variable que almacena una dirección (*) de un objeto tipo **punto** y quien es tipo punto? **original**

1. Se crea original y ahí está su dirección
<img width="570" alt="image" src="https://github.com/user-attachments/assets/b87696c0-8d44-42f1-a810-d14f1297d33a" />

2. Voy a la memoria, busco la supuesta dirección de original y compuebo que si es la dirección a ese objeto.
<img width="318" alt="image" src="https://github.com/user-attachments/assets/36c30d97-e9cf-4511-839f-0340dadba778" />

3. Depues de ejecutarse cambiarNombre, veo que ahora name=cambiado, pero veo que parece ser que tiene la misma dirección.
<img width="560" alt="image" src="https://github.com/user-attachments/assets/d7a340f3-702d-4812-804d-9361f5ec3961" />

4. Voy a la memoria, busco la supuesta dirección de cambiado y compuebo que si es la misma dirección que tenía original, solo que ahora cambiío algo dentro de ese objeto pero sigue siendo el mismo.
<img width="318" alt="image" src="https://github.com/user-attachments/assets/ed5c61e0-42af-4340-8d9d-dfd1bc543aa1" />

Además no se llama el destructor porque no estoy creando nada nuevo.

------------------------------------------------------------------------------------------------------------------------------
En este caso ***<p align=center> ¿Cuál es la diferencia entre pasar un objeto por valor, por referencia y por puntero? </p>***

| ... | Por Valor | Por referencia | Por Puntero |
| -------------| ------------- | ------------- | ------------- |
| **Que pasa?** | Estoy creando una copia del objeto que le pasé  | Estoy poniendole un alias al objeto que le pasé  | Estoy pasandole la dirección del objeto  |
| **Que cambia?** | Modifica la copia, pero NO el original se mantiene  | SI cambia el objeto original aunque lo estemos manejando bajo un alias  | SI cambia el original, porque estoy llendo a buscarlo a la memoria y cambiandolo desde allá  |
| **Destructor** | Si se llama porque tengo que limpiar esa copia que cree para evitar memory leaks al terminar la función | No se llama porque no cree nada nuevo y sigo trabajando sobre el original  | No se llama porque estoy trabajando siempre sobre la dirección del original |
