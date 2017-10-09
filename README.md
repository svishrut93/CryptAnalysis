# CryptAnalysis #
<h1> Problem Introduction</h1>

The problem described is a variation of the hill cipher: A polygraphic substitution cipher based on linear algebra.</br>
The author modifies the hill cipher in the following ways and calls it the “Hilly Cipher”</br>
   --> Modify the substitution table for plaintext characters(A-Z) , so that it is an addicted to the key.</br>
   -->The conventional hill cipher provides inverse modulo 26, which is used while solving linear equations during decryption.</br> To circumvent this, the author chooses a key, for which determinant of inverse mod 26 does not exist.
The author provides a plain text and cipher text pair (P1, C1).</br>

![alt text](https://github.com/svishrut93/CryptAnalysis/blob/master/Captures/cipher1.PNG)

![alt text](https://github.com/svishrut93/CryptAnalysis/blob/master/Captures/plain%20text%201.PNG)

Cipher text C2: </br>

![alt text](https://github.com/svishrut93/CryptAnalysis/blob/master/Captures/cipher%20text%20c2.PNG)

Other hints about the problem :</br>
• Both cipher texts C1 and C2 are encrypted with the same keys.</br>
• Cipher text C1 is not part of cipher text C2.</br>
The author also provides an additional lookup table with 11 characters ( *, #, &, %, $, +, ?, !, @, ^, - ).</br>
This table is rotated and is used as a substitution table for numbers during encryption.</br>

![alt text](https://github.com/svishrut93/CryptAnalysis/blob/master/Captures/Table.PNG)

<h1>Encryption procedure : </h1>
• Key is chosen as an invertible n*n matrix. K with n >= 5 , or n = 6 by default.</br>
• K must follow the condition gcd (det(K), 26) != 1.</br>
• Compute s = sum of elements of main diagonal of key (K)</br>
-->If s = 0 , then s = sum of elements of secondary diagonal.</br>
-->If this is also 0 then : Generate new key matrix.</br>
• Compute substitution table Tp as</br>
A = 1* s</br>
B = 2*s</br>
C= 3*s</br>
.</br>
.</br>
.</br>
Z = 26 * s</br>
• Divide plain text into blocks of n(6) characters .</br>
• Replace plain text with numbers using substitution table in Tp. This results in a plaintext number vector . P</br>
• Multiply K and P to get vector : C1 = K * P</br>
• Compute vector for cipher text C = C1 mod 26</br>
• Substitute elements of C like A = 1 ; B = 2 ; C= 3 and so onn.</br>
• Compute an extension vector X as</br>
X = upper bound(C1 / 26 )</br>
• Construct an extension matrix E as</br>
E = s* I + k</br>
• Compute the encrypted extension as Xenc = E * X</br>
• Append all the cipher letters with the encrypted extensions.</br>
• C1 XEnc1 ... C6 XEnc6</br>
• Define the additional symbols used for substituting digits as the following table</br>

![alt text](https://github.com/svishrut93/CryptAnalysis/blob/master/Captures/Table2.PNG)

• Compute sum “t“ of all elements of key matrix K .</br>
• Upon this result rotate the above substitution table .</br>
Eg: t mod 11 = 6</br>
Shift table 6 times to right</br>

![alt text](https://github.com/svishrut93/CryptAnalysis/blob/master/Captures/Table3.PNG)


• Substitute XEnc using the substitution table TA. So you get XEncSym.</br>
• Send C1 XEncSym …….C6 XEncSym as cipher text to recipient.</br>
