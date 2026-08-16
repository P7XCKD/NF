## creata a file and write in file and using append
```c
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>

void main()
{
char data[100]= " testing " "random words" " is it working" ;
FILE *f;
f = fopen("test.txt","w");
printf("file created");
fputs(data,f);
fprintf(f,"\nappend working");
fclose(f);
}

```
### output:
![image](.attachments/18d81bebeea8446f13e031b3cb4905439f399807.png) 