## Ex. No : 1
## IMPLEMENTATION OF SYMBOL TABLE
## Register Number : 212224220013

## AIM:
To write a C program to implement a symbol table.

## ALGORITHM:
* Start the program.
* Get the input from the user with the terminating symbol ‘$’.
* Allocate memory for the variable by dynamic memory allocation function.
* If the next character of the symbol is an operator then only the memory is allocated.
* While reading, the input symbol is inserted into symbol table along with its memory address.
* The steps are repeated till ‘$’ is reached.
* To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
* Stop the program.

## PROGRAM:
```
    #include <stdio.h>
    #include <stdlib.h>
    #include <ctype.h>
    #include <string.h>
    
    #define MAX_EXPRESSION_SIZE 100
    
    int main() {
        int i = 0, j = 0, x = 0, n;
        void *add[20];   // store addresses
        char b[MAX_EXPRESSION_SIZE], d[20], c;
    
        printf("Enter the Expression terminated by $: ");
        while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
            b[i++] = c;
        }
        b[i] = '\0';   // Null terminate
        n = i - 1;
    
        printf("Given Expression: %s\n", b);
    
        printf("\nSymbol Table\n");
        printf("Symbol\taddr\ttype\n");
    
        for (j = 0; j <= n; j++) {
            c = b[j];
            if (isalpha((unsigned char)c)) {
                if (j == n) {
                    void *p = malloc(sizeof(char));
                    add[x] = p;
                    d[x] = c;
                    printf("%c\t%p\tidentifier\n", c, p);
                    x++;
                } else {
                    char ch = b[j + 1];
                    if (ch == '+' || ch == '-' || ch == '*' || ch == '=' || ch == '/' || ch == ';') {
                        void *p = malloc(sizeof(char));
                        add[x] = p;
                        d[x] = c;
                        printf("%c\t%p\tidentifier\n", c, p);
                        x++;
                    }
                }
            }
        }
    
        return 0;
    }
```
## OUTPUT:
<img width="821" height="467" alt="image" src="https://github.com/user-attachments/assets/70441581-18fd-48ba-9f54-ad143d5350d5" />

## RESULT:
The program to implement a symbol table is executed and the output is verified.

