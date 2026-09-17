## Ex. No : 6
## IMPLEMENTATION OF THE BACK END OF THE COMPILER
## Name : ASWIKA B
## Register Number : 212224220013

## AIM
To write a program to implement the back end of the compiler.

## ALGORITHM
* Start the program.
* Get the three variables from statements and stored in the text file k.txt.
* Compile the program and give the path of the source file.
* Execute the program.
* Target code for the given statement is produced.
* Stop the program.
  
## PROGRAM
```
#include <stdio.h>
#include <string.h>

// Define a structure for a simple IR instruction
typedef struct {
    char opcode[10]; // Operation code (e.g., ADD, MOV)
    char arg1[10];   // First argument (register or variable)
    char arg2[10];   // Second argument (register or variable)
    char result[10]; // Result variable
} Instruction;

// Function to generate pseudo-assembly from the IR
void generate_code(Instruction ir[], int count) {
    printf("Generated Assembly:\n");
    for (int i = 0; i < count; i++) {
        if (strcmp(ir[i].opcode, "ADD") == 0) {
            printf("    ADD %s, %s ; Store in %s\n", ir[i].arg1, ir[i].arg2, ir[i].result);
        } else if (strcmp(ir[i].opcode, "SUB") == 0) {
            printf("    SUB %s, %s ; Store in %s\n", ir[i].arg1, ir[i].arg2, ir[i].result);
        } else if (strcmp(ir[i].opcode, "MOV") == 0) {
            printf("    MOV %s, %s\n", ir[i].arg1, ir[i].result);
        } else {
            printf("Unknown operation: %s\n", ir[i].opcode);
        }
    }
}

int main() {
    // Define a simple list of IR instructions
    Instruction ir[] = {
        {"MOV", "R1", "", "A"},    // MOV R1 to A
        {"ADD", "A", "B", "R2"},   // ADD A and B, store in R2
        {"SUB", "R2", "C", "R3"},  // SUB R2 and C, store in R3
        {"MOV", "R3", "", "D"}     // MOV R3 to D
    };
    
    int ir_count = sizeof(ir) / sizeof(Instruction);
    
    // Generate the assembly-like code from the IR
    generate_code(ir, ir_count);
    
    return 0;
}
```
## OUTPUT
<img width="482" height="375" alt="image" src="https://github.com/user-attachments/assets/cc265ce1-158f-4c89-b3ec-00f2a8fb65fa" />

## RESULT
The back end of the compiler is implemented successfully, and the output is verified.
