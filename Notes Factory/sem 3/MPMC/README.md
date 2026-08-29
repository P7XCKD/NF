### XP header (1) 
<p align="center">

<a href="https://ibb.co/0y4jv78d" align="center"><img src="https://i.ibb.co/8gvDtCTS/image.png" alt="image" align="center"></a>
</p>
<div align="center"> <b>
<u>DEPARTMENT OF INFORMATION TECHNOLOGY</u>

Course: Microprocessor and Microcontroller Lab( ITL304)
 B.Tech. (Information Technology) – Semester III
Academic Year: 2026-27 (ODD Semester) </b>
</div>

***

## 8086 ALP Steps

### 1. Write Code

```text
edit filename.asm
```

Write the 8086 program, then **Save → Exit**.  
_Creates the source `.asm` file._

### 2. Assemble

```text
tasm filename.asm
```

_Checks the code for errors and creates a `.obj` file._

### 3. Link

```text
tlink filename.obj
```

_Converts the `.obj` file into an executable `.exe` file._

### 4. Execute

```text
filename.exe
```

_Runs the assembled program._

### 5. Debug

```text
td filename.exe
```

_Opens Turbo Debugger to execute instructions step-by-step and observe registers/memory._