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

<img width="600" alt="image" src="https://github.com/user-attachments/assets/70ea287a-22df-4b25-b9ef-2b398a5e4200" />

#### Explosión de tipo 0, que es la circular:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/0ec2b915-2d8d-4d6b-a150-99088b18776c" />

#### ¿Qué puedes observar en la memoria? 
Que hasta que en el canvas no de un click, la memoria me advierte "No disponible cuando se está ejecutando el código que está siendo depurado." pero cuando presiono click y creo una particula, ahí si de una la memoria empieza a mostrar los objetos.

#### ¿Qué información te proporciona el depurador? 

<img width="600" alt="image" src="https://github.com/user-attachments/assets/d609f5b2-7e17-4aaa-b937-893513e89b38" />

Me dice a donde apunta this, me muestra las paraticulas y sus tipos (como rising o circular). Me muestra el tipo de explisión (si es 0,1 o 2). Numparticles que es un valor randomizado entre 20 y 30, que luego se va a usar en el ciclo en el que se determina el tipo de explosión.

#### ¿Qué puedes concluir? NO OLVIDES tener a la mano todas la jerarquía de clases que componen a CircularExplosion. De esta manera podrás identificar cada parte del objeto en memoria.
