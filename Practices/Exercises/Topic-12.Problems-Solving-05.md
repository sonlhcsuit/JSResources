# Problems Solving
__________________________
> ### 1. Harshad Numbers
Harshad/Niven numbers are positive numbers that are divisible by the sum of their digits. All single-digit numbers are Harshad numbers.

For example, 27 is a Harshad number as 2 + 7 = 9, and 9 is a divisor of 27.

Harshad numbers can occur in consecutive clusters. The numbers 1 through 10 are Harshad numbers. The numbers 132 and 133 are both Harshad numbers. The numbers 1014, 1015, 1016, 1017 are Harshad numbers.

Create a function that takes a number and returns an array of two elements. The first element is the length of the Harshad cluster of which the number is a part. The second is its order in the cluster.

```js
harshad(5) ➞ [10, 5]
// cluster = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
// The second element should be the layman order in the
// cluster, not the programming index.

harshad(133) ➞ [2, 2]
// cluster = [132, 133]

harshad(82) ➞ [0, 0]
// Not a Harshad number, so cluster length is 0, position is 0.
```


> ### 2. Patterned Wristband
A wristband can have 4 patterns:

- horizontal: each item in a row is identical.
- vertical: each item in a column is identical.
- diagonal left: each item is identical to the one on it's upper left or bottom right.
- diagonal right: each item is identical to the one on it's upper right or bottom left.
You are shown an incomplete section of a wristband.

Write a function that returns `true` if the section can be correctly classified into one of the 4 types, and false otherwise.

```js
isWristband([
  ["A", "A"],
  ["B", "B"],
  ["C", "C"]
]) ➞ true 
// Part of horizontal wristband.

isWristband([
  ["A", "B"],
  ["A", "B"],
  ["A", "B"]
]) ➞ true 
// Part of vertical wristband.

isWristband([
  ["A", "B", "C"],
  ["C", "A", "B"],
  ["B", "C", "A"],
  ["A", "B", "C"]
]) ➞ true
// Part of diagonal left wristband.

isWristband([
  ["A", "B", "C"],
  ["B", "C", "A"],
  ["C", "A", "B"],
  ["A", "B", "A"]
]) ➞ true
// Part of diagonal right wristband.
```

> ### 3. Count the Countdown Sequences
5, 4, 3, 2, 1 is an example of a countdown sequence. Write a function that returns an array of the form[x, y] where x is the number of countdown sequences in the given array and y is the array of those sequences in the order in which they appear in the array.

```js
finalCountdown([4, 8, 3, 2, 1, 2]) ➞ [1, [[3, 2, 1]]]
// 1 countdown sequence: 3, 2, 1

finalCountdown([4, 4, 5, 4, 3, 2, 1, 8, 3, 2, 1]) ➞ [2, [[5, 4, 3, 2, 1], [3, 2, 1]]]
// 2 countdown sequences:
// 5, 4, 3, 2, 1 and 3, 2, 1

finalCountdown([4, 3, 2, 1, 3, 2, 1, 1]) ➞ [3, [[4, 3, 2, 1], [3, 2, 1], [1]]]
// 3 countdown sequences:
// 4, 3, 2, 1 ; 3, 2, 1 and 1

finalCountdown([1, 1, 2, 1]) ➞ [3, [[1], [1], [2, 1]]]

finalCountdown([]) ➞  [0, []]
```

Notes   
- A disjoint 1 is a valid countdown sequence. See examples #3 & #4.
- All numbers in the array will be greater than 0.

> ### 4. Ascending Consecutive Numbers
Write a function that returns `true` if a string consists of ascending or ascending ***AND*** consecutive numbers.

```js
ascending("232425") ➞ true
// Consecutive numbers 23, 24, 25

ascending("2324256") ➞ false
// No matter how this string is divided, the numbers are not consecutive.

ascending("444445") ➞ true
// Consecutive numbers 444 and 445.
```

Notes  
- A number can consist of any number of digits, so long as the numbers are adjacent to each other, and the string has at least two of them.

> ### 5. Word Buckets
Write a function that divides a phrase into word buckets, with each bucket containing n or fewer characters. Only include full words inside each bucket.

```js
bucketize("she sells sea shells by the sea", 10)
➞ ["she sells", "sea shells", "by the sea"]

bucketize("the mouse jumped over the cheese", 7)
➞ ["the", "mouse", "jumped", "over", "the", "cheese"]

bucketize("fairy dust coated the air", 20)
➞ ["fairy dust coated", "the air"]

bucketize("a b c d e", 2)
➞ ["a", "b", "c", "d", "e"]
```

Notes  
- Spaces count as one character.
- Trim beginning and end spaces for each word bucket (see final example).
- If buckets are too small to hold a single word, return an empty array: []
- The final goal isn't to return just the words with a length equal (or lower) to the given n, but to return the entire given phrase bucketized (if possible). So, for the specific case of "by" the only word with a proper length, the phrase can't be bucketized, and the returned array has to be empty.

> ### 6. Ruth and Aaron
Two consecutive integers a and b are considered a Ruth-Aaron pair if the sum of the prime factors of a is equal to the sum of the prime factors of b.

Two definitions exist:

Summing up distinct prime factors. For example, 24 and 25 constitute a Ruth-Aaron pair by this definition. 8 and 9 do not.
```js
P24 = [2, 3]  // sum = 5

P25 = [5]  // sum = 5, equal to 24

P8 = [2]  // sum = 2

P9 = [3]  // sum = 3
```
Summing up repeated prime factors. By this definition, 24 and 25 do not constitute a Ruth-Aaron pair. But 8 and 9 do.
```js
P24 = [2, 2, 2, 3]  // sum = 9

P25 = [5, 5]  // sum = 10

P8 = [2, 2, 2]  // sum = 6

P9 = [3, 3]  // sum = 6, equal to 8
```
If two consecutive numbers have only distinct prime factors and have equal sums of prime factors, they are considered Ruth-Aaron pairs by both definitions.
```js
P77 = [7, 11]  // sum = 18

P78 = [2, 3, 13]  // sum = 18
```
Create a function that takes a number `n` and returns:

`false` if it is not part of a Ruth-Aaron pair.
A `2-element array` if it is part of a Ruth-Aaron pair.
The first element should be "Ruth" if n is the smaller number in the pair, or "Aaron" if it is the larger.
The second element should be 1 if n is part of a Ruth-Aaron pair under the first definition (sum of distinct prime factors), 2 if it qualifies by the second definition, 3 if it qualifies under both.
```js
ruthAaron(5) ➞ ["Ruth", 3]

ruthAaron(25) ➞ ["Aaron", 1]

ruthAaron(9) ➞ ["Aaron", 2]

ruthAaron(11) ➞ false
```

> ### 7. International Standard Book Numbers
The International Standard Book Number (ISBN) is a unique identifying number given to each published book. ISBNs assigned after January 2007 are 13 digits long (ISBN-13), however books with 10-digit ISBNs are still in wide use.

An ISBN-10 is verified this way:
```js
isbn10 = "0330301624"
```
Line up the digits with the numbers 10 to 1:

0	3	3	0	3	0	1	6	2	4   
10	9	8	7	6	5	4	3	2	1   

Multiply each digit with the number below it (the 10th digit in an ISBN can be an X. This last X simply means 10).

Sum up the products:

0 + 27 + 24 + 0 + 18 + 0 + 4 + 18 + 4 + 4 = 99   

If the sum is divisible by 11, the ISBN-10 is valid.

An ISBN-13 is verified this way:
```js
isbn13 = "9780316066525"
```
Line up the digits with alternating 1s and 3s:

9	7	8	0	3	1	6	0	6	6	5	2	5    
1	3	1	3	1	3	1	3	1	3	1	3	1   

Multiply each digit with the number below it and get the sum:

9 + 21 + 8 + 0 + 3 + 3 + 6 + 0 + 6 + 18 + 5 + 6 + 5 = 90
If the sum is divisible by 10, the ISBN-13 is valid.

Create a function that takes a string of numbers (possibly with an X at the end) and...

Return `Invalid` if it is not a valid ISBN-10 or ISBN-13.

Return `Valid` if it is a valid ISBN-13.

If it is a valid ISBN-10, convert it into an ISBN-13 and return the ISBN-13 number.

Convert a valid ISBN-10 to ISBN-13 by tacking 978 to the start, then changing the last digit (the check digit) so that the resulting number passes the ISBN-13 check.

```js
isbn13("9780316066525") ➞ "Valid"

isbn13("0330301824") ➞ "Invalid"

isbn13("0316066524") ➞ "9780316066525"
```

> ### 8. Index Parity of Largest Even
Write a function that returns the largest even integer in an array with its corresponding index and the parity of that index, but determining the parity of that index is limited to not using the modulo operator %.

***Output Structure***
```js
{"@odd|even index " + index_of_largest: largest_integer}
```

```js
bitwiseIndex([107, 19, 36, -18, -78, 24, 97]) ➞ {"@even index 2": 36}

bitwiseIndex([31, 7, 2, 13, 7, 9, 10, 13]) ➞ {"@even index 6": 10}

bitwiseIndex([4, 4, 4, 4, 4, 4]) ➞ {"@even index 0": 4}

bitwiseIndex([-31, -7, -13, -7, -9, -13]) ➞ "No even integer found!"
```

Notes   
- The use of indexOf() and max() are restricted.
- If there are no even integers, return "No even integer found!".
- The set of limitations imposed on this challenge dictates the level of difficulty.
- Another version of this challenge that deals with recursion can be found here.

> ### 9. Ulam Sequence
The Ulam sequence starts with:
```js
ulam = [1, 2]
```

The next number in the sequence is the smallest positive number that is equal to the sum of 2 distinct numbers (that are already in the sequence) exactly one way. Trivially, this is 3, as there are only 2 numbers in the starting sequence.

```js
ulam = [1, 2, 3]
```
The next number is 4, which is the sum of 3+1. 4 is also 2+2, but this equation does not count, as the 2 addends have to be distinct.

```js
ulam = [1, 2, 3, 4]

```
The next number cannot be 5, as 5 = 1 + 4, but also 5 = 2 + 3. There should only be one way to make an Ulam number from 2 distinct addends found in the sequence. The next number is 6 (2+4). There are 2 ways to make 7 (1+6 or 3+4), so the next is 8 (2+6). And so on.
```js
ulam = [1, 2, 3, 4, 6, 8, 11, 13, 16, 18, 26, 28, 36, 38, 47, 48, 53, …]

```
Create a function that takes a number `n` and returns the `nth` number in the `Ulam` sequence.

```js
ulam(4) ➞ 4

ulam(9) ➞ 16

ulam(206) ➞ 1856
```

> ### 10. Asteroid Collision
You are given an array asteroids of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

```js
asteroidCollision([-2, -1, 1, 2]) ➞ [-2, -1, 1, 2]

asteroidCollision([-2, 1, 1, -2]) ➞ [-2, -2]

asteroidCollision([1, 1, -2, -2]) ➞ [-2, -2]

asteroidCollision([10, 2, -5]) ➞ [10]

asteroidCollision([8, -8]) ➞ []

```
