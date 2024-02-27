# Cryptography---19CS412-classical-techqniques


# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To develop a simple C program to implement Caeser Cipher.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <string.h>

int main()
{
    int i, key;
    char s[1000];

    printf("Enter a plaintext to encrypt:\n");
    fgets(s, sizeof(s), stdin);
    printf("Enter key:\n");
    scanf("%d", &key);

    int n = strlen(s);

    for (i = 0; i < n; i++) 
    {
        char c = s[i];

        if (c >= 'a' && c <= 'z')
        {
            s[i] = 'a' + (c - 'a' + key) % 26;
        } 
        else if (c >= 'A' && c <= 'Z')
        {
            s[i] = 'A' + (c - 'A' + key) % 26;
        }
    }

    printf("Encrypted message: %s\n", s);

    return 0;
}
```

## OUTPUT:
![image](https://github.com/praveenvenkatt/Cryptography---19CS412-classical-techqniques/assets/119560117/3e844049-0ce9-4409-a354-30bf666ddc5b)


## RESULT:
The program is executed successfully

---------------------------------

# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To develop a simple C program to implement PlayFair Cipher.

## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:

## OUTPUT:

## RESULT:
The program is executed successfully


---------------------------

# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>

int main() 
{
    unsigned int key[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}};
    unsigned int inverseKey[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};

    char msg[4];
    unsigned int enc[3] = {0}, dec[3] = {0};

    printf("Enter plain text: ");
    scanf("%3s", msg);

    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            enc[i] += key[i][j] * (msg[j] - 'A') % 26;

    printf("Encrypted Cipher Text: %c%c%c\n", enc[0] % 26 + 'A', enc[1] % 26 + 'A', enc[2] % 26 + 'A');

    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            dec[i] += inverseKey[i][j] * enc[j] % 26;

    printf("Decrypted Cipher Text: %c%c%c\n", dec[0] % 26 + 'A', dec[1] % 26 + 'A', dec[2] % 26 + 'A');

    return 0;
}
```
## OUTPUT:
![image](https://github.com/praveenvenkatt/Cryptography---19CS412-classical-techqniques/assets/119560117/24ddc7f8-9420-4f61-ab00-90d62c3676c1)

## RESULT:
The program is executed successfully

-------------------------------------------------

# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple C program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define MAX_LENGTH 100

int main() 
{
    char input[MAX_LENGTH];
    char key[MAX_LENGTH];
    char result[MAX_LENGTH];

    printf("Enter the text to encrypt: ");
    fgets(input, MAX_LENGTH, stdin);
    input[strcspn(input, "\n")] = '\0'; 

    printf("Enter the key: ");
    fgets(key, MAX_LENGTH, stdin);
    key[strcspn(key, "\n")] = '\0'; 

    int inputLength = strlen(input);
    int keyLength = strlen(key);

    for (int i = 0, j = 0; i < inputLength; ++i) 
    {
        char currentChar = input[i];

        if (isalpha(currentChar))
        {
            int shift = toupper(key[j % keyLength]) - 'A';
            int base = isupper(currentChar) ? 'A' : 'a';

            result[i] = ((currentChar - base + shift + 26) % 26) + base;
            ++j;
        }
        else
        {
            result[i] = currentChar;
        }
    }

    result[inputLength] = '\0';
    printf("Encrypted text: %s\n", result);

    for (int i = 0, j = 0; i < inputLength; ++i) 
    {
        char currentChar = result[i];

        if (isalpha(currentChar)) 
        {
            int shift = toupper(key[j % keyLength]) - 'A';
            int base = isupper(currentChar) ? 'A' : 'a';

            result[i] = ((currentChar - base - shift + 26) % 26) + base;
            ++j;
        }
    }

    result[inputLength] = '\0';
    printf("Decrypted text: %s\n", result);

    return 0;
}
```

## OUTPUT:
![image](https://github.com/praveenvenkatt/Cryptography---19CS412-classical-techqniques/assets/119560117/608e85b7-31e5-4808-95a3-e58faadfe118)


## RESULT:
The program is executed successfully

-----------------------------------------------------------------------

# Rail Fence Cipher
Rail Fence Cipher using with different key values

# AIM:

To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <string.h>

#define MAX_LENGTH 100

int main()
{
    char input[MAX_LENGTH];
    char encrypted[MAX_LENGTH];
    int rails;

    printf("Enter the text to encrypt: ");
    fgets(input, MAX_LENGTH, stdin);
    input[strcspn(input, "\n")] = '\0'; 

    printf("Enter the number of rails: ");
    scanf("%d", &rails);
    getchar(); 

    int inputLength = strlen(input);
    int cycle = 2 * (rails - 1);
    int k = 0;

    for (int i = 0; i < rails; ++i)
    {
        for (int j = i; j < inputLength; j += cycle) 
        {
            encrypted[k++] = input[j];
            if (i != 0 && i != rails - 1 && j + cycle - 2 * i < inputLength)
            {
                encrypted[k++] = input[j + cycle - 2 * i];
            }
        }
    }
    encrypted[inputLength] = '\0';

    printf("Encrypted text: %s\n", encrypted);

    return 0;
}
```

## OUTPUT:
![image](https://github.com/praveenvenkatt/Cryptography---19CS412-classical-techqniques/assets/119560117/936238e3-37fe-46e0-b637-be3e87f380cb)


## RESULT:
The program is executed successfully
