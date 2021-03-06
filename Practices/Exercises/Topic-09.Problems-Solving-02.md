# Problems Solving
__________________________
> ### 1. Distance to Nearest Vowel
Write a function that takes in a string and for each character, returns the distance to the nearest vowel. If the character is a vowel itself, return 0.

```js
distanceToNearestVowel("aaaaa") ➞ [0, 0, 0, 0, 0]

distanceToNearestVowel("babbb") ➞ [1, 0, 1, 2, 3]

distanceToNearestVowel("abcdabcd") ➞ [0, 1, 2, 1, 0, 1, 2, 3]

distanceToNearestVowel("shopper") ➞ [2, 1, 0, 1, 1, 0, 1]
```
```js
function distanceToNearestVowel(strg){
    return []
}
```

> ### 2. Odd Square Patch
Create a function that takes an array of numbers, and returns the size of the biggest square patch of odd numbers. See examples for a clearer picture.

```js
oddSquarePatch([
  [1, 2, 4, 9],
  [4, 5, 5, 7],
  [3, 6, 1, 7]
]) ➞ 2
// The 2x2 square at the lower right
// ([5, 7] on the 2nd row, [1, 7] on the third).

oddSquarePatch([[1, 2, 4, 9]]) ➞ 1

// An array with a single row can only have a square patch of
// maximum size 1x1 containing a single odd element.

oddSquarePatch([[2, 4, 6]]) ➞ 0
```

> ### 3. Junction or Self?
In this challenge, you have to separate integers into two families, establishing if they are Junction Numbers or Self Numbers. Given a positive number `n`:

If exists at least a single number which added to the sum of its digits is equal to `n`, then `n` is a Junction Number.

If there are not numbers which added to the sum of their digits are equal to `n`, then `n` is a Self Number.

Given a positive integer `n`, implement a function that returns:

The string "Self" if n is a Self Number.
If n is a Junction Number an array, ordered descendingly, containing the numbers which generate n.

```js
junctionOrSelf(25) ➞ [17]
// If we add 17 to the sum of its digits...
// ...17 + 1 + 7 = 25
// 25 is a Junction Number

junctionOrSelf(818) ➞ [805, 796]
// If we add 805 to the sum of its digits...
// ...805 + 8 + 0 + 5 = 818
// If we add 796 to the sum of its digits...
// ...796 + 7 + 9 + 6 = 818
// 818 is a Junction Number

junctionOrSelf(7) ➞ "Self"
// 1 + 1 = 2
// 2 + 2 = 4
// 3 + 3 = 6
// No number added to its own digits is equal to 7
// 7 is a Self Number
```

As in example #3, the sum of the digits of a positive integer lower than 10 is equal to that same integer.

By the formal definition, a Junction number must have at least two other numbers that generate it, so that the Instructions are to be considered valid only for this specific challenge.

> ### 4. Morse Code Decoded
Create a function that takes a string (morse code) as an argument and returns an unencrypted string.

```js
decodeMorse(".... . .-.. .--.   -- .   -.-.--") ➞ "HELP ME !"

decodeMorse("-.-. .... .- .-.. .-.. . -. --. .") ➞ "CHALLENGE"
```
The following object can be used for coding:
```js
morseToDots = {
  ".-":"A", "-...":"B", "-.-.":"C", "-..":"D", ".":"E", "..-.":"F",
  "--.":"G", "....":"H", "..":"I", ".---":"J", "-.-":"K", ".-..":"L",
  "--":"M", "-.":"N", "---":"O", ".--.":"P", "--.-":"Q", ".-.":"R",
  "...":"S", "-":"T", "..-":"U", "...-":"V", ".--":"W", "-..-":"X",
  "-.--":"Y", "--..":"Z", "-----":"0", ".----":"1", "..---":"2",
  "...--":"3", "....-":"4", ".....":"5", "-....":"6", "--...":"7",
  "---..":"8", "----.":"9", "-.-.--":"!", "   ":" ", "..--..":"?",
  ".-.-.-":".", ".----.":"\"", "---..." :":", "--..--":", ", " ":""
}
```

> ### 5. Creating a Picture Frame
Create a function that takes the width, height and character and returns a picture frame as a matrix.

```js
getFrame(4, 5, "#") ➞ [
  ["####"],
  ["#  #"],
  ["#  #"],
  ["#  #"],
  ["####"]
]
// Frame is 4 characters wide and 5 characters tall.

getFrame(10, 3, "*") ➞ [
  ["**********"],
  ["*        *"],
  ["**********"]
]
// Frame is 10 characters and wide and 3 characters tall.

getFrame(2, 5, "0") ➞ "invalid"
// Frame"s width is not more than 2.
```

> ### 6. Magic Sigil Generator
A magic sigil is a glyph which represents a desire one wishes to manifest in their lives. There are many ways to create a sigil, but the most common is to write out a specific desire (e.g. "I HAVE WONDERFUL FRIENDS WHO LOVE ME"), remove all vowels, remove any duplicate letters and then design a glyph from what remains.

Using the sentence above as an example, we would remove duplicate letters:
 
AUFRINDSWHLOVME  
And then remove all vowels, leaving us with:

FRNDSWHLVM  
Create a function that takes a string and removes its vowels and duplicate letters. The returned string should not contain any spaces and be in uppercase.

```js
sigilize("i am healthy") ➞ "MLTHY"

sigilize("I FOUND MY SOULMATE") ➞ "FNDYSLMT"

sigilize("I have a job I enjoy and it pays well") ➞ "HVBJNDTPYSWL"
```
Notes: Reverse

> ### 7. Digital Egomania: the Self-Describing Numbers
In this challenge, you have to establish if a given number is self-describing. To be self-describing, a positive number must have an even quantity of digits, because it has to be split into separated pairs of adjacent digits x and y, and each pair can be interpreted as a declaration: among the digits of the number, there are x instances of the digit equal to y.

If we take as an example the self-describing number 10123331, we can see how it has an even quantity of digits and it can be split into four pairs:

[1, 0] ➞ This pair declares that among the digits of the number there is 1 instance of 0
[1, 2] ➞ This pair declares that among the digits of the number there is 1 instance of 2
[3, 3] ➞ This pair declares that among the digits of the number there are 3 instances of 3
[3, 1] ➞ This pair declares that among the digits of the number there are 3 instances of 1
If every "declaration" represented by the pairs is true (as in the above example), then the number is self-describing.

Given a non-negative integer num, implement a function that returns true if num is a self-describing number, or false if it's not.

```js
isSelfDescribing(10123331) ➞ true
// See the Instructions

isSelfDescribing(224444) ➞ true
// Pair [2, 2] is true (two times 2 into num)
// Pair [4, 4] is true (four times 4 into num)
// Pair [4, 4] is true (same as previous)

isSelfDescribing(2211) ➞ false
// Pair [2, 2] is true (two times 2 into num)
// Pair [1, 1] is false! It declares: one time 1 into num...
// ...but 2211 has two instances of 1 among its digits

isSelfDescribing(333) ➞ false
// Odd quantity of digits, it can't be splitted
```

Notes  
Pairs can be repeated (see example #2), but they have to be true in any case.
Remember to consider the totality of the digits of the number, when checking if a pair represents a true declaration (see example #3).
You can expect always valid non-negative integers as input.

> ### 8. Check Magic Square
A "magic square" is a square divided into smaller squares each containing a number, such that the numbers in each vertical, horizontal, and diagonal row add up to the same value.

3x3 Magic Square   
<img src="https://edabit-challenges.s3.amazonaws.com/3x3magicsquare.png">

Write a function that takes a 2D array, checks if it's a magic square and returns either true or false depending on the result.

```js
isMagicSquare([
  [8, 1, 6],
  [3, 5, 7],
  [4, 9, 2]
]) ➞ true

isMagicSquare([
  [16,  3,  2, 13],
  [ 5, 10, 11,  8],
  [ 9,  6,  7, 12],
  [ 4, 15, 14,  1]
]) ➞ true

isMagicSquare([
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]) ➞ false
```
Check diagonals as well.
Test input will always be square.
Check the Resources tab for additional info on magic squares.






> ### 9. The Fiscal Code

Each person in Italy has an unique identifying ID code issued by the national tax office after the birth registration: the Fiscal Code (Codice Fiscale). Check the Resources tab for more info on this.

Given an object containing the personal data of a person (name, surname, gender and date of birth) return the 11 code characters as a string following these steps:

Generate 3 capital letters from the surname, if it has:

At least 3 consonants then the first three consonants are used.(Newman -> NWM).     
Less than 3 consonants then vowels will replace missing characters in the same order they appear (Fox -> FXO | Hope -> HPO).   
Less than three letters then "X" will take the third slot after the consonant and the vowel (Yu -> YUX).

    
Generate 3 capital letters from the name, if it has:          
Exactly 3 consonants then consonants are used in the order they appear (Matt -> MTT).    
More than 3 consonants then first, third and fourth consonant are used (Samantha -> SNT | Thomas -> TMS).      
Less than 3 consonants then vowels will replace missing characters in the same order they appear (Bob -> BBO | Paula -> PLA).     
Less than three letters then "X" will take the the third slot after the consonant and the vowel (Al -> LAX).     
 
Generate 2 numbers, 1 letter and 2 numbers from date of birth and gender:      

Take the last two digits of the year of birth (1985 -> 85).       
Generate a letter corresponding to the month of birth (January -> A | December -> T) using the table for conversion included in the code.      
For males take the day of birth adding one zero at the start if is less than 10 (any 9th day -> 09 | any 20th day -> 20).         
For females take the day of birth and sum 40 to it (any 9th day -> 49 | any 20th day -> 60).       
Examples

``` javascript
const months = {
    1: "A",
    2: "B",
    3: "C",
    4: "D",
    5: "E",
    6: "H",
    7: "L",
    8: "M",
    9: "P",
    10: "R",
    11: "S",
    12: "T"
}
```

``` javascript
fiscalCode({
    name: "Matt",
    surname: "Edabit",
    gender: "M",
    dob: "1/1/1900"
})➞
"DBTMTT00A01"

fiscalCode({
    name: "Helen",
    surname: "Yu",
    gender: "F",
    dob: "1/12/1950"
})➞
"YUXHLN50T41"

fiscalCode({
    name: "Mickey",
    surname: "Mouse",
    gender: "M",
    dob: "16/1/1928"
})➞
"MSOMKY28A16"
```

> ### 10. Number of Boomerangs
A boomerang is a V-shaped sequence that is either upright or upside down. Specifically, a boomerang can be defined as: sub-array of length 3, with the first and last digits being the same and the middle digit being different.

Some boomerang examples:
```js
[3, 7, 3], [1, -1, 1], [5, 6, 5]
``` 

Create a function that returns the total number of boomerangs in an array.

To illustrate:

```js
[3, 7, 3, 2, 1, 5, 1, 2, 2, -2, 2]
// 3 boomerangs in this sequence:  [3, 7, 3], [1, 5, 1], [2, -2, 2]
```
Be aware that boomerangs can overlap, like so:

```js
[1, 7, 1, 7, 1, 7, 1]
// 5 boomerangs (from left to right): [1, 7, 1], [7, 1, 7], [1, 7, 1], [7, 1, 7], and [1, 7, 1]
```
```js
countBoomerangs([9, 5, 9, 5, 1, 1, 1]) ➞ 2

countBoomerangs([5, 6, 6, 7, 6, 3, 9]) ➞ 1

countBoomerangs([4, 4, 4, 9, 9, 9, 9]) ➞ 0
```

Notes
[5, 5, 5] (triple identical digits) is NOT considered a boomerang because the middle digit is identical to the first and last.
