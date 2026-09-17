# Ex. No : 4	
# RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
# Name: ASWIKA B
## Register Number : 212224220013


## AIM   
To write a YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits.

## ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the keywords int, float and double and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with YACC compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a statement as input and the valid variables are identified as output.

## PROGRAM
variable_test.l
```
%{
#include "variable_test.tab.h"
%}

%%
"int"     { return INT; }
"float"   { return FLOAT; }
"double"  { return DOUBLE; }
","       { return ','; }
";"       { return ';'; }
[a-zA-Z][a-zA-Z0-9]* { printf("\nIdentifier is %s", yytext); return ID; }
[ \t\r\n]     { /* skip whitespace and newlines */ }
.         { /* ignore unrecognized characters */ }
%%

int yywrap() { return 1; }
```
variable_test.y
```
%{
#include <stdio.h>
%}
%token ID INT FLOAT DOUBLE
%%
D : T L ';'    { printf("Valid Declaration\n"); }
  ;
L : L ',' ID   | ID
  ;
T : INT | FLOAT | DOUBLE
  ;
%%
extern FILE *yyin;
int main() {
    do {
        yyparse();
    } while (!feof(yyin));
    return 0;
}
void yyerror(char *s) { fprintf(stderr, "Error: %s\n", s); }
```

## OUTPUT 

<img width="389" height="205" alt="Screenshot 2025-11-21 103124" src="https://github.com/user-attachments/assets/cf1e5d80-752b-494b-988c-31143df89c34" />

## RESULT
A  YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.
