
DES Encryption and Decryption Program in C++

Overview

This C++ program implements the Data Encryption Standard (DES) algorithm, including encryption, decryption, and subkey generation. The program can take a 16-character hexadecimal plaintext or ciphertext and a 16-character hexadecimal key, then perform encryption or decryption based on the user's choice.

Features

Hexadecimal to Binary Conversion: Functions to convert hexadecimal values to binary and vice versa.
Binary to Decimal Conversion: Functions to convert binary values to decimal and vice versa.
Subkey Generation: Generates 16 subkeys required for the DES algorithm using circular left shifts and permutation tables.
DES Algorithm Implementation: Performs DES encryption and decryption, including initial and final permutations, expansion, substitution using S-boxes, and permutation functions.
How to Compile and Run

Compilation
To compile the program, navigate to the directory containing the encrypt.cpp file and run the following command in the terminal:

bash
Copy code
g++ -o encrypt encrypt.cpp
Running the Program
You can run the program by executing the compiled file:

bash
Copy code
./encrypt
Alternatively, if you are using Visual Studio Code, you can compile and run the program by pressing the play button in the top right corner of the editor.

Program Explanation

Key Components
Initial Permutation (IP) Table: Reorders the bits of the input plaintext.
Inverse Initial Permutation (IP Inverse) Table: Reorders the bits of the output ciphertext to its final form.
Expansion Table: Expands the 32-bit right half of the plaintext to 48 bits.
Permutation Function (P) Table: Reorders the bits after the S-box substitution.
Substitution Boxes (S-boxes): Performs a non-linear substitution on the expanded 48-bit input.
Key Permutation Tables (PC1 and PC2): Used for generating the subkeys from the main key.
Left Shifts: Functions to perform circular left shifts on the key halves.
Subkey Generation
The 64-bit key is first converted to binary and then permuted using PC1 to produce a 56-bit key.
The 56-bit key is split into two 28-bit halves, which are then shifted and recombined to form 16 subkeys.
Each subkey is permuted using PC2 to produce the final 48-bit subkeys.
DES Algorithm
Encryption

Convert the 16-character hexadecimal plaintext to a 64-bit binary number.
Apply the initial permutation (IP) to the plaintext.
Split the permuted plaintext into two 32-bit halves.
Perform 16 rounds of the following operations:
Expand the right half to 48 bits using the expansion table.
XOR the expanded right half with the subkey for the current round.
Substitute the result using the S-boxes.
Permute the substituted result using the permutation function table.
XOR the permuted result with the left half of the plaintext.
Swap the left and right halves.
Combine the left and right halves.
Apply the inverse initial permutation (IP Inverse) to produce the final ciphertext.
Convert the binary ciphertext to hexadecimal and display it.
Decryption

The process for decryption is similar to encryption, with the subkeys applied in reverse order.
User Input
The user is prompted to choose between encryption and decryption.
The user inputs a 16-character hexadecimal plaintext or ciphertext and a 16-character hexadecimal key.
The program validates the input length and proceeds with the selected operation.
Error Handling
If the user inputs a key or plaintext/ciphertext with a length other than 16 characters, an error message is displayed.
Example Usage

bash
Copy code
 would you like to perform encryption or decryption (input E to encrypt or D to decrypt) -- E
 Enter a 16 character hexadecimal plaintext or cipherText -- 0123456789ABCDEF
 Enter a 16 character hexadecimal key -- AABB09182736CCDD

The cipherText produced from the given key and plaintext is -- <cipherText>
