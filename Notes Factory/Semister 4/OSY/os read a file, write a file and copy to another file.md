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
#include <stdlib.h> // For exit()

int main()
{
    FILE *fptr1, *fptr2;
    char filename[100], c;

    printf("Enter the filename to open for reading \n");
    scanf("%s", filename);

    // Open one file for reading
    fptr1 = fopen(filename, "r");
    if (fptr1 == NULL)
    {
        printf("Cannot open file %s \n", filename);
        exit(0);
    }

    printf("Enter the filename to open for writing \n");
    scanf("%s", filename);

    // Open another file for writing
    fptr2 = fopen(filename, "w");
    if (fptr2 == NULL)
    {
        printf("Cannot open file %s \n", filename);
        exit(0);
    }

    // Read contents from file
    c = fgetc(fptr1);
    while (c != EOF)
    {
        fputc(c, fptr2);
        c = fgetc(fptr1);
    }

    printf("\nContents copied to %s", filename);

    fclose(fptr1);
    fclose(fptr2);
    return 0;
}

```
#### output 

Enter the filename to open for reading

input.txt

Enter the filename to open for writing output.txt

Contents copied to output.txt
***