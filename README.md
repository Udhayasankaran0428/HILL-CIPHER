
# EX. NO: 3 IMPLEMENTATION OF HILL CIPHER

## AIM:

To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B = 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To decrypt the message, each block is multiplied by the inverse of the m trix used for encryption. The matrix used for encryption is the cipher key, and it should be chosen randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user.

STEP-2: Split the plain text into groups of length three. 

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main(void){
    unsigned a[3][3]={{6,24,1},{13,16,10},{20,17,15}},
             b[3][3]={{8,5,10},{21,8,21},{21,12,8}};
    unsigned v[3]={0}, w[3]={0};
    char s[64];
    int i,j,t;

    printf("Plain letters: ");
    if(!fgets(s,sizeof s,stdin)) return 0;
    for(i=0;i<3;i++){
        char ch = toupper((unsigned char)(s[i]?s[i]:'A'));
        v[i] = (ch<'A'||ch>'Z') ? 0 : ch - 'A';
        printf("%u ", v[i]);
    }

    for(i=0;i<3;i++){ t=0; for(j=0;j<3;j++) t += a[i][j]*v[j]; w[i]=t%26; }
    printf("\nEncrypted:");
    for(i=0;i<3;i++) printf(" %c", (char)(w[i]+'A'));

    for(i=0;i<3;i++){ t=0; for(j=0;j<3;j++) t += b[i][j]*w[j]; v[i]=t%26; }
    printf("\nDecrypted:");
    for(i=0;i<3;i++) printf(" %c", (char)(v[i]+'A'));
    putchar('\n');
    return 0;
} 
```

## OUTPUT:
<img width="369" height="241" alt="image" src="https://github.com/user-attachments/assets/eb2d90f0-c664-481c-a137-fab6e3c7f496" />


## RESULT:
The program is executed successfully.
