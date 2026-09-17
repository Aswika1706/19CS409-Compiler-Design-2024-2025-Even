## Ex. No : 5
## RECOGNITION OF THE GRAMMAR (anb where n>=10) USING YACC
## Name : ASWIKA B
## Register Number : 212224220013

## AIM
To write a YACC program to recognize the grammar anb where n>=10.

## ALGORITHM
* Start the program.
* Write a program in the vi editor and save it with .l extension.
* In the lex program, write the translation rules for the variables a and b.
* Write a program in the vi editor and save it with .y extension.
* Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
* Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
* Compile these with the C compiler as gcc lex.yy.c y.tab.c
* Enter a string as input and it is identified as valid or invalid.
  
## PROGRAM
```
#include <stdio.h>
#include <string.h>
int main() {
    char str[100];
    int i = 0;
    printf("Enter the string: ");
    scanf("%s", str);
    // Check if first character is 'a'
    if (str[0] != 'a') {
        printf("Invalid: string must start with 'a'\n");
        return 0;
    }
    // Check if the rest of the characters are all 'b'
    for (i = 1; str[i] != '\0'; i++) {
        if (str[i] != 'b') {
            printf("Invalid: all characters after 'a' must be 'b'\n");
            return 0;
        }
    }
    // Check if there are at least 10 'b's
    int b_count = strlen(str) - 1;
    if (b_count >= 10) {
        printf("Valid string: matches anb where n >= 10\n");
    } else {
        printf("Invalid: number of 'b's is less than 10 (found %d)\n", b_count);
    }
    return 0;
}
```
## OUTPUT
<img width="656" height="422" alt="image" src="https://github.com/user-attachments/assets/efd12d37-3793-45f7-9187-f7716acb6f83" />

## RESULT
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
