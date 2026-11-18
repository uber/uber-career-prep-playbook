# Practice Assignment 0: Arrays, Strings, & Hashing

These questions should be completed without Googling the answer, which in most cases is easily available on the internet. That would defeat the point of the assignment, which is for *you* to practice interviewing skills. You use your own knowledge as it stands. There are two exceptions to this rule. Firstly, if you are unsure of syntax (e.g., method names, constructor arguments, etc.), you may look it up. Secondly, if you do not know a term, you may look it up. In some cases, depending on your academic schedule, you may not yet have covered a data structure yet, in which case we *encourage* you to learn and study the general concepts *before* attempting the problem.

Some questions may seem vague. This is intentional, as interview questions are often vague. Avoid making unnecessary assumptions, including based on example input/output, which is not exhaustive. If you *must* make an assumption, state your assumption in a comment in your code.

## Part 1: Environment Setup (~1 hr)

\[Insert instructions on how you woul like fellows to submit homework and any necessary setup such as git/GitHub.\]

## Part 2: Array & String/Set & Map Problems (~2 hrs)

### Instructions

Before beginning this section, read up on the definitions of Big O notation, time and space complexity, hashing, and set and map data structures if they are unfamiliar to you or you need a refresher.

1. [Big O Notation](https://www.educative.io/answers/what-is-big-o-notation)
2. [Time Complexity](https://www.educative.io/answers/what-is-the-time-complexity-of-an-algorithm)
3. [Time vs. Space Complexity](https://www.educative.io/answers/time-complexity-vs-space-complexity)
4. [Asymptotic Notations](https://www.educative.io/answers/what-are-the-common-asymptotic-notations)
5. [Sets](https://www.geeksforgeeks.org/introduction-to-set-data-structure-and-algorithm-tutorials/) and [Maps](https://www.geeksforgeeks.org/introduction-to-map-data-structure-and-algorithm-tutorials/)
6. [Hashing and Maps](https://www.thedshandbook.com/hash-tables/)

In your technical interview for entrance into the UCP cohort, you were asked a question in which you were given an array or a string. Most array and string problems can be solved in O(n^2) time using nested loops; this is the “brute force” solution. However, most of these solutions can be improved to O(n) time. Over the course of homeworks 0 and 1 and workshop 1, we will be exploring techniques for doing so.

Using hash data structures (sets or maps) is one such technique. To use this technique, iterate over the array or string and hash each element, then iterate over the hash data structure to get the solution. This is an example of a time-space trade-off; in most cases, using this technique will increase the space from O(1) to O(n) to achieve optimal time complexity of O(n). What you store in your hash data structure depends on the problem. There are three main variations. From simplest to most complex:

1. **Hash the elements.** Use a hash set (or a hash map in which the values do not matter if your language does not support sets) and just hash the elements themselves. This is equivalent to converting the array or string to a set. Use this technique if the solution requires knowing about the presence or absence of elements.
2. **Hash the counts.** Use a hash map and iterate through the array or string, adding each element to the map with a count of 1 if not present and incrementing the count if present. The result is a hash map representing the occurrences of each element in the original array or string. Use this technique if the solution requires knowing about the frequency of elements.
3. **Compute and hash something else.** Sometimes the solution will require a different value per element. For example, this could be the index of the element in the original data structure or a value computed based on other elements in the data structure. In this case, use a hash map, do any precomputation that requires iterating through the initial data structure first (if necessary), then iterate through the array or string computing and storing the value for each element.

In most cases, the required solution will not be in the form of a set or map but rather require you to look up or compute something based on your set or map.

You will now do three array/string problems that can be optimally solved in O(n) time and O(n) space using a hash data structure and one of these three techniques. For each problem, write a function to solve the problem and write test cases to check your function. When run, the file you submit should execute your function on your test cases (e.g., through a main method, if applicable in your language). **State the time and space complexity of your solution in a comment at the top of your file**.

Time how long you spend on each problem. You should actively **work on each problem for a MAXIMUM of 40 minutes**. Once 40 minutes has elapsed, submit whatever you have, regardless of whether you are finished. Please indicate in a comment at the bottom of your file how long you spent on the problem. It is important that you are honest about how long each problem took you as it will help your mentor help you!

### Question 1: ZeroSum

Given an array of integers, return the number of pairs of integers in the array that sum to 0 assuming you can use the element at each index at most once.

Examples:

```text
Input Array: [1, 10, 8, 3, 2, 5, 7, 2, -2, -1]
Output: 2
(Pairs: (1, -1), (2,-2))

Input Array: [1, 10, 8, -2, 2, 5, 7, 2, -2, -1]
Output: 3
(Pairs: (1, -1), (2,-2), (2,-2))

Input Array: [4, 3, 3, 5, 7, 0, 2, 3, 8, 6]
Output: 0

Input Array: [4, 3, 3, 5, 7, 0, 2, 3, 8, 0]
Output: 1
(Pairs: (0, 0))
```

Follow-Up: Now assume you can re-use elements in different pairs (i.e., the elements in a pair must be from different indices but different pairs may use an element form the same index).

Examples:

```text
Input Array: [1, 10, 8, 3, 2, 5, 7, 2, -2, -1]
Output: 3
(Pairs: (1, -1), (2,-2), (2,-2))

Input Array: [1, 10, 8, -2, 2, 5, 7, 2, -2, -1]
Output: 5
(Pairs: (1, -1), (2,-2), (2,-2), (2,-2), (2,-2))

Input Array: [4, 3, 3, 5, 7, 0, 2, 3, 8, 6]
Output: 0

Input Array: [4, 3, 3, 5, 7, 0, 2, 3, 8, 0]
Output: 1
(Pairs: (0, 0))
```

### Question 2: UniqueSum

Given an array of integers, return the sum of unique elements in the array.

Examples:

```text
Input Array: [1, 10, 8, 3, 2, 5, 7, 2, -2, -1]
Output: 33 (1+10+8+3+2+5+7+-2+-1)

Input Array: [4, 3, 3, 5, 7, 0, 2, 3, 8, 6]
Output: 35 (4+3+5+7+0+2+8+6)
```

### Question 3: FirstOccurrence

Given a string, return a string that contains only the first occurrence of each character in the string.

Examples:

```text
Input String: "abracadabra"
Output: "abrcd"

Input String: "Uber Career Prep"
Output: "Uber CaPp"

Input String: "zzyzx"
Output: "zyx"
```
