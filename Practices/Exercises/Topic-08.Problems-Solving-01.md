# Problems Solving
__________________________

> ### 1. Caesars Cipher

One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function which takes a ROT13 encoded string as input and returns a decoded string.

All letters will be uppercase. Do not transform any non-alphabetic character (i.e.spaces, punctuation), but do pass them on.

``` javascript
function rot13(str) {
    return str;
}
rot13("PUNEVMNEQ"); //
```


> ### 2. Playfair Cipher
The Playfair cipher is a substitution cipher that uses digraphs (pairs of letters) instead of single letters, and makes use of symmetrical encryption.

There are some variations on the rules of encipherment. One version of the cipher rules is outlined below:

A 5x5 Polybius square is constructed, deranged with a keyword.
keyword = python
First, fill in the keyword at the top of the grid, omitting any duplicates (3rd example's keyword has two occurrences of "h". The second one should be omitted).
|   |   |   |   |   |
|---|---|---|-- |---|
|P	|Y	|T	|H	|O  |
|N  |   |   |   |   |				

Next, fill in the rest of the slots with the leftover letters of the alphabet that are not in the keyword. Classically, "I" and "J" share a slot (some people elect to omit "Q", "V", or "Z" instead).

|   |   |   |   |   |
|---|---|---|-- |---|
|P	|Y	|T	|H	|O  |
|N  |A  |B  |C  |D  |	
|E	|F	|G	|I/J|K  |
|L	|M	|Q	|R	|S  |
|U	|V	|W	|X	|Z  |

Remove spaces and punctuation from the message to be enciphered. Then break it up into two-letter chunks (digraphs):  
```js
message = "Tomorrow we attack."

message = "tomorrowweattack"

message = "to mo rr ow we at ta ck"
```

Digraphs must have two distinct letters. If any digraph consists of the same letter, insert an "x" between them and shift the pairings to the right. Repeat as necessary until all double letters are eliminated. If the resulting message has an odd number of letters, add an "x" to the end.  
```js
message = "to mo rx ro ww ea tt ac k"
```

Note how shifting the pairings rightward after inserting an 'x' after the first 'r' has created two more double letter digraphs. Correct them sequentially.
```js
message = "to mo rx ro wx we at ta ck"
```
This insertion corrected both double letter digraphs, and evened out the message length. No more changes are necessary.

Encipher each digraph into a different digraph by following these 3 rules of encipherment:  

If the two letters are on the same row, as is the case for the first digraph "to", replace each letter with the letter to its right, wrapping around to the beginning of the row if necessary.

`to -> hp `

If the two letters are on the same column, as in the third digraph "rx", replace each letter with the letter beneath it, wrapping around to the top if necessary

`rx -> xh`

If the two letters have dissimilar rows and columns, as in the second digraph "mo", visualise a rectangle with these letters at opposite vertices, then find the other two vertices. Replace each letter with the vertex sharing its row. The original letters are rendered in bold below. The cipher letters are italicised and bolded.

|   |   |   |   |   |
|---|---|---|-- |---|
|P	|Y	|T	|H	|O  |
|N  |A  |B  |C  |D  |	
|E	|F	|G	|I/J|K  |
|L	|M	|Q	|R	|S  |
|U	|V	|W	|X	|Z  |

`mo -> sy`

"to mo rx ro wx we at ta ck" -> "hp sy xh sh xz ug by yb di"

Create a function that takes `two strings` — a plaintext message or ciphertext `str`, and a keyword — and returns the corresponding ciphertext or deciphered plaintext (without spaces and with "x" in odd places as appropriate).

```js
playfair("Tomorrow we attack.", "python") ➞ "HPSYXHSHXZUGBYYBDI"

playfair("HPSYXHSHXZUGBYYBDI", "python") ➞ "TOMORXROWXWEATTACK"

playfair("MYDZABIFBMENFEQAAE", "rhythm") ➞ "THEXEAGLEHASLANDED"
```

> ### 3. Polybius Square (Basic)
The Polybius Square cipher is a simple substitution cipher that makes use of a 5x5 square grid. The letters A-Z are written into the grid, with "I" and "J" typically sharing a slot (as there are 26 letters and only 25 slots).

|   |1  |2  |3  |4	|5  |  
|---|---|---|---|---|---|
|1	|A	|B	|C	|D	|E  |
|2	|F	|G	|H	|I/J|K  |
|3	|L	|M	|N	|O	|P  |
|4	|Q	|R	|S	|T	|U  |
|5	|V	|W	|X	|Y	|Z  |


To encipher a message, each letter is merely replaced by its row and column numbers in the grid.

Create a function that takes a plaintext or ciphertext message, and returns the corresponding ciphertext or plaintext.

```js
polybius("Hi") ➞ "2324"

polybius("2324  4423154215") ➞ "hi there"

polybius("543445 14343344 522433 21422415331443 52244423 4311311114") ➞ "you dont win friends with salad"
```

Hint:   
As "I" and "J" share a slot, both are enciphered into 24, but deciphered only into "I" (see third and fourth test).


> ### 4. Affine Cipher Encrypt

Create a function that takes a string of plain text (English alphabet) all in lowercase, encryption function, and converts the plain text into ciphertext using the affine encryption function.

Encryption Function  

In the affine cipher, the letters of an alphabet of size m are first mapped to the integers in the range 0 … m − 1. It then uses modular arithmetic to transform the integer that each plaintext letter corresponds to into another integer that corresponds to a ciphertext letter.

The encryption function for a single letter is `E(x)=(ax+b)mod m` where modulus m is the size of the alphabet and a and b are the keys of the cipher. The value a must be chosen such that a and m are coprime.

The alphabet is going to be the letters a through z and will have the corresponding values a=0, b=1, c=2, d=3 ... z=25.

```js
affineEncrypt("salakpur", "(x+2)%26") ➞ "ucncmrwt"
// a = 1 , b = 2
// Encryption function = "(x+2)%26"
// gcd(1, 26) = 1
// Therefore, we apply the encryption function for the letters.

affineEncrypt("dang", "(2x+7)%26") ➞ "2 and 26 are not coprime"
// a = 2, b = 26
// gcd(2, 26) = 2
```
Hint: 
For the problem 1 =< a <= 11 , 1 =< b <= 9 , m = 26
Create your own gcd function.

> ### 5.Affine Cipher Decrypt

Create a function that takes a `string of ciphertext` (English alphabet) all in lowercase, encryption function, and converts it into plain text using the affine decryption function.

***Decryption Function***
In the affine cipher, the letters of an alphabet of size m are first mapped to the integers in the range `0 … m − 1.` It then uses modular arithmetic to transform the integer that each plaintext letter corresponds to into another integer that corresponds to a ciphertext letter. The encryption function for a single letter is `E(x)=(ax+b)mod m` where modulus m is the size of the alphabet and a and b are the keys of the cipher. The value a must be chosen such that a and m are coprime.

The decryption function is `D(x)=a^(-1)*(x-b)mod m` where `a^(-1)` is the modular multiplicative inverse of `a modulo m` ie `a * a^(-1) mod m == 1`. The multiplicative inverse of a only exists if a and m are coprime. Hence without the restriction on a, decryption might not be possible.

The alphabet is going to be the letters a through z and will have the corresponding values `a=0, b=1, c=2, d=3 ... z=25.`

```js
affineDecrypt("ucncmrwt", "(x+2)%26") ➞  "salakpur"
// a = 1, b = 2, encryption = "(x+2)%26".
// Modular Multiplicative Inverse of 1 =  1.
// We apply the decryption function for the letters.

affineDecrypt("hezmrc", "(3x+4)%26") ➞  "bahuni"
// a = 3, b = 4, encryption = "(x+2)%26".
// Modular Multiplicative Inverse of 3 = 9.
// We apply the decryption function for the letters.
```
Notes    
For the problem 1 =< a <= 11 , 1 =< b <= 9 , m = 26


> ### 6. Vigenere Cipher
The Vigenere Cipher is a poly-alphabetic substitution cipher that uses a set of shift ciphers and a keyword.

One of the simplest ciphers is the Caesar/shift cipher, where each letter in the plaintext message is replaced by the letter a particular number of positions up, or downstream in the alphabet. Shift 1 Caesar cipher:

A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z   
B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A   

The Vigenere table is generated by doing a shift-1 Caesar cipher as many times as the number of letters in the alphabet (English alphabet, for this challenge).

A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z   
B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A  
C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B   
D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C   
E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D   
F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E   
G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F   
H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G   
I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H   
J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I   
K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J   
L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K  
M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L   
N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M   
O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N   
P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O   
Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P   
R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q   
S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R   
T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S    
U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T   
V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U   
W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V   
X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W   
Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X   
Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y   

To encipher the message, first, spaces and punctuation are removed to create the plaintext. All characters are transformed to uppercase to match the table:

message = "Soylent Green is people."

plaintext = "SOYLENTGREENISPEOPLE"
A keyword is chosen, in this case, "spoiler" and repeated as many times as necessary to match the length of the plaintext:

key = "SPOILERSPOILERSPOILE"
The last "r" is dropped as the plaintext length has been reached.

The plaintext and key are lined up. To encipher the 1st letter, a search is done across the first row to find the column of the plaintext letter, in this case "S", in the 19th column. Then a search is done down the first column to locate the row of the 1st key letter, in this case also "S", in the 19th row. The letter at the intersection between column 19 and row 19, "K", will be the 1st letter in the ciphertext.

The 2nd plaintext letter "O" is at column 15, while the 2nd key letter "P" is at row 16. The letter at the intersection is "D". And so on.

|Plaintext      |	S	O	Y	L	E	N	T	G	R	E	E	N	I	S	P	E	O	P	L	E|
|---------------|--------------------------------------------------------------------------------|
|Key            |	S	P	O	I	L	E	R	S	P	O	I	L	E	R	S	P	O	I	L	E|
|Ciphertext     |	K	D	M	T	P	R	K	Y	G	S	M	Y	M	J	H	T	C	X	W	I|

Create a function that takes two strings: a message or ciphertext, and a keyword. Return the ciphertext if the input is a message, or the deciphered text (without spaces or punctuation) if the input is in ciphertext.

```js
vigenere("Soylent Green is people.", "spoiler") ➞ "KDMTPRKYGSMYMJHTCXWI"

vigenere("Darth Vader is Luke's father.", "spoiler") ➞ "VPFBSZRVTFQDPLCTGNLXYWG"

vigenere("HMRSSAIEKLSAXQILCCAC", "python") ➞ "SOYLENTGREENISPEOPLE"
```

> ### 7. Columnar Cipher
The columnar cipher is a transposition cipher that works like this.

Start with a secret message:

msg = "Meet me by the lake at midnight. Bring shovel."
Transform uppercase letters into lowercase and remove punctuation and spaces:

msg = "meetmebythelakeatmidnightbringshovel"
Then, pick a keyword made out of distinct letters:

keyword = "python"
Break up the message into chunks of the same length as the keyword, and write them in rows under the keyword. Then, number the columns based on the alphabetised order of the letters in the keyword:

| | | | | | |
|-|-|-|-|-|-|
|p|y|t|h|o|n|   
|m|e|e|t|m|e|  
|b|y|t|h|e|l|  
|a|k|e|a|t|m|   
|i|d|n|i|g|h|   
|t|b|r|i|n|g|   
|s|h|o|v|e|l|   
|4|6|5|1|3|2|  

Read off the enciphered message (ciphertext) from the columns, in the order specified by the numbers:

ciphertext = "thaiivelmhglmetgnembaitsetenroeykdbh"
If the message length is not a multiple of the keyword length, fill in each blank space with "x". For example:

msg = "Meet me at midnight."

keyword = "python"

| | | | | | |
|-|-|-|-|-|-|
|p|y|t|h|o|n|   
|m|e|e|t|m|e|  
|a|t|m|i|d|n|
|i|g|h|t|x|x|


Create a function that takes a string and a keyword. Return the ciphertext if the string is in plaintext (i.e. broken up into normal English words and punctuated), or the deciphered message if the string is in ciphertext. The resulting deciphered message will not have spaces.

```js
cipher("Meet me by the lake at midnight. Bring shovel.", "python")
➞ "thaiivelmhglmetgnembaitsetenroeykdbh"

cipher("meeanbsleyamgioxebltirhxttkihnvxmhedtgex", "monty")
➞ "meetmebythelakeatmidnightbringshovelxxxx"

cipher("Mission Delta Kilo Sierra has been compromised. Kill Steve. Evacuate", "cake")
➞ "ioliiabcrsiteuxmieksrsnpiksecesdaoraemmdlvatxsntleheooelevax"
```

> ### 8. Water Jug Puzzle
Given a set of 3 jugs of water that have capacities of a, b, and c liters, find the minimum number of operations performed before each jug has `x`, `y`, and `z` liters. Only jug C will start completely filled.

An operation is any of the following: A jug is emptied, a jug is filled, or water is poured from one jug to another until one of the jugs is either empty or full.

For example, jugs `A`, `B`, and `C` with capacities of 3, 5, and 8, where jugs `A` and `B` start empty and `C` has the full 8, require 2 operations to reach the state of 0, 3, and 5 liters in the jugs.

Create a function that, given an array of jug capacities [A, B, C] and an goal state array [x, y, z], returns the minimum number of operations needed to reach the goal state. If the inputs are invalid or there is no solution, return "No solution."

```js
waterjug([3, 5, 8], [0, 3, 5]) ➞ 2

waterjug([1, 3, 4],  [0, 2, 2]) ➞ 3

waterjug([8, 17, 20], [0, 10, 10]) ➞ 9

waterjug([4, 17, 22], [2, 5, 15]) ➞ "No solution."

waterjug([3, 5, 8], [0, 0, 9]) ➞ "No solution."
```

Hint:  
- The amount of water in a jug can never exceed the capacity of that jug.
- The total liters in the goal state must be equal to the capacity of jug C.

> ### 9. Vampire Numbers

A Vampire Number is a positive integer greater than 99, that rearranged in all of its possible digits permutations, with every permutation being split into two parts, is equal to the product of at least one of its permutations.

If the number has an even quantity of digits, left and right parts will have the same length in every permutation;

If the number has an odd quantity of digits and at least three digits, the left and right parts will present different lengths for every possible permutation, alternating between them in the range +1 and -1.
Given a positive integer n, implement a function that returns the type of n as a string:

- `Normal Number` if n is lower than 100 or if no permutations return a product of their parts equal to n.
- `Pseudovampire` if n it is a Vampire with an odd quantity of digits.
- `True Vampire` if n it is a Vampire with an even quantity of digits.
```js
isVampire(1260) ➞ "True Vampire"
// Has an even number of digits and is greater than 99)
// Permutations:
// 12 * 60 = 720
// 16 * 20 = 320
// 10 * 26 = 260
// 21 * 60 = 1260

isVampire(126) ➞ "Pseudovampire"
// Has an odd number of digits and is greater than 99
// Permutations:
// 12 * 6 = 72
// 1 * 26 = 26
// 21 * 6 = 126

isVampire(67) ➞ "Normal Number"
// Is lower than 100
// Permutations:
// 6 * 7 = 7 * 6 = 42
```

Notes    
Trivially, a number from 1 to 99 is a Normal Number by the definitions: a single-digit number can't be split into two parts, and the product of the permutated two digits of a number will always be lower than the number itself.