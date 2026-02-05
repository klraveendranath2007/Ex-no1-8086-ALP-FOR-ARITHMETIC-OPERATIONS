## 8086 ASSEMBLY LANGUAGE PROGRAM FOR ARITHMETIC OPERATIONS

### AIM

To write and execute Assembly Language Programs to perform arithmetic operations for the 8086 microprocessor.



### APPARATUS REQUIRED

Personal Computer with MASM Software

### 1. ADDITION

#### ALGORITHM

1.Initialize registers and memory.    
2.Load two 16-bit numbers into AX and BX.  
3.Add both numbers.  
4.Check for carry and increment counter if carry occurs.  
5.Store sum in memory.  
6.Store carry in next memory location.  
7.Stop execution.  


#### FLOW CHART
<img width="377" height="622" alt="image" src="https://github.com/user-attachments/assets/bd33a0c3-7a78-4c35-9c80-93dab8bae111" />

#### PROGRAM

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE
ORG 1000H
MOV CL,00H
MOV AX,1234H
MOV BX,1234H
ADD AX,BX
JNC L1
INC CL
L1:MOV SI,1200H
MOV [SI],AX
MOV [SI+02],CL
MOV AH,4CH
INT 21H
CODE ENDS
END
```

#### OUTPUT TABLE

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      1200 : 12          |        1204 : 24         |
|      1201 : 34          |        1205 : 68         |  
|      1202 : 12          |        1206 : 00         |
|      1203 : 34          |                          |  


#### MANUAL CALCULATION
<img width="250" height="254" alt="image" src="https://github.com/user-attachments/assets/b54341ba-f56c-479b-b081-416fc9ef4932" />


---

### OUTPUT IMAGE FROM MASM SOFTWARE
<img width="540" height="300" alt="debug_000" src="https://github.com/user-attachments/assets/3bbca00c-6660-43b1-be90-9012327f1f2c" />

### 2. SUBTRACTION

#### ALGORITHM

1.Initialize registers and memory.  
2.Load two 16-bit numbers into AX and BX.  
3.Subtract the contents of BX from AX.  
4.Check for borrow and increment counter if borrow occurs.  
5.Store the difference in memory.   
6.Store the borrow in the next memory location.  
7.Stop execution.  

#### FLOWCHART

<img width="377" height="584" alt="image" src="https://github.com/user-attachments/assets/fec934e1-7f2b-4b6e-bd8a-2b0b6a80ef52" />

#### PROGRAM
```asm
CODE SEGMENT
ASSUME CS: CODE, DS: CODE
ORG 1000H
MOV AX,1234H
MOV BX,1234H
SUB AX,BX
JNC DOWN
INC CL
DOWN: MOV SI,1200H
MOV [SI],AX
MOV [SI+2],CL
MOV AH,4CH
INT 21H
CODE ENDS
END
```


#### OUTPUT TABLE

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      1200 : 12          |        1204 : 00         |
|      1201 : 34          |        1205 : 00         |  
|      1202 : 12          |                          |
|      1203 : 34          |                          |  


#### MANUAL CALCULATION

<img width="209" height="201" alt="image" src="https://github.com/user-attachments/assets/b1eefd8e-017e-4545-9979-a51891011699" />

---


### OUTPUT SCREEN FROM MASM SOFTWARE
<img width="540" height="300" alt="debug_001" src="https://github.com/user-attachments/assets/ff730153-68b5-4301-a2f2-b78d75d9fa5f" />

### 3. MULTIPLICATION

#### ALGORITHM

1.Initialize registers and memory.  
2.Clear the DX register to store the higher-order result.  
3.Load the first 16-bit number into register AX.  
4.Load the second 16-bit number into register BX.  
5.Multiply the contents of AX and BX.  
6.Store the lower 16-bit result from AX into memory.  
7.Store the higher 16-bit result from DX into the next memory location.  
8.Stop execution.  

#### FLOWCHART

<img width="323" height="539" alt="image" src="https://github.com/user-attachments/assets/6f111bbb-d1b2-4723-8f1d-a6b88d011a79" />


#### PROGRAM

```asm
CODE SEGMENT
ASSUME CS: CODE, DS: CODE
ORG 1000H
MOV DX,0000H
MOV AX,1234H
MOV BX,1234H
MUL BX
MOV SI,1200H
L1: MOV[SI],AX
MOV [SI+02H],DX
MOV AH,4CH
INT 21H
CODE ENDS
END
```

#### OUTPUT TABLE

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      1200 : 12          |        1204 : 90         |
|      1201 : 34          |        1205 : 5A         |  
|      1202 : 12          |        1206 : 4B         |
|      1203 : 34          |        1207 : 01         | 

#### MANUAL CALCULATION

<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/c8cb5fba-9636-45e4-ae65-677a3b5c757c" />


---

### OUTPUT SCREEN FROM MASM SOFTWARE
<img width="540" height="300" alt="debug_002" src="https://github.com/user-attachments/assets/7e96f009-f4ea-450c-b76f-f6841372e3e4" />

### 4. DIVISION

#### ALGORITHM

1.Initialize registers and memory.  
2.Clear the DX register.  
3.Load the dividend into AX and the divisor into BX.  
4.Divide the contents of AX by BX.  
5.Store the quotient in AX and the remainder in DX.  
6.Store the quotient in memory.  
7.Store the remainder in the next memory location.  
8.Stop execution.  

#### FLOWCHART
<img width="255" height="280" alt="image" src="https://github.com/user-attachments/assets/b96a307e-4799-485f-a28f-20f2a5dbe3b1" />

#### PROGRAM

```asm
CODE SEGMENT
ASSUME CS:CODE,DS:CODE
ORG 1000H
MOV DX,0000H
MOV AX,1234H
MOV BX,1234H
DIV BX
MOV SI,1200H
MOV [SI],AX
MOV [SI+02H],DX
MOV AH,4CH
INT 21H
CODE ENDS
END
```

#### OUTPUT TABLE

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      1200 : 12          |        1204 : 01         |
|      1201 : 34          |        1205 : 00         |  
|      1202 : 12          |        1206 : 00         |
|      1203 : 34          |        1207 : 00         |  



#### MANUAL CALCULATION
<img width="200" height="250" alt="image" src="https://github.com/user-attachments/assets/6fdf7457-4d7d-4a82-8719-dbc57b8f930d" />



---
### OUTPUT FROM MASM SOFTWARE
<img width="540" height="300" alt="debug_003" src="https://github.com/user-attachments/assets/a17eb401-a191-46d1-bec8-86c19aa0b160" />



### RESULT

Thus, the Assembly Language Programs for 8086 to perform arithmetic operations (Addition, Subtraction, Multiplication, and Division) using both direct and indirect methods were successfully written and executed using MASM.

