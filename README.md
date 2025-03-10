# Ex. No : 1

# IMPLEMENTATION OF SYMBOL TABLE

#NAME : GOPIKRISHNAN M
# Register Number :212223043004


# Date :10-03-2025

# AIM:

To write a C program to implement a symbol table.

# ALGORITHM:

1. Start the program.
2. Get the input from the user with the terminating symbol ‘$’.
3. Allocate memory for the variable by dynamic memory allocation function.
4. If the next character of the symbol is an operator then only the memory is allocated.
5. While reading, the input symbol is inserted into symbol table along with its memory address.
6. The steps are repeated till ‘$’ is reached.
7. To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8. Stop the program.

# PROGRAM:

#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    char b[MAX_EXPRESSION_SIZE], d[15], c, srch;
    
    // Array to store the addresses (though here we can just store characters)
    void *add[15]; // Increase the size of add array to match symbol count
    
    printf("Enter the Expression terminated by $: ");
    
    // Read the expression
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; // Null terminate the string
    n = i - 1;

    printf("Given Expression: %s\n", b);

    // Print the symbol table header
    printf("\nSymbol Table\n");
    printf("Symbol\taddr\t\ttype\n");

    // Parse the expression and construct the symbol table
    for (j = 0; j <= n; j++) {
        c = b[j];
        
        // If the character is an alphabet, treat it as an identifier
        if (isalpha((unsigned char)c)) {
            // If it's the last character, we need to add it
            if (j == n || !isalpha((unsigned char)b[j + 1])) {
                add[x] = &b[j]; // Store the address of the character in the symbol table
                d[x] = c; // Store the character itself
                printf("%c\t%p\tidentifier\n", c, add[x]);
                x++;
            }
        }
        
        // Handle operators (+, -, *, =)
        else if (c == '+' || c == '-' || c == '*' || c == '=') {
            add[x] = &b[j]; // Store the address of the operator
            d[x] = c; // Store the operator
            printf("%c\t%p\toperator\n", c, add[x]);
            x++;
        }
    }

    // Search for a symbol in the symbol table
    printf("\nThe symbol to be searched: ");
    getchar(); // To capture the newline character after previous input
    srch = getchar();

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c@address%p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (flag == 0) {
        printf("Symbol Not Found\n");
    }

    return 0;
}

# OUTPUT:

![Screenshot (65)](https://github.com/user-attachments/assets/f393bc94-a1d7-4c10-8fb8-b1744c7ca966)
![Screenshot (66)](https://github.com/user-attachments/assets/43e98a97-e49f-4d34-b3f5-4d70b2cb95fc)



# RESULT:

The program to implement a symbol table is executed and the output is verified.
