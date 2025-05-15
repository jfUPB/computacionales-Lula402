https://github.com/user-attachments/assets/bb021590-333a-4404-9240-e4291cd4749a

```asm
    0 @16384 
    1 M=-1 
    2 D=A 
    3 @10 
    4 M=D 
    5 @24576 
    6 D=M 
    7 @130 
    8 D=D-A 
    9 @17 
   10 D;JEQ 
   11 @2 
   12 D=D-A 
   13 @25 
   14 D;JEQ 
   15 @5 
   16 0;JMP 
   17 @10 
   18 A=M 
   19 M=0 
   20 A=A-1 
   21 M=-1 
   22 D=A 
   23 @3 
   24 0;JMP 
   25 @10 
   26 A=M 
   27 M=0 
   28 A=A+1 
   29 M=-1 
   30 D=A 
   31 @3 
   32 0;JMP
```
