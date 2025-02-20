``` asm
 0 @5 
 1 D=M 
 2 @10 
 3 D=A-D 
 4 @10 
 5 D;JLT 
 6 @7
 7 M=1 
 8 @0 
 9 0;JMP 
 10 @7 
 11 M=0 
 12 @0 
 13 0;JMP 
```
#### Cuando el valor en la dirección es mayor o igual a 10.
<img width="192" alt="image" src="https://github.com/user-attachments/assets/698087ad-10ca-4c27-be1c-cb9022f82ab8" />
<img width="144" alt="image" src="https://github.com/user-attachments/assets/08285843-f423-48c9-8c2f-69b6fab63a03" />

#### Cuando el valor en la dirección 5 es menor que 10
<img width="181" alt="image" src="https://github.com/user-attachments/assets/4b341549-b1eb-4fe2-9d23-e9e36e100347" />
<img width="118" alt="image" src="https://github.com/user-attachments/assets/b9b229eb-fc8a-44ff-8d70-cb7154150977" />
