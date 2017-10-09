# CryptAnalysis #
<h1> Problem Introduction<h1>

The problem described is a variation of the hill cipher: A polygraphic substitution cipher based on linear algebra.
The author modifies the hill cipher in the following ways and calls it the “Hilly Cipher”
   --> Modify the substitution table for plaintext characters(A-Z) , so that it is an addicted to the key.
   -->The conventional hill cipher provides inverse modulo 26, which is used while solving linear equations during decryption. To circumvent this, the author chooses a key, for which determinant of inverse mod 26 does not exist.
The author provides a plain text and cipher text pair (P1, C1)
