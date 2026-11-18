# Cohort Selection Technical Interviews

Resources for the technical interviews used to select the cohort: tips for interviewers and the question bank, with follow-ups and possible solutions for each question.

## Tips for Technical Interviewers

1. Do the problems ahead of time!
2. Give your candidate an example of an input and the correct solution.
3. Answer clarifying questions. If the problem doesn’t say, feel free to decide what you want and go with it!
4. Nervous or overeager candidates tend to jump right into coding or trying to write something down. If this happens, ask your candidate to talk through their ideas first.
5. If your candidate is quiet, ask them to talk through their ideas aloud. If there’s a silence of more than a couple of minutes, get your candidate talking again.
6. That said, give your candidate time to think. This is one of the hardest parts of being an interviewer – there are often a lot of pauses and it can be awkward or painful. Two minutes of quiet can feel like a very long time.
7. If you’re not sure if the candidate is stuck or just thinking and quiet, ask your candidate to explain what they’re thinking. This will help you avoid giving premature or unnecessary hints.
8. If the candidate is making progress, stay quiet. Sometimes it’s also hard to keep your mouth shut, and it can feel weird to sit there and observe in silence, but when the candidate is excelling, the interviewer does very little talking!
9. Take notes! *Note things that go well and poorly so you can write your full feedback afterwards without interrupting the flow or atmosphere of the interview.* Also write down how long the candidate spends on each part (developing the initial algorithm, translating it into code, testing, etcetera) to understand where they struggle and excel.
10. Encourage the candidate to work through examples by hand and/or draw an illustration of the problem if they’re confused or stuck.
11. Brainstorm “little hints”, “medium hints”, and “big hints” you can give if the candidate gets stuck. “Little hints” tend to be open-ended (i.e., “how would you do this problem if you were solving it by hand?”) while “big hints” point the candidate to the correct algorithm (i.e., “what would happen if you used data structure X instead of data structure Y?) While “medium hints” unsurprisingly are somewhere in the middle (for example, they might indicate the area in which you want to make a change without giving away the specific change, such as “is there another data structure you could use instead?”).
12. If they’re stuck, help them talk about their thoughts so far before giving a hint. Often talking through the problem will get an candidate unstuck without any hints by acting as a “rubber duck.” Questions like “and then what?” or “what about when…?” without bringing in any new information are often sufficient to keep the ideas and words flowing.
13. If you do have to give hints, give them one at a time, in increasing order of difficulty (i.e., start with a “small hint” and only work up to a “big hint” if the candidate is still stuck and running out of time). Leave plenty of space between the hints to give the candidate time to work with them.
14. Keep track of the time! When time is almost up, tell your candidate you’re almost out of time, and ask them to wrap up their solution as best as possible, such as by explaining what they would do if they had more time. It helps you get a sense of how their thinking has progressed and creates a better experience for them.

## Question Bank

### 1. Palindromes & Anagrams

#### Problem

A palindrome is a word, phrase, or sequence that reads the same backward as forward. An example of some palindromes are “kayak,” “racecar,” and "rats live on no evil star.” Write a function that takes a string as an input and returns a boolean indicating if the string is a palindrome (the same forwards and backwards) ignoring capitalization, spaces and characters that are not letters.

##### Function Definition

```text
is_palindrome(str) -> bool
str: string
bool: boolean
```

##### Example Input/Output

```text
Input 1: "noon"
Output 1: True
Input 2: ""
Output 2: True
Input 3: "kayak"
Output 3: True
Input 4: "no"
Output 4: False
Input 5: "step on no pets"
Output 5: True
Input 6: "Was it a car or a cat I saw?"
Output 6: True
```

##### Possible Solutions

1. Simultaneously iterate over the string forwards and backwards comparing each character. If two characters do not match, return false. If the middle is reached, return true. \[Complexity: Optimal; Time: O(n); Space: O(1)\]
2. Recursive. Compare the first and last characters, returning false if they do not match. Recurse on the remainder of the string until a base case (string of length zero or one) is reached. If the base case is reached, return true. \[Complexity: Brute Force; Time: O(n); Space: O(n)\]
3. Reverse the string, then compare the reversed and original the same. Return true if they are the same, false otherwise. \[Complexity: Brute Force; Time: O(n); Space: O(n)\]

*If the candidate codes any of these solutions, move on to follow-up 1.*

*Note: In both the original problem and both follow-ups, boolean flags in the solution can be substituted with an integer count. Additionally, completely correct solutions will ignore characters that are not letters and lowercase (or uppercase) all letters. This is left out of the problem statement to ensure candidates ask identify edge cases and ask appropriate clarifying questions instead of making assumptions. If original solutions do not account for this, remind candidates of this requirement and see if they can update their solution. If they do not make progress in five minutes, this is the one instance in which it is okay to move on without the candidate completing the problem.*

#### Follow-Up 1

An anagram is a word or phrase formed by rearranging the letters of another. An example of some anagrams are “act” and “cat”; “auctioned” and “cautioned”; and “a gentleman” and “elegant man.” Write a function that takes two strings as input and returns a boolean indicating if the strings are anagrams (the same letters in different orders).

##### Function Definition

```text
are_anagrams(str1, str2) -> bool
str1, str2: string
bool: boolean
```

##### Example Input/Output

```text
Input 1: "noon", "no"
Output 1: False
Input 2: "on", "no"
Output 2: True
Input 3: "state", "taste"
Output 3: True
Input 4: "teen", "ten"
Output 4: False
Input 5: "the eyes", "they see"
Output 5: True
Input 6: "William Shakespeare", "I'll make a wise phrase"
Output 6: True
```

##### Possible Solutions

1. Make a map of character to integer. Iterate through string 1, incrementing the count for each character. Iterate through string 2, decrementing the count for each character. Iterate over the map; return false if any value is not 0. Return true if the end is reached. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
2. Sort both strings, then compare the sorted strings. Return true if they are the same, false otherwise. \[Complexity: Good; Time: O(nlogn); Space: O(n)\]
3. Generate every possible permutation of string 1 and compare each to string 2. Return true if they are the same. If all permutations are checked, return false. \[Complexity: Terrible; Time: O(n!), Space: O(n!)\]

*If the candidate codes solution (1) or (2) move on to follow-up 2. If the candidate proposes solution (3), guide them towards brainstorming other solutions rather than coding it. Do not move on until a viable solution has been coded.*

#### Follow-Up 2

Now combining the ideas from the previous two parts, the final goal is to determine if a string can be rearranged to form a palindrome. Write a function that takes a string as input and returns a boolean indicating if it is an anagram of a palindrome. *Note: if the candidate needs a hint, suggest that rather than trying to use the functions in the previous part, think about what makes a string a palindrome and what makes two strings anagrams.*

##### Function Definition

```text
is_palindrome_anagram(str) -> bool
str: string
bool: boolean
```

##### Example Input/Output

```text
Input 1: "noon"
Output 1: True
Input 2: ""
Output 2: True
Input 3: "dada"
Output 3: True
Input 4: "no"
Output 4: False
```

##### Possible Solutions

1. Create a map of counts. Iterate over the string, incrementing the count of each character. Initialize a boolean to false to keep track of whether an odd character has been seen. Iterate over the map. If the count is odd and the boolean is already true, return false. If the count is odd and the boolean is still false, update to true. Return true after completing the loop. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
2. Create a set of characters. Iterate over the string. For each character, if the character is in the set, remove it, and if it is not in the set, add it. Return true if the set is of size 0 or 1, false otherwise. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
3. Initialize a count array of characters (index is integer of character). Iterate over the string and increment the count of every character. Initialize a boolean to false to keep track of whether an odd character has been seen. Iterate over the array. If the count is odd and the boolean is already true, return false. If the count is odd and he boolean is still false, update to true. Return true after completing the loop. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
4. Sort the string. Initialize a boolean to false to keep track of whether an odd character has been seen. Iterate over the sorted string, counting occurrences of each character. If the count is odd and the boolean is already true, return false. If the count is odd and the boolean is still false, update to true. Return true after completing the loop. \[Complexity: Good, Time: O(nlogn); Space: O(n)\]
5. Use two nested loops to iterate over the string. Initialize a boolean to false to keep track of whether an odd character has been seen. For each character, count the number of times the character appears. If odd and the boolean is already true, return false. If the count is odd and the boolean is still false, update to true. Return true after completing both nested loops. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]
6. Generate every possible permutation of the string and check whether it is a palindrome. Return true if one is. If all permutations are checked, return false. \[Complexity: Terrible; Time: O(n!), Space: O(n!)\]

*If the candidate codes solution (1), (2), (3), or (4), move on to another question, time permitting. If the candidate codes solution (4), see if you can guide them towards (1), (2), or (3) before moving on. However, if they do not make progress after ~5 minutes, move on. If the candidate proposes solution (5), guide them towards brainstorming other solutions rather than coding it. Do not move on until a viable solution has been coded.*

### 2. Special Array Elements

#### Problem

Determine if an array has a majority element (element that appears \> n/2 times, where n is the length of the array).

##### Function Definition

```text
has_majority_element(arr) -> int
arr: array of integers
int: integer element in arr
```

##### Example Input/Output

```text
Input 1: [2, 4, 2, 5, 2, 2, 4]
Output 1: 2
Input 2: [2, 2, 5, 2, 2, 4]
Output 2: 2
Input 3: [4, 2, 5, 2, 2, 4, 3]
Output 3: NULL
Input 4: [2, 4, 5, 3, 2, 4]
Output 4: NULL
```

##### Possible Solutions

1. Create a map of characters to counts. Increment the counts iterating through the array. Check if any of the counts exceed n/2; if so, a majority element has been found. This solution may be improved by returning early if incrementing a count causes it to cross the n/2 threshold. It can even be further optimized by returning NULL early if there are not sufficient elements remaining to find a majority element. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
2. Sort the array. Iterate through the sorted array, counting each character. If a count is greater than n/2, a majority element has been found. \[Complexity: Good; Time: O(nlogn); Space: O(n)\]
3. Iterate over the array. For each character, use a nested loop to iterate over the array, counting the number of occurrences. If the number of occurrences is greater than n/2, a majority element has been found. This solution may be improved somewhat by only checking characters in the first half of the array. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]

*If the candidate codes solution (1) or (2), move on to follow-up 1. If the candidate codes solution (3), see if you can guide them towards (1) or (2) before moving on. However, if they do not make progress after ~5 minutes, move on.*

#### Follow-Up 1

Determine if an array has a plurality element (element that appears more than any other element).

##### Function Definition

```text
has_plurality_element(arr) -> int
arr: array of integers
int: integer element in arr
```

##### Example Input/Output

```text
Input 1: [2, 4, 2, 5, 2, 3, 4]
Output 1: 2
Input 2: [2, 4, 1, 5, 2, 3, 4]
Output 2: NULL
Input 3: [4, 2, 5, 2, 2, 4]
Output 3: 2
Input 4: [4, 2, 4, 2, 2, 4]
Output 4: NULL
```

##### Possible Solutions

1. Iterate over the array to create a map of elements to counts. Iterate over the map, keeping track of the maximum and a boolean to indicate whether it is unique. At the end, the unique boolean indicates whether a plurality element has been found. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
2. Sort the array and keep track of a maximum count and a unique max boolean. Iterate through the sorted array, counting each character. If the number of occurrences is greater than the current max, update the maximum and set the unique max to true. If the number of occurrences is the same as the current max, set the unique max to false. At the end, the unique max indicates whether a plurality element has been found. \[Complexity: Good; Time: O(n\*logn); Space: O(n)\]
3. Iterate over the array and keep track of a maximum count and a unique max boolean. For each character, use a nested loop to iterate over the array, counting the number of occurrences. If the number of occurrences is greater than the current max, update the maximum and set the unique max to true. If the number of occurrences is the same as the current max, set the unique max to true. At the end, the unique max indicates whether a plurality element has been found. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]

*If the candidate codes solution (1) or (2), move on to follow-up 2. If the candidate codes solution (3), see if you can guide them towards (1) or (2) before moving on. However, if they do not make progress after ~5 minutes, move on.*

#### Follow-Up 2

Determine if an array has an equilibrium index (index where the sum of all elements to the left equals the sum of all elements to the right).

##### Function Definition

```text
has_equilibrium_index(arr) -> int
arr: array of integers
int: integer index in arr
```

##### Example Input/Output

```text
Input 1: [1, 4, 2, 5, 2, 3, 2]
Output 1: 3
Input 2: [1, 4, 2, 2, 3, 2]
Output 2: NULL
Input 3: [8, 2, 3, 1, 5, 4]
Output 3: 2
Input 4: [6]
Output 4: 0
```

##### Possible Solutions

1. Iterate over the array left-to-right creating an array of cumulative left sums (excluding the current index). Also iterate over the array right-to-left creating an array of cumulative right sums (also excluding the current index). Iterate over the indices once more, checking both the left and right sum arrays. Return true if the left and right sums are equal. Return false if the end is reached. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
2. Iterate over the indices of the array. For each index, use a nested loop to sum the elements to the left and right of the index. Return the index if they are equal. Return NULL if the end of the nested loops are reached. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]

*If the candidate codes solution (1), move on to another question, time permitting. If the candidate codes solution (2), see if you can guide them towards (1) before moving on. However, if they do not make progress after ~5 minutes, move on.*

### 3. Array Arrangement

#### Problem

Write a partition function that rearranges an array containing odd and even numbers in-place (without creating a new array or sorting the array) so that all odd numbers come before all the even numbers. If the candidate uses a language that does not support pass-by-reference, have them print the resulting array rather than returning it to keep space at O(1).

##### Function Definition

```text
parition_ints(arr) -> void
arr: array of integers
```

##### Example Input/Output

```text
Input 1: [1, 4, -2, 3, 9, 8, -6, 0]
Output 1: [1, 9 ,3, -2, 4, 8, -6, 0]
Input 2: [8, -8, 12, 10, 0]
Output 2: [8, -8, 12, 10, 0]
```

##### Possible Solutions

1. Iterate forwards and backwards through the array simultaneously. Stop the forwards iteration when an even number is reached and the backwards iteration when an odd number is reached. Swap them. Advance both pointers. Continue until the forwards and backwards indices cross. \[Complexity: Optimal; Time: O(n); Space: O(1)\]
2. Iterate through the array. At each index, if it contains an even element, iterate through the rest of the array until an odd element is found and swap them. When no element to swap with is found or the iteration ends the process is complete. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]
3. Iterate through the array. At each index, if it contains an even element, save that element in a temp value and shift all elements to the right of it one to the left. Insert that element into the end slot in the array \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]

*If the candidate proposes the solution in which a new array is created and first the even numbers are copied and then the odds, remind them of the in-place requirement and guide them towards one of the other solutions before they code. If the candidate codes solution (1), move on to follow-up 1. If the candidate codes solutions (2) or (3) see if you can guide them towards (1) before moving on. However, if they do not make progress after ~5 minutes, move on.*

#### Follow-Up 1

Now suppose we want to separately partition zeros. In the partitioned array, zeros should be between the odd and the other even integers. Again, if the candidate uses a language that does not support pass-by-reference, have them print the resulting array rather than returning it to keep space at O(1).

##### Function Definition

```text
partition_ints(arr) -> void
arr: array of integers
```

##### Example Input/Output

```text
Input 1: [1, 4, -2, 3, 9, 8, -6, 0]
Output 1: [1, 9, 3, 0, -2, 8, -6, 4]
Input 2: [8, -8, 12, 10, 0]
Output 2: [0, -8, 12, 10, 8]
```

##### Possible Solutions

1. Iterate through the array and count the even and odd integers. Iterate forwards and backwards through the array simultaneously. Stop the forwards iteration when an even number or 0 is reached and the backwards iteration when an odd number or 0 is reached. Swap them. Advance the forwards pointer if it is on an odd number or the index is greater than or equal to the number of odd numbers; advance the backwards pointer if it is on an even number or the index is less than the total elements minus the even elements. Continue until the forwards iteration until and backwards indices cross. \[Complexity: Optimal; Time: O(n); Space: O(1)\]
2. Use two passes. First partition the array into evens and odds or zeros. Iterate forwards and backwards through the array simultaneously. Stop the forwards iteration when an even number is reached and the backwards iteration when an odd number or a zero is reached. Swap them. Advance both pointers. Continue until the forwards and backwards indices cross. Do a second pass, iterating forwards and backwards on the subarray containing odd numbers and zeros (0 through the final position of the backwards pointer) simultaneously. Stop the forwards iteration when a zero is reached and the backwards iteration when an odd number is reached. Swap them. Advance both pointers. \[Complexity: Optimal; Time: O(n); Space: O(1)\] *Note: of course it is possible to instead first partition the array the other way, into evens or zeros and odds.*
3. The brute force swapping solution (2) from the original problem, swapping even and zero elements for odds. Use a flag to indicate whether odd numbers remain. When no more odd numbers remain, continue, swapping evens for zeros. Continue until no more zeros are found or the iteration completes. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]
4. The brute force shifting solution (3) from the original problem. Use a flag to indicate whether odd numbers remain. Shift when a zero or an even element is encountered. When no more odd numbers remain, shift when an even element is encountered. \[Complexity: Brute Force; Time: O(n^2); Space: O(1)\]

*If the candidate proposes the solution in which a new array is created and first the negative numbers are copied, then the zeros, then the odds, remind them of the in-place requirement and guide them towards one of the other solutions before they code. If the candidate codes solution (1) or (2), move on to follow-up 2. If the candidate codes solutions (3) or (4) see if you can guide them towards (1) or (2) before moving on. However, if they do not make progress after ~5 minutes, move on.*

#### Follow-Up 2

Now suppose the array only contains 0s, 1s, and 2s.

##### Function Definition

```text
partition_ints(arr) -> int
arr: array of integers
int: integer index in arr
```

##### Example Input/Output

```text
Input 1: [0, 0, 1, 1, 1, 2]
Output 1: [1, 1, 1, 0, 0, 2]
Input 2: [2, 0, 0, 0, 0, 0]
Output 2: [0, 0, 0, 0, 0, 2]
```

##### Possible Solutions

1. Count each element and store the results in a map. Initialize a sorted constant array of the three possible elements. Initialize an index counter to zero. Iterate over the constant array, looking up the count of each element in the map and overwriting the appropriate number of indices in the original array with the element from the constant array. \[Complexity: Optimal; Time: O(n); Space: O(1)\]
2. Count each element and store the results in variables. Initialize an index counter to zero. In the correct order, go through the variables and overwrite the appropriate number of indices in the original array with the element the variable represents. \[Complexity: Optimal; Time: O(n); Space: O(1)\] *Note: while the complexity of this solution is the same as (1), it is much messier as it uses three variables instead of a data structure and relies on the knowledge of “magic numbers.”*
3. Any of the solutions from follow-up (1) will also work. \[Complexity: Varies\]

*If the candidate proposes the solution in which a new array is created and first the negative numbers are copied, then the zeros, then the odds, remind them of the in-place requirement and guide them towards one of the other solutions before they code. If the candidate proposes (3), this is good insight but ask if it can be improved upon by using the additional constraints in the follow-up if they do not suggest doing so themselves. Do not move on until the candidate codes solution (1) or (2). If the candidate codes solution (2), see if you can guide them towards solution (1) before moving on to another question. However, if they do not make progress after ~5 minutes, move on.*

### 4. Array Arithmetic

#### Problem

Given an array of integers, create an array where each index has the sum of all the elements in the original array except for the element at that index.

##### Function Definition

```text
other_sum_array(arr) -> sum_arr
arr: array of integers
sum_arr: array of integers
```

##### Example Input/Output

```text
Input 1: [0, 1, 2, 3, 4, 5]
Output 1: [15, 14, 13, 12, 11, 10]
Input 2: [8]
Output 3: [0]
```

##### Possible Solutions

1. Iterate over the array and sum the elements. Iterate again and for each element subtract that element from the sum. Add the difference to the results array. \[Complexity: Optimal; Time: O(n); Space: O(1)\]
2. Iterate over the array forwards and backwards to create partial forward sum and backward sum arrays such that each index contains the sum of all the elements before but not including that index. Iterate over the indices once more. The result for each index is the sum of partial forward sum and partial backward sum for that index. \[Complexity: Almost Optimal; Time: O(n); Space: O(n)\]
3. Use a nested loop to iterate over the indices. For each index, iterate over the array, summing all the elements except the one at that index. \[Complexity: Brute Force; Time: O(n^2); Space: O(n)\]

*If the candidate codes solution (1) or (2), move on to follow-up 1. If the candidate codes solution (3), see if you can guide them towards (1) or (2) before moving on. However, if they do not make progress after ~5 minutes, move on.*

#### Follow-Up 1

Now create an array where each index has the product of all the elements in the original array except for the element at that index.

##### Function Definition

```text
other_product_array(arr) -> prod_arr
arr: array of integers
prod_arr: array of integers
```

##### Example Input/Output

```text
Input 1: [0, 1, 2, 3, 4, 5]
Output 1: [120, 0, 0, 0, 0, 0]
Input 2:  [1, 2, 3, 4, 5]
Output 2: [120, 60, 40, 30, 24]
Input 2:  [0, 0, 1, 2, 3, 4, 5]
Output 2: [0, 0, 0, 0, 0, 0, 0]
```

##### Possible Solutions

1. Iterate over the array and multiply the elements. Iterate again and for each element divide the product by that element. The thing that is different, and more challenging, than in the original problem is handling the 0-element case. Keep a set of zero element indices. Do not multiply zero elements. If the final set size is one, set that index to the product and every other index to zero. If the set size is zero, set all indices to zero. Add the difference to the results array. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
2. Iterate over the array forwards and backwards to create partial forward product and backward product arrays such that each index contains the product of all the elements before but not including that index. Iterate over the indices once more. The result for each index is the product of partial forward product and partial backward product for that index. \[Complexity: Optimal; Time: O(n); Space: O(n)\]
3. Use a nested loop to iterate over the indices. For each index, iterate over the array, multiplying all the elements except the one at that index. \[Complexity: Brute Force; Time: O(n^2); Space: O(n)\]

*If the candidate codes solution (1) or (2), move on to follow-up 1. If the candidate codes solution (3), see if you can guide them towards (1) or (2) before moving on. However, if they do not make progress after ~5 minutes, move on.*

#### Follow-Up 2

Now given a 2D array (matrix), create a 2D array (matrix) where each index i,j is the sum of all the indices in the rectangle from 0,0 (upper left corner) to i,j (lower right corner). *Note: this problem can be hard to understand from just words. Show the example and explain how the output is derived from the input.*

##### Function Definition

```text
sum_matrix(mat) -> sum_mat
mat: 2D array of integers
sum_mat: 2D array of integers
```

##### Example Input/Output

```text
Input 1: [1, 2, 3
          4, 5, 6
          7, 8, 9]
Output 1: [1, 3, 6
           5, 12, 21
           12, 27, 45]
```

##### Possible Solutions

1. Iterate over the first row and the first column. Set (r, 0) in the result array to the sum of (r-1, 0) in the result array and (r, 0) in the original array; set (0, c) in the result array to the sum of (0, c-1) in the result array and (0,c) in the original array. Iterate from (1,1), setting (r, c) in the result array to the sum of (r-1, c) + (r, c-1) - (r-1, c-1) in the result array and (r, c) in the original array. \[Complexity: Optimal; Time: O(n)/O(r\*c); Space: O(1)\]
2. For each row-column index, iterate over the matrix up to that row and column summing the elements. Set that index in the result array to this sum. \[Complexity: Brute Force; Time: O(n^2)/O(r^2\*c^2); Space: O(1)\]

*If the candidate codes either solution, move on to another question, time permitting, unless the candidate proposes improving solution (2) to solution (1).*
