## Read a file by opening it
```c
#include <stdio.h>

int main() {

    FILE *fp = fopen("a.txt", "r");
    char ch;

    while ((ch = fgetc(fp)) != EOF) {
        printf("%c", ch);
    }

    fclose(fp);
    return 0;
}

```

#### Output 

**Case 1: File does not exist**
The file is not opened. The program will exit now

**Case 2: File exists with content "Hello"**
The file is created Successfully.
***

## Write a file:
```c
#include <stdio.h>

int main()
{
    FILE *fp = fopen("a.txt", "w");

    fprintf(fp, "Hello World");

    fclose(fp);

    return 0;
}
```
#### Output
<non-zero value>The file is created Successfully.

(Appends "\n Some text3" to E: \file1.txt)
***
## Copying text of a file to another file:

```c
#include <stdio.h>

int main() {
    FILE *fp1 = fopen("a.txt", "r");
    FILE *fp2 = fopen("b.txt", "w");
    char ch;

    while ((ch = fgetc(fp1)) != EOF) {
        fputc(ch, fp2);
    }

    fclose(fp1);
    fclose(fp2);

    return 0;
}
```
#### output 

Enter the filename to open for reading

input.txt

Enter the filename to open for writing output.txt

Contents copied to output.txt
***