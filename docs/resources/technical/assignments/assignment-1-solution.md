# Practice Assignment 1 Solution Guide: Arrays & Strings

Read [Practice Assignment 1](assignment-1.md) to see the instructions given to the fellows, input/output examples accompanying the problem statements, and summaries of the problem-solving techniques the fellows are asked to identify and use. Please see the UCP Workshop 1 Technical Session deck for details on each of these problem-solving techniques.

### Question 1: Max Mean Sub Array

Given an array of integers and an integer, k, find the maximum mean of a subarray of size k.

**Technique:** Fixed-size sliding window

**Approach:** For a full write-up and sample code see [MaxMeanSubArray](https://www.geeksforgeeks.org/find-maximum-average-subarray-of-k-length/).

1. Create an auxiliary sums array of the same size as the original, or, equivalently, a map of indices to integers. Iterate through the array; for index i, store the sum of the element at i plus the sum at i-1 in the auxiliary array at index i in the sums array (in other words, each index i in the sums array represents the sum from index 0 to index i). Initialize a max sum variable to sums\[k-1\]. Starting at index k, iterate through the sums array, for each index i comparing the difference sums\[i\] - sums\[i-k\] to the max sum and updating it when appropriate.
2. Compute the sum of the first k elements (indices 0 through k-1). Initialize a max sum variable to this sum. Iterate over the array starting at index k. For each index i, subtract the element at i-k from the sum and add the element at i. Compare the max sum to the new sum and update it when appropriate.

**Big O:** O(n) time, O(n) space (approach 1) or O(1) space (approach 2)

### Question 2: Reverse Vowels

Given a string, reverse the order of the vowels in the string.

**Technique:** Forward-backward two-pointer

**Approach:** For a full write-up and sample code see [ReverseVowels](https://www.geeksforgeeks.org/reverse-vowels-given-string/).

Initialize a forward pointer to index 0 and a backward pointer to index n-1 where n is the length of the string. While the forward index is less than the backward index, repeat the following steps:

1. Advance the forward index until it is on a vowel.
2. Advance the backwards index until it is on a vowel.
3. Swap the elements at the forward and backwards indices.
4. Increment the forward index.
5. Decrement the backwards index.

**Big O:** O(n) time, O(1) space

### Question 3: Zero Sum Sub Arrays

Given an array of integers, count the number of subarrays that sum to zero.

**Technique:** Hash the running computation

**Approach:** For a full write-up and sample code see [ZeroSumSubArrays](https://www.geeksforgeeks.org/print-all-subarrays-with-0-sum/). (Note: linked write-up asks to print all subarrays with void output; we ask to return the number of subarrays with no printing.)

Initialize a map of sums to counts. Initialize a running sum to zero. Initialize a count of arrays to zero. Iterate through the array, adding the current element to the running sum. Check if the running sum is already in the map. If so, add the current value for the running sum to the count of arrays, then increment the value. Otherwise, add the sum to the map with a value of one.

**Big O:** O(n) time, O(n) space

### Question 4: Backspace String Compare

Given two strings representing series of keystrokes, determine whether the resulting text is the same. Backspaces are represented by the '#' character so "x#" results in the empty string ("").

**Technique:** Simultaneous iteration two-pointer

**Approach:** For a full write-up and sample code see [BackspaceStringCompare](https://leetcode.com/problems/backspace-string-compare/editorial/).

Initialize two pointers, one in each string, to the last index. While the two pointers are both greater than or equal to zero, repeat the following steps:

1. If the characters at the two pointers are the same and not \#, decrement both pointers.
2. If the characters at the two pointers are different and neither is \#, return false.
3. If either or both characters are \#, decrement that pointer until the next character is not \#, keeping a count k of the \# characters encountered. While k is not 0, repeat the following:
    1. Decrement the pointer.
    2. If the current character is not \#, decrement k.

If both pointers are -1, return true. Otherwise, return false.

**Big O:** O(n) time, O(1) space

### Question 5: Shortest Substring

Given a string and a second string representing required characters, return the length of the shortest substring containing all the required characters.

**Technique:** Growing/shrinking sliding window

**Approach:** For a full write-up and sample code see [ShortestSubstring](https://www.geeksforgeeks.org/smallest-window-contains-characters-string/).

Initialize a map of characters to counts. Initialize start and end indices and a character count to infinity (max int). Convert the string of required characters to a set. Increment the end index, checking if the at that index character to see if it is in the required set. If it is, increment its count in the map (or add it to the map with a count of one if not already present). When the size of the map equals the size of the required set, set the character count to the length of the string between the start and end indices, inclusive. Stop incrementing the end index, and increment the start index, checking if the at that index character to see if it is in the required set. If it is, decrement its count in the map (or remove it if its count is one). When the size of the map is no longer the size of the required set, set the character count to the length of the string between the start and end indices plus one, inclusive. Stop incrementing the start index, and repeat the process until the string is exhausted.

**Big O:** O(n) time, O(n) space

### Question 6: Missing Integer

Given an integer n and a sorted array of integers of size n-1 which contains all but one of the integers in the range 1-n, find the missing integer.

**Technique:** Binary search variation

**Approach:** For a full write-up and sample code see [MissingInteger](https://www.geeksforgeeks.org/find-the-missing-number-in-a-sorted-array/).

Perform a binary search the with following conditions:

1. Missing integer found: the difference between the current element and the previous element is two rather than one. Return the integer between the two elements.
2. Reduce search space to the left half of the array (decrease upper bound): the difference between the current (middle) element and its index is two.
3. Reduce search space to right half of array (increase lower bound): the difference between the current (middle) element and its index is one.

**Big O:** O(logn) time, O(1) space

### Question 7: K Anagrams

Two strings are considered to be “k-anagrams” if they can be made into anagrams by changing at most k characters in one of the strings. Given two strings and an integer k, determine if they are k-anagrams.

**Technique:** Increment/decrement counts

**Approach:** For a full write-up and sample code see [KAnagrams](https://www.geeksforgeeks.org/check-two-strings-k-anagrams-not/).

Return false if the strings are not the same length. Initialize a map of characters to counts. Iterate through one string, increasing the count of each character encountered. Iterate through the second string, decreasing the count of each character encountered. Initialize a count of differences to zero. Iterate through the values in the map, adding the absolute value of every value to the difference count. Return true if the final difference count is less than or equal to k and false otherwise.

**Big O:** O(n) time, O(n) space

### Question 8: Merge Intervals

Given a list of integer pairs representing the low and high end of an interval, inclusive, return a list in which overlapping intervals are merged.

**Technique:** Sort, then solve

**Approach:** For a full write-up and sample code see [MergeIntervals](https://leetcode.com/problems/merge-intervals/editorial/).

Initialize a list of merged intervals. Sort the pairs by the first value (start of the interval). Initialize a start value to the start of the first interval. Repeat the following steps until the list is exhausted:

1. If there is no next interval, add the saved start value and end value of the current interval to the merged list.
2. If the end of the next interval is greater than the end of the current interval, add the saved start value and end value of the current interval to the merged list. Move to the next interval and reset the start value to its start.
3. If the end of the next interval is less than or equal to the end of the current interval, move to the next interval without resetting the start value.

(Equivalently, you can sort by the second value, or end of the interval, and iterate backwards starting at the last interval, checking whether the end of the the previous interval is less than the start of the current interval.)

**Big O:** O(nlogn) time, O(1), O(logn), or O(n) space for sorting depending on the algorithm, O(n) for return value

### Question 9: Dedup Array

Given a sorted array of non-negative integers, modify the array by removing duplicates so each element only appears once. If arrays are static (aka, not dynamic/resizable) in your language of choice, the remaining elements should appear in the left-hand side of the array and the extra space in the right-hand side should be padded with -1s.

**Technique:** Two-pointer with “catch-up” condition

**Approach:** For a full write-up and sample code see [DedupArray](https://www.geeksforgeeks.org/remove-duplicates-sorted-array/)**.** Initialize a leading and trailing pointer to 0. Increment the leading pointer; if the element at that index is not the same as the previous element, increment the trailing pointer and set the element at its index to the element at the leading index. Repeat until the leading pointer reaches the final index; increment the trailing pointer and set it to the last element. The final position of the trailing pointer indicates the end of the updated array.

**Big O:** O(n) time, O(1) space
