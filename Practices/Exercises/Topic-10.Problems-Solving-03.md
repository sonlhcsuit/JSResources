# ***Problems Solving***
________________________

> ### 1. Roman Numeral Converter

Complete the function to convert the given number into a roman numeral.
All roman numerals answers should be provided in upper-case.

``` javascript
function convertToRoman(num) {
    return num;
}
convertToRoman(97); //XCVII
```

> ### 2. Padovan Sequence
In number theory, the Padovan sequence is the sequence of integers P(n) defined by the initial values:
```js
P(0) = P(1) = P(2) = 1
// And the recurrence relation:

P(n) = P(n-2) + P(n-3)
```
As with any sequence defined by a recurrence relation, Padovan numbers P(m) for m<0 can be defined by rewriting the recurrence relation as:

`P(m) = P(m+3) - P(m+1)`   
**Objective**
Create a function that takes two numbers, m and n, being m always negative and n always positive, and returns an array with the Padovan numbers between P(m) and P(n).

```js

padovan(-1, 1) ➞ [0, 1, 1]

padovan(-10, 10) ➞ [2, -1, 0, 1, -1, 1, 0, 0, 1, 0, 1, 1, 1, 2, 2, 3, 4, 5, 7, 9, 12]

padovan(-50, 1) ➞ [-524, 245, 71, -279, 316, -208, 37, 108, -171, 145, -63, -26, 82, -89, 56, -7, -33, 49, -40, 16, 9, -24, 25, -15, 1, 10, -14, 11, -4, -3, 7, -7, 4, 0, -3, 4, -3, 1, 1, -2, 2, -1, 0, 1, -1, 1, 0, 0, 1, 0, 1, 1]
```

> ### 3. Telephone Number Validator

Complete the function to return `true` if the passed string looks like a valid US phone number.

The user may fill out the form field any way they choose as long as it has the format of a valid US number. The following are examples of valid formats for US numbers (refer to the tests below for other variants):

``` 
555-555-5555
(555)555-5555
(555) 555-5555
555 555 5555
5555555555
1 555 555 5555
```

For this challenge you will be presented with a string such as `800-692-7753` or `8oo-six427676;laskdjf` . Your job is to validate or reject the US phone number based on any combination of the formats provided above. The area code is required. If the country code is provided, you must confirm that the country code is 1. Return `true` if the string is a valid US phone number; otherwise return `false` .

``` javascript
function telephoneCheck(str) {
    return true;
}
telephoneCheck("555-555-5555");
```

| Invoke                              | answer     |
|-------------------------------------|------------|
| telephoneCheck("555-555-5555")      | a boolean. |
| telephoneCheck("1 555-555-5555")    | true.      |
| telephoneCheck("1 (555) 555-5555")  | true.      |
| telephoneCheck("5555555555")        | true.      |
| telephoneCheck("555-555-5555")      | true.      |
| telephoneCheck("(555)555-5555")     | true.      |
| telephoneCheck("1(555)555-5555")    | true.      |
| telephoneCheck("555-5555")          | false.     |
| telephoneCheck("5555555")           | false.     |
| telephoneCheck("1 555 555 5555")    | true.      |
| telephoneCheck("1 456 789 4444")    | true.      |
| telephoneCheck("123**&!!asdf#")     | false.     |
| telephoneCheck("55555555")          | false.     |
| telephoneCheck("(6054756961)")      | false      |
| telephoneCheck("2 (757) 622-7382")  | false.     |
| telephoneCheck("0 (757) 622-7382")  | false.     |
| telephoneCheck("-1 (757) 622-7382") | false      |
| telephoneCheck("2 757 622-7382")    | false.     |
| telephoneCheck("10 (757) 622-7382") | false.     |
| telephoneCheck("27576227382")       | false.     |
| telephoneCheck("(275)76227382")     | false.     |
| telephoneCheck("2(757)6227382")     | false.     |
| telephoneCheck("2(757)622-7382")    | false.     |
| telephoneCheck("(555)5(55?)-5555")  | false.     |

> ### 4. Cash Register

Design a cash register drawer function `checkCashRegister()` that accepts purchase price as the first argument `price` , payment as the second argument `cash` , and cash-in-drawer `cid` as the third argument.

`cid` is a 2D array listing available currency.

The checkCashRegister() function should always return an object with a status key and a change key.

Return `{status: "INSUFFICIENT_FUNDS", change: {}}` if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return `{status: "CLOSED", change: {...}}` with cash-in-drawer as the value for the key change if it is equal to the change due.

Otherwise, return `{status: "OPEN", change: {... }}`, with the change due in coins and bills, sorted in highest to lowest order, as the value of the change key.

``` javascript
function checkCashRegister(price, cash, cid) {
    var change;
    return change;
}
checkCashRegister(19.5, 20, {
    'PENNY':1.01,
    'NICKEL':2.05,
    'DIME':3.1,
    'QUARTER':4.25,
    'ONE':90,
    'FIVE':55,
    'TEN':20,
    'TWENTY':60,
    'FIFTY':100,
    'ONE HUNDRED':100
});

//{status: "OPEN", change: {"QUARTER": 0.5}}
```

> ### 5. Phone Letter Combinations
Given a string containing digits from 2-9 inclusive, return number of all possible letter combinations that the number could represent. A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.  

<img src="https://www.researchgate.net/profile/Shumin_Zhai/publication/221518150/figure/fig1/AS:305488823635968@1449845619238/The-standard-12-key-telephone-keypad-character-layout-follows-the-ITU-E161-standard-8.png">


Alternative Text  


```js
letter_combinations("23") ➞ 9 (["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"])

letter_combinations("532") ➞ 29 ( ["jda", "jdb", "jdc", "jea", "jeb", "jec", "jfa", "jfb", "jfc", "kda", "kdb", "kdc", "kea", "keb", "kec", "kfa", "kfb", "kfc", "lda", "ldb", "ldc", "lea", "leb", "lec", "lfa", "lfb", "lfc"] )   
```

> ### 6. Digitaldrome
In this challenge, you have to establish if the digits of a given number form a sequence (ascending or descending).

Given an integer n, implement a function that returns a string:

- `Metadrome` if the digits of n form an ascending sequence without repeating digits.  

- `Plaindrome` if the digits of n form an ascending sequence with repeating digits.   

- `Katadrome` if the digits of n form a descending sequence without repeating digits.  

- `Nialpdrome` if the digits of n form a descending sequence with repeating digits.  

- `Repdrome` if n contains a single repeating digit.  

- `Nondrome` if none of the above conditions is true.
```js
digitaldrome(1357) ➞ "Metadrome"
// Ascending sequence without repeating digits

digitaldrome(12344) ➞ "Plaindrome"
// Ascending sequence with repeating digits

digitaldrome(7531) ➞ "Katadrome"
// Descending sequence without repeating digits

digitaldrome(9874441) ➞ "Nialpdrome"
// Descending sequence with  repeating digits

digitaldrome(666) ➞ "Repdrome"
// There's only a single repeating digit

digitaldrome(1985) ➞ "Nondrome"
// This is not a sequence
```
Hint:  
- Any given n will be a positive integer.
- The word "drome" comes from the Greek suffix for "run", while "kata" and "meta" are the prefixes for "down" (or "into") and "after" (or "through").

> ### 7. Poker Flush?
Create a function that takes in two arrays and determines whether there exists a flush.

The first array represents the 5 cards dealt on the table.
The second array represents the 2 cards in your hand.
Notation: card number and suit (abbreviated as S = Spades, H = Hearts, D = Diamonds, C = Clubs) separated by an underscore.
```js
checkFlush(["A_S", "J_H", "7_D", "8_D", "10_D"], ["J_D", "3_D"]) ➞ true 
// diamond flush

checkFlush(["10_S", "7_S", "9_H", "4_S", "3_S"], ["K_S", "Q_S"]) ➞ true 
// spade flush

checkFlush(["3_S", "10_H", "10_D", "10_C", "10_S"], ["3_S", "4_D"]) ➞ false
```

> ### 8. Dice Gambling
Create a function that takes an array consisting of dice rolls from 1-6. Return the sum of your rolls with the following conditions:

If a 1 is rolled, that is bad luck. The next roll counts as 0.
If a 6 is rolled, that is good luck. The next roll is multiplied by 2.
The array length will always be 3 or higher.
```js
rolls([1, 2, 3]) ➞ 4
// The second roll, 2, counts as 0 as a result of rolling 1.

rolls([2, 6, 2, 5]) ➞ 17
// The 2 following the 6 was multiplied by 2.

rolls([6, 1, 1]) ➞ 8
// The first roll makes the second roll worth 2, but the
// second roll was still 1 so the third roll doesn't count.
```

Notes   
Even if a 6 is rolled after a 1, 6 isn't summed but the 6's "effect" still takes place.



> ### 9. Sexagenary Cycle (Chinese Zodiac)

In early recorded Chinese history, time was reckoned using the sexagenary (60-year) cycle, generated from two subcycles:

Five heavenly stems (elements) in this order: wood, fire, earth, metal, water. The stems change every two years.
Twelve earthly branches (animals) in this order: rat, ox, tiger, rabbit, dragon, snake, horse, sheep, monkey, rooster, dog, pig. The branches change yearly.
The combinations between these two sub-cycles result in a 60-year cycle where no two years are the same — for example, the 5 years of the Rat have 5 different elements: 1924 Wood Rat, 1936 Fire Rat, 1948 Earth Rat, 1960 Metal Rat, 1972 Water Rat.

The first 14 years of the current cycle are shown in the table below:

| Gregorian Year | Stem  | Branch  |
|----------------|-------|---------|
| 1984           | Wood  | Rat     |
| 1985           | Wood  | Ox      |
| 1986           | Fire  | Tiger   |
| 1987           | Fire  | Rabbit  |
| 1988           | Earth | Dragon  |
| 1989           | Earth | Snake   |
| 1990           | Metal | Horse   |
| 1991           | Metal | Sheep   |
| 1992           | Water | Monkey  |
| 1993           | Water | Rooster |
| 1994           | Wood  | Dog     |
| 1995           | Wood  | Pig     |
| 1996           | Fire  | Rat     |
| 1997           | Fire  | Ox      |

These days, the sexagenary cycle is used mainly for historical celebrations and events, and in Chinese astrology. The Gregorian calendar is now the standard means of reckoning time.

Create a function that takes a number representing a year in the Gregorian calendar, and returns a string consisting of the corresponding stem-and-branch combination in the sexagenary cycle.

Examples

``` javascript
sexagenary(1971)➞
"Metal Pig"

sexagenary(1927)➞
"Fire Rabbit"

sexagenary(1974)➞
"Wood Tiger"
```



> ### 10. Number of Lucky Tickets
Create a function that counts how many n-digit numbers have the same sum of the first half and second half of the digits (“lucky” numbers). The number n is even. For example, for n = 6, the numbers "001010", "112220", "000000" are lucky.

```js
luckyTicket(2) ➞ 10

luckyTicket(4) ➞ 670

luckyTicket(12) ➞ 39581170420
```

Notes  
- There are checks for n > 10, so watch out for code performance.