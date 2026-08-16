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
