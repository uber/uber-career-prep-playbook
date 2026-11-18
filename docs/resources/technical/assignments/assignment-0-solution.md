# Practice Assignment 0 Solution Guide: Arrays, Strings, & Hashing

Read [Practice Assignment 0](assignment-0.md) to see the instructions given to the fellows, input/output examples accompanying the problem statements, and descriptions of the problem-solving techniques the fellows are asked to identify and use.

### Question 1: Zero Sum

Given an array of integers, return the number of pairs of integers in the array that sum to 0 assuming you can use the element at each index at most once.

**Technique:** Hash the counts

**Approach:** Iterate over the array, building a map of integers to counts. Initialize a final count to zero. Iterate over the map. Do one of the following:

1. For each negative (or positive) integer, do nothing. For each positive (or negative) integer x, look up the count of x\*-1. Add the *minimum* of the counts of x and x\*-1 to the final count. If 0 is encountered, divide the count by 2 (rounded down) and add it to the final count.
2. Look up the count of x\*1. Add the *minimum* of the counts of x and x\*-1 to the final count. When the iteration is complete, divide the final count by 2 (rounded down) before returning it.

Follow-Up: Given an array of integers, return the number of pairs of integers in the array that sum

**Big O:** O(n) space, O(n) time

#### Follow-Up

Now assume you can re-use elements in different pairs (i.e., the elements in a pair must be from different indices but different pairs may use an element form the same index).

**Technique:** Hash the counts

**Approach:** Iterate over the array, building a map of integers to counts. Initialize a final count to zero. Iterate over the map. Do one of the following:

1. For each negative (or positive) integer, do nothing. For each positive (or negative) integer x, look up the count of x\*-1. Add the *product* of the counts of x and x\*-1 to the final count. If 0 is encountered with count y, add the *product* of y and (y-1)/2 to the final count.
2. Look up the count of x\*1. Add the *product* of the counts of x and x\*-1 to the final count. When the iteration is complete, divide the final count by 2 before returning it.

**Big O:** O(n) space, O(n) time

### Question 2: Unique Sum

Given an array of integers, return the sum of unique elements in the array.

**Technique:** Hash the elements

**Approach:**

Do one of the following:

1. Iterate over the array, building a set of the elements (or, equivalently, initializing a set from the array if supported in the language of choice, or building a map with garbage/identical values if the language of choice does not have a built-in set data structure). Initialize a final count. Iterate over the set, adding each element to the final count.
2. Initialize a final count. Iterate over the array, building a set of the elements (or, equivalently, building a map with garbage/identical values if the language of choice does not have a built-in set data structure). Before adding an element to the set, check if it is already present; if it is not, add it to the final count.

**Big O:** O(n) space, O(n) time

### Question 3: First Occurrence

Given a string, return a string that contains only the first occurrence of each character in the string.

**Technique:** Hash the elements

**Approach:**

Initialize a result string. Iterate over the string, building a set of the characters (or, equivalently, building a map with garbage/identical values if the language of choice does not have a built-in set data structure). Before adding a character to the set, check if it is already present; if it is not, append it to the result string.

*Note: the solution should avoid O(n) string appends (if possible in the language of choice) as that would result in a time complexity of O(n^2). The technique for doing so depends on the mutability of strings and the options for initialization in the language of choice. In a language with mutable strings, this could involve allocating a result string the same size as the original string, then truncating it to the size of the set. In a language with immutable strings that allows string initialization from an array, this could involve building the result as an array of characters and initializing the result string only at the end.*

**Big O:** O(n) space, O(n) time
