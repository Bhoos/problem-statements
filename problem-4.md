# Problem Statement 4
To understand recursion, one must first understand the recursion. Most of the errors in programming are logical mistakes.

**Requirements:**
- JavaScript

**Problem Goal:** 
-  Find the calculation bug in the following code.Where can it go wrong?

**Problem Description:**
```
const rates = [
   {
       "upto": 100,
       "rate": 100
   },
   {
       "upto": 200,
       "rate": 150
   },
   {
       "upto": -1,
       "rate": 200
   }
];
```
This scenario relates to our taxation system in Nepal. This is the same scenario we faced in our coin shop implementation. User will get 100 coins equivalent to 1 diamond till he spends 100 diamonds at one buy. When the user spends more than 100 diamonds at one buy, The added value of 1 diamond after 100 diamonds will be equivalent to 150 coins. This loop will run till the last -1 upto value. Then all the beyond value will have a rate of 200 equivalent to 1 diamond.

**Scenario:**
```
function findRanges(
 ranges: Array<{ upto: number; rate: number }>,
 currentRange: number,
 total = 0,
): number {
 if (currentRange <= 0) return total;
 const rangesCopy = ranges.slice();
 const min = Math.min(currentRange, rangesCopy[0].upto);
 const nextTotal = rangesCopy[0].rate * min;
 rangesCopy.shift();
 return total + findRanges(rangesCopy, currentRange - min, nextTotal);
 }
```

Where can it go wrong?
