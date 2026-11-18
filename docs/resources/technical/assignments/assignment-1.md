# Practice Assignment 1: Arrays & Strings

These questions should be completed without Googling the answer, which in most cases is easily available on the internet. That would defeat the point of the assignment, which is for *you* to practice interviewing skills. You use your own knowledge as it stands. There are two exceptions to this rule. Firstly, if you are unsure of syntax (e.g., method names, constructor arguments, etc.), you may look it up. Secondly, if you do not know a term, you may look it up. In some cases, depending on your academic schedule, you may not yet have covered a data structure yet, in which case we *encourage* you to learn and study the general concepts *before* attempting the problem.

Some questions may seem vague. This is intentional, as interview questions are often vague. Avoid making unnecessary assumptions, including based on example input/output, which is not exhaustive. If you *must* make an assumption, state your assumption in a comment in your code.

## Array & String Problems (~6 hrs)

### Instructions

For each problem, identify the appropriate array/string technique from Workshop 1. **State the technique in a comment at the top of your file**. As a reminder, the options are:

> **Two Pointer Techniques:**

1. Fixed-size sliding window
2. Variable-size (shrinking/growing) sliding window
3. Reset/catch-up two-pointer
4. Forward/backward two-pointer
5. Two arrays/strings two-pointer

    **Sorting & Searching Techniques:**

<!-- -->

1. Binary search variation
2. Sorting algorithm variation
3. Sort the array, then solve

    **Hashing Techniques**

<!-- -->

1. One-directional running computation/total
2. Bi-drectional running computation/total
3. Two arrays/strings increment/decrement hashmap counts

Then, write a function to solve the problem and write test cases to check your function. When run, the file you submit should execute your function on your test cases (e.g., through a main method, if applicable in your language). **State the time and space complexity of your solution in a comment at the top of your file**.

Time how long you spend on each problem. You should actively **work on each problem for a MAXIMUM of 40 minutes**. Once 40 minutes has elapsed, submit whatever you have, regardless of whether you are finished. Please indicate in a comment at the bottom of your file how long you spent on the problem. It is important that you are honest about how long each problem took you as it will help your mentor help you!

### Question 1: MaxMeanSubArray

Given an array of integers and an integer, k, find the maximum mean of a subarray of size k.

Examples:

```text
Input Array: [4, 5, -3, 2, 6, 1]
Input k = 2
Output: 4.5

Input Array: [4, 5, -3, 2, 6, 1]
Input k = 3
Output: 3

Input Array: [1, 1, 1, 1, -1, -1, 2, -1, -1]
Input k = 3
Output: 1

Input Array: [1, 1, 1, 1, -1, -1, 2, -1, -1, 6]
Input k = 5
Output: 1
```

### Question 2: ReverseVowels

Given a string, reverse the order of the vowels in the string.

Examples:

```text
Input String: "Uber Career Prep"
Modified String: "eber Ceraer PrUp"

Input String: "xyz"
Modified String: "xyz"

Input String: "flamingo"
Modified String: "flominga"
```

### Question 3: ZeroSumSubArrays

Given an array of integers, count the number of subarrays that sum to zero.

Examples:

```text
Input Array: [4, 5, 2, -1, -3, -3, 4, 6, -7]
Output: 2
(Subarrays: [5, 2, -1, -3, -3], [-3, 4, 6, -7])

Input Array: [1, 8, 7, 3, 11, 9]
Output: 0

Input Array: [8, -5, 0, -2, 3, -4]
Output: 2
(Subarrays: [0], [8, -5, 0, -2, 3, -4])
```

### Question 4: BackspaceStringCompare

Given two strings representing series of keystrokes, determine whether the resulting text is the same. Backspaces are represented by the '#' character so "x#" results in the empty string ("").

Examples:

```text
eInput Strings: "abcde", "abcde"
Output: True

Input Strings: "Uber Career Prep", "u#Uber Careee#r Prep"
Output: True

Input Strings: "abcdef###xyz", "abcw#xyz"
Output: True

Input Strings: "abcdef###xyz", "abcdefxyz###"
Output: False
```

### Question 5: ShortestSubstring

Given a string and a second string representing required characters, return the length of the shortest substring containing all the required characters.

Examples:

```text
Input Strings: "abracadabra", "abc"
Output: 4
(Shortest Substring: "brac")

Input Strings: "zxycbaabcdwxyzzxwdcbxyzabccbazyx", "zzyzx" (Fun fact: "Zzyzx" is a town in the Mojave Desert in California!)
Output: 10
(Shortest Substring: "zzxwdcbxyz")

Input Strings: "dog", "god"
Output: 3
(Shortest Substring: "dog")
```

### Question 6: MissingInteger

Given an integer n and a sorted array of integers of size n-1 which contains all but one of the integers in the range 1-n, find the missing integer.

Examples:

```text
Input Array: [1, 2, 3, 4, 6, 7]
Input n: 7
Output: 5

Input Array: [1]
Input n: 2
Output: 2

Input Array: [1, 2, 3, 4, 5, 6, 7, 8, 10, 11, 12]
Input n: 12
Output: 9
```

### Question 7: KAnagrams

Two strings are considered to be “k-anagrams” if they can be made into anagrams by changing at most k characters in one of the strings. Given two strings and an integer k, determine if they are k-anagrams.

Examples:

```text
Input Strings: "apple", "peach"
Input k: 1
Output: False

Input Strings: "apple", "peach"
Input k: 2
Output: True

Input Strings: "cat", "dog"
Input k: 3
Output: True

Input Strings: "debit curd", "bad credit"
Input k: 1
Output: True

Input Strings: "baseball", "basketball"
Input k: 2
Output: False
```

### Question 8: MergeIntervals

Given a list of integer pairs representing the low and high end of an interval, inclusive, return a list in which overlapping intervals are merged.

Examples:

```text
Input: [(2, 3), (4, 8), (1, 2), (5, 7), (9, 12)]
Output: [(4, 8), (1, 3), (9, 12)]

Input: [(5, 8), (6, 10), (2, 4), (3, 6)]
Output: [(2, 10)]

Input: [(10, 12), (5, 6), (7, 9), (1, 3)]
Output: [(10, 12), (5, 6), (7, 9), (1, 3)]
```

### Question 9: DedupArray

Given a sorted array of non-negative integers, modify the array by removing duplicates so each element only appears once. If arrays are static (aka, not dynamic/resizable) in your language of choice, the remaining elements should appear in the left-hand side of the array and the extra space in the right-hand side should be padded with -1s.

Examples:

```text
Input Array: [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
Modified Array: [1, 2, 3, 4]
or [1, 2, 3, 4, -1, -1, -1, -1, -1, -1] (depending on language)

Input Array: [0, 0, 1, 4, 5, 5, 5, 8, 9, 9, 10, 11, 15, 15]
Modified Array: [0, 1, 4, 5, 8, 9, 10, 11, 15]
or [0, 1, 4, 5, 8, 9, 10, 11, 15, -1, -1, -1, -1, -1] (depending on language)

Input Array: [1, 3, 4, 8, 10, 12]
Modified Array: [1, 3, 4, 8, 10, 12]
```
