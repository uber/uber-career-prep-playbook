# Practice Assignment 4 Solution Guide: Tries & Repeated Computation

Read [Practice Assignment 4](assignment-4.md) to see the instructions given to the fellows, input/output examples accompanying the problem statements, and summaries of the problem-solving techniques the fellows are asked to identify and use. Please see the UCP Workshop 3 Technical Session deck for details on each of these problem-solving techniques.

### Question 1: Build a Trie

Implement a trie class, including the insert, search, and delete methods. Your class should adhere to the following API, adjusted appropriately for your language of choice.

**Approach:**

*Insert:* Traverse the word in parallel with the trie. For each letter, look up the corresponding location in the current node’s array. If it does not already contain a node, create one. When the end of the word is reached, mark the current node as a valid word.

*Remove:* Traverse the word in parallel with the trie. For each letter, look up the corresponding location in the current node’s array. When the end of the word is reached, un-mark the current node as a valid word. An improvement is to store the traversed nodes in a stack; once the end of the word is reached, if it has no children, remove it from its parent (the top node on the stack). Then pop the stack and repeat, also checking to ensure the node isn’t a valid word. Return once a node that is a valid word or has children is reached or the entire stack is popped.

*Is Valid Word:* Traverse the word in parallel with the trie. For each letter, look up the corresponding location in the current node’s array. If it does not already contain a node, return false. If the end of the word is reached, return the valid word marker at the terminal node.

### Question 2: Boggle

Boggle is a word game in which players compete to find the most words on a square grid of random letters. Valid words must be at least three characters and formed from non-overlapping (i.e., a position on the board can only be used once in a word) adjacent (including diagonal) letters. Given a Boggle board and a dictionary of valid words, return all valid words on the board.

**Technique:** Trie as a parameter

**Approach:** For a full write-up and sample code see [Boggle](https://www.geeksforgeeks.org/boggle-using-trie/)**.**

Accept the dictionary as a trie. Initialize a set of words. Use a nested loop to iterate through the Boggle board (matrix), using each as a starting letter. For each starting letter, initialize a visited set to contain the starting location and a current word to the starting letter. Perform a DFS from the starting node, adding each visited letter to the visited set and current word before making the recursive call. Traverse the trie in parallel; if the current word corresponds to a valid word, add it to the word set; if it is not on an existing path in the trie, return early. Reset the current word and visited set before performing the next DFS. Return the word set.

**Big O:** O(2^n) time (this is is still the upper bound, or worst case, but in practice using the trie dramatically improves this because very few letter combinations are valid word prefixes), O(n) space

### Question 3: Running Median

You are given an array of numbers representing a stream received one by one. Return an array representing the median after each new number is received.

**Technique:** Maintain two heaps

**Approach:** For a full write-up and sample code see [RunningMedian](https://www.geeksforgeeks.org/median-of-stream-of-integers-running-integers/)**.**

Initialize a min heap, a max heap, an array of medians, a current median to 0. Iterate through the input array. For each element is received, do the following:

1. If the element is greater than the current median, add it to the min heap. Otherwise, add it to the max heap.
2. If the size of the heaps differs by more than one, remove the top element from the larger heap and add it to the smaller heap.
3. If the heaps are the same size, the current median is the mean of the tops of the heaps. Otherwise, the median is the top of the larger heap. Add the current median to the array and update the median element.

Return the array of medians.

**Big O:** O(nlogn) time, O(n) space

### Question 4: Catalan Numbers

The Catalan numbers are a mathematical sequence of numbers. The nth Catalan number is defined as (2n)! / (n+1)!n!. Given a non-negative integer n, return the Catalan numbers 0-n.

**Technique:** Dynamic programming; either tabulation or memoization works but tabulation is slightly preferable because it lacks the recursive overhead

**Approach:** For a full write-up and sample code see [CatalanNumbers](https://www.geeksforgeeks.org/program-nth-catalan-number/)**.**

Approach 1: Initialize an array of size n+1. Set the indices 0 and 1 to have the value 1 (the 0th and first Catalan numbers are one). Iterate from 2 to n, inclusive, to find the value for each index, i, in this range. In an inner loop, increment j from 0 to i, exclusive; add the product of the the values at indices j and i - j -1 to the value for i. Return the array.

Approach 2: This approach requires the mathematical observation that the formula for the nth Catalan number can be simplified to the product of the (n-1)th Catalan number and (4n - 2) / (n + 1). We don’t expect this approach. Iterate from 2 to n, inclusive, calculating each number based on the previous one.

**Big O:** O(n^2) time, O(n) space (approach 1); O(n) time, O(1) extra space, O(n) space for return value (approach 2)

### Question 5: Min Cost Stair Climbing

A staircase on a hiking trail implements a rather unusual toll system to cover trail maintenance costs. Each stair in the staircase has a different toll which you only have to pay if you step on that stair. Due to the height of the stairs, you can only climb one or two stairs at once. This means that from the ground you must initially step on either stair 0 or stair 1 and that, if there are n stairs, the last stair you step on can be either stair n-1 or n-2. Given an array representing the costs per stair, what is the minimum possible toll you can pay to climb the staircase?

**Technique:** Dynamic programming; either tabulation or memoization works but tabulation is slightly preferable because it lacks the recursive overhead

**Approach:** For a full write-up and sample code see [MinCostStairClimbing](https://www.geeksforgeeks.org/minimum-cost-to-reach-the-top-of-the-floor-by-climbing-stairs/)**.**

Approach 1: Initialize a min cost array of size n+1. Set the min cost for stairs 0 and 1 to their costs. Iterate to calculate the min cost for each index i from 2 to n, setting the min cost at i to the cost for i and plus the minimum of the costs for i - 1 and i -2. Return the value at index n.

Approach 2: Use two variables for the previous two indices (stairs) rather than an array.

**Big O:** O(n) time, O(n) space (approach 1); O(n) time, O(1) space

### Question 6: Word Break

Given a string of characters without spaces and a dictionary of valid words, determine if it can be broken into a list of valid words by adding spaces.

**Technique:** Trie as a parameter; this can also be done with [dynamic programming](https://www.geeksforgeeks.org/word-break-problem-dp-32/) but the complexity is worse (and it is harder to implement)

**Approach:** For a full write-up and sample code see [WordBreak](https://www.geeksforgeeks.org/word-break-problem-trie-solution/)**.**

Approach: Accept the dictionary as a trie. Create a boolean array indicating indices that have already been checked (and failed). Iterate from the start of the string and traverse the trie in parallel, doing the following:

1. If the current word is a valid word in the trie, if the next index has not already been visited, recurse with it as the start of the string. . When a valid word is found, recurse on the remainder of the string. If the next character is ever not

**Big(O):** O(n\*m) time where m is the longest word in the dictionary, O(n) space

### Question 7: Largest Square of 1s

Given a square matrix of 0s and 1s, find the dimension of the largest square consisting only of 1s.

**Technique:** Dynamic programming; either tabulation or memoization works but tabulation is slightly preferable because it lacks the recursive overhead

**Approach:** For a full write-up and sample code see [LargestSquareOf1s](https://www.geeksforgeeks.org/maximum-size-sub-matrix-with-all-1s-in-a-binary-matrix/#)**.**

Create a DP matrix of the same size as the original. Copy the first row and first column. Use two nested loop to iterate through the rest of the matrix. For each location, if the element is 0, set the DP value to 0. Otherwise, set the DP value to setting each location DP\[i\]\[j\] to one plus the minimum of DP\[i\]\[j-1\] and DP\[i-1\]\[j\]. Iterate through the DP matrix and find the maximum value. Return it.

**Big O:** O(n\*m) time, O(n\*m) space

### Question 8: Coin Change

Given a list of coin denominations and a target sum k, return the number of possible ways to make change for that sum.

**Technique:** Dynamic programming; either tabulation or memoization works but memoization is preferable because not all sub-results are necessary to compute the final result

**Approach:** For a full write-up and sample code see [CoinChange](https://www.geeksforgeeks.org/coin-change-dp-7/)**.**

Initialize a DP map of maps. The key i in the outer map represents the first i coins used to make the sum j, the key in the inner map. Use a recursive helper function that accepts a number of coins, n, and a sum k in addition to the coin values and DP map. Each time the recursive function is called, do the following:

1. If the sum k is 0 return 1.
2. If the number of coins n is 0 return 0.
3. If the number of coins and sum is already in the DP map, return it.
4. Otherwise, make two recursive calls: n coins and sum-coins\[n-1\] (the value of the nth coin); and n-1 coins and sum. Set the value in the DP map to the sum of the two recursive calls and return it.

**Big O:** O(n\*k) time, O(n\*k) space

### Question 9: Adopt a Pet

An animal shelter that houses cats and dogs wants to ensure no pet has to wait too long for a forever home. Therefore, anyone who comes to adopt a pet can pick the species (cat or dog) but not the specific animal; they are assigned the animal of that species that has been in the shelter longest. If there are no animals available of the desired species, they must take the other species. You are given a list of pets in the shelter with their names, species, and time in the shelter at the start of a week. You receive a sequence of incoming people (to adopt pets) and animals (new additions to the shelter) one at a time. Print the names and species of the pets as they are adopted out.

**Technique:** Maintain two queues

**Approach:**

Create a queue for each cats and dogs. Sort the initial input by time in descending order and iterate through it, inserting into the appropriate queue based on pet species. Thereafter, when a new pet is received add it the appropriate queue. Remove and print the front of the appropriate queue if a person arrives; be sure to remove from the non-empty queue if the requested queue is empty.

**Big O:** O(1) time for each pet/person arrival, O(n) overall, O(n) space
