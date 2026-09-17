## Ex. No : 3
## RECOGNITION OF A VALID ARITHMETIC EXPRESSION THAT USES
## Name : ASWIKA B
## Register Number : 212224220013

## AIM
To write a yacc program to recognize a valid arithmetic expression that uses operator +,- ,* and /.

## ALGORITHM
* Start the program.
* Write a program in the vi editor and save it with .l extension.
* In the lex program, write the translation rules for the operators =,+,-,*,/ and for the identifier.
* Write a program in the vi editor and save it with .y extension.
* Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
* Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
* Compile these with the C compiler as gcc lex.yy.c y.tab.c
* Enter an arithmetic expression as input and the tokens are identified as output.
  
## PROGRAM
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>

char expr[100];
int pos = 0;

int E();
int F();
void error();

int F() {
    if (isdigit(expr[pos])) {
        while (isdigit(expr[pos])) pos++;
        return 1;
    }
    else if (isalpha(expr[pos])) {
        while (isalnum(expr[pos])) pos++;
        return 1;
    }
    else if (expr[pos] == '(') {
        pos++;
        if (E()) {
            if (expr[pos] == ')') {
                pos++;
                return 1;
            }
        }
        return 0;
    }
    return 0;
}

int E() {
    if (!F()) return 0;
    while (expr[pos] == '+' || expr[pos] == '-' || expr[pos] == '*' || expr[pos] == '/') {
        pos++;
        if (!F())
            return 0;
    }
    return 1;
}

void error() {
    printf("\nError: Invalid arithmetic expression\n");
}

int main() {
    printf("Enter the expression:\n");
    fgets(expr, sizeof(expr), stdin);
    expr[strcspn(expr, "\n")] = '\0';
    pos = 0;
    if (E() && expr[pos] == '\0') {
        printf("\nValid arithmetic expression\n");
    } else {
        error();
    }
    return 0;
}
```
## OUTPUT
Valid Expression
<img width="1267" height="573" alt="image" src="https://github.com/user-attachments/assets/b3dba5e2-9b30-4450-b5c8-2ad3c499d4f1" />


Invalid Expression
<img width="1262" height="637" alt="image" src="https://github.com/user-attachments/assets/c3dc08d1-7ba3-440f-be5a-ba94daf5a9c2" />


## RESULT
A YACC program to recognize a valid arithmetic expression that uses operator +,-,* and / is executed successfully and the output is verified
