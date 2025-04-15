# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# Register Number :
# Date : 
# AIM :
## To write a C program to implement a symbol table.
# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol and memory address are inserted into the symbol table.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and the symbol table has been checked for the corresponding variable, the variable along with its address is displayed as a result.
8.	Stop the program. 
# PROGRAM
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>
#define MAX_EXPRESSION_SIZE 100
#define MAX_SYMBOLS 15
int main() {
    int i = 0, x = 0, n;
    void *add[MAX_SYMBOLS];
    char b[MAX_EXPRESSION_SIZE], d[MAX_SYMBOLS], c, srch;
    int found = 0;
    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0';
    n = i - 1;
    printf("\nGiven Expression: %s\n", b);
    printf("\nSymbol Table\n");
    printf("Symbol\tAddress\t\tType\n");
    for (int j = 0; j <= n && x < MAX_SYMBOLS; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            int alreadyExists = 0;
            for (int k = 0; k < x; k++) {
                if (d[k] == c) {
                    alreadyExists = 1;
                    break;
                }
            }
            if (!alreadyExists) {
                void *p = malloc(sizeof(char));
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }
    while (getchar() != '\n'); 
    printf("\nEnter the symbol to be searched: ");
    srch = getchar();
    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("\n✅ Symbol Found!\n");
            printf("%c @ address %p\n", srch, add[i]);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("\nSymbol Not Found!\n");
    }
    for (i = 0; i < x; i++) {
        free(add[i]);
    }
    printf("\nPress Enter to exit...");
    while (getchar() != '\n'); // Wait for Enter key
    getchar();
    return 0;
}
```
# OUTPUT
## SYSTEM FOUND
![Screenshot 2025-04-15 111422](https://github.com/user-attachments/assets/06264751-d03e-48f7-8293-692d30485537)
## SYSTEM NOT FOUND
![Screenshot 2025-04-15 111510](https://github.com/user-attachments/assets/5c473e13-d044-4e7c-bef9-a68b78e477a2)

# RESULT
### The program to implement a symbol table is executed and the output is verified.
