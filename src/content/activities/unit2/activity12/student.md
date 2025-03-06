### <p align="center">Condicionales</p> 
#### Ensamblador
```asm
    0 @5 
    1 D=A 
    2 @1 
    3 M=D 
    4 @10 
    5 D=A 
    6 @0 
    7 M=D 
    8 @0 
    9 D=A 
   10 @2 
   11 M=D 
   12 @0 
   13 D=M 
   14 @2 
   15 D=D-M 
   16 @24 
   17 D;JGT 
   18 @0 
   19 D=A 
   20 @2 
   21 M=D 
   22 @28 
   23 0;JMP 
   24 @0 
   25 D=A 
   26 @2 
   27 M=D 
   28 @28 
   29 0;JMP 
```
#### Alto nivel
```csharp
static void Main(string[] args)
{
    int x = 5;
    int y = 10;

    if (x>y) 
    {
        Console.WriteLine("X es mayor que Y");
    }
    else {Console.WriteLine("Y es mayor que X"); }           
}
```
### <p align="center">Ciclos while</p>  

#### Ensamblador
```asm
@0
D=A
@0
M=D      
(LOOP)
@0
D=M       
@10
D=D-A    
@14
D;JGE     
@0
M=M+1     
@LOOP
0;JMP
```
#### Alto nivel
```csharp
static void Main(string[] args)
{
    int x = 0;
    while (x>10)
    {
        x++;
    }

}
```
### <p align="center">Ciclos for</p>  

#### Ensamblador
```asm
@0
D=A
@0
M=D     
@0
D=A
@1
M=D       
(FOR_LOOP)
@1
D=M       
@10
D=D-A     
@20
D;JGE  
@0
M=M+1    
@1
M=M+1    
@FOR_LOOP
0;JMP
```
#### Alto nivel
```csharp
static void Main(string[] args)
{
int x = 0;
for (int i = 0; i < 10; i++)
 {
  x++;
 }
}
```
### <p align="center">Escritura de variables por medio de punteros</p> 

#### Ensamblador
```asm

```
#### Alto nivel
```csharp
#include <iostream>
using namespace std;

int main() {
    int x = 10;       // Se inicisliza X
    int* p = &x;      // p apunta a x
    int y = *p;       // Se lee el valor de x a través de p y se almacena en y

    cout << "Valor de x: " << x << endl;
    cout << "Valor de y (leído mediante p): " << y << endl;
    return 0;
}
```
### <p align="center">Lectura de variables por medio de punteros</p> 

#### Ensamblador
```asm
```
#### Alto nivel
```csharp
#include <iostream>
using namespace std;

int main() {
    int arr[3] = {1, 2, 3};     // Arreglo de 3 cositas
    int* p = arr;     // p apunta al primer elemento del arreglo osea [0]
    p[1] = 42;        // la posición 1 del array será = 42 (*(p + 1) = 42)
    cout << "Arreglo modificado: ";
    for (int i = 0; i < 3; i++) {
        cout << arr[i] << " ";       //Recorremos el arreglo con un for
    }
    cout << endl;
    return 0;
}

```
### <p align="center">Manipulación de un arreglo por medio de punteros</p> 

#### Ensamblador
```asm
```
#### Alto nivel
```csharp
```
### <p align="center">Llamado a funciones con parámetros</p> 

#### Ensamblador
```asm
```
#### Alto nivel
```csharp
```
### <p align="center">Llamado a funciones con retorno de parámetros</p>  

#### Ensamblador
```asm
```
#### Alto nivel
```csharp
```
```csharp
```
