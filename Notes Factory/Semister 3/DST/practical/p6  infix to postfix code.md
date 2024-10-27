```c
#include <stdio.h>
#include <string.h>

int question(char c)
{
    if (c == '^')
        return 3;
    else if (c == '/' || c == '*')
        return 2;
    else if (c == '+' || c == '-')
        return 1;
    else
        return -1;
}

char direction(char c) {
    if (c == '^')
        return 'R';
    return 'L';
}

void infix_to_postfix(char s[], char result[])
{
    int resultindex = 0;
    int len = strlen(s);
    char storage[1000];
    int storageindex = -1;

    for (int i = 0; i < len; i++)
        {
        char symbol = s[i];

        if ((symbol >= 'a' && symbol <= 'z') || (symbol >= 'A' && symbol <= 'Z') || (symbol >= '0' && symbol <= '9'))
        {
            result[resultindex++] = symbol;
        }
        else if (symbol == '(')
        {
            storage[++storageindex] = symbol;
        }
        else if (symbol == ')')
            {
            while (storageindex >= 0 && storage[storageindex] != '(') {
                result[resultindex++] = storage[storageindex--];
            }
            storageindex--;
        } else {
            while (storageindex >= 0 && (question(s[i]) < question(storage[storageindex]) ||
            (question(s[i]) == question(storage[storageindex]) && direction(s[i]) == 'L')))
            {
                result[resultindex++] = storage[storageindex--];
            }
            storage[++storageindex] = symbol;
        }
    }

    while (storageindex >= 0)
    {
        result[resultindex++] = storage[storageindex--];
    }

    result[resultindex] = '\0';
}

int main()
 {
    char exp[] = "a+b(c*d)(f-g)+h";
    char result[1000];

    infix_to_postfix(exp, result);

    printf("Postfix expression: %s\n", result);

    return 0;
}
