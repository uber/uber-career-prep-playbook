# Practice Assignment 2 Solution Guide: Linked Lists & Trees

Read [Practice Assignment 2](assignment-2.md) to see the instructions given to the fellows, input/output examples accompanying the problem statements, and summaries of the problem-solving techniques the fellows are asked to identify and use. Please see the UCP Workshop 2 Technical Session deck for details on each of these problem-solving techniques.

### Question 1: Implement a Singly Linked List

If needed, please refer to the [definition](https://www.geeksforgeeks.org/data-structures/linked-list/singly-linked-list/) and implementation of a singly linked list in the fellow’s language of choice, readily available on the internet.

### Question 2: Implement a Doubly Linked List

If needed, please refer to the [definition](https://www.geeksforgeeks.org/introduction-and-insertion-in-a-doubly-linked-list/) and implementation of a doubly linked list in the fellow’s language of choice, readily available on the internet.

### Question 3: Implement a Binary Search Tree

If needed, please refer to the [definition](https://www.geeksforgeeks.org/binary-search-tree-data-structure/) and implementation of a binary search tree in the fellow’s language of choice, readily available on the internet.

### Question 4: Implement a Queue

**Approach:** Use a singly linked list as the underlying data structure but also store a tail pointer **or** use a doubly linked list. The head of the list represents the front of the queue and the tail represents the back. The enqueue function calls the list’s insertAtBack method and the dequeue function calls the list’s removeAtFront method.

### Question 5: Implement a Stack

**Approach:** Use a singly linked list as the underlying data structure. The head of the list represents the top of the stack and the tail represents the bottom. The push function calls the list’s insertAtFront method and the pop function calls the list’s removeAtFront method.

### Question 6: Implement a Deque

**Approach:** Use a doubly linked list as the underlying data structure. The head of the list represents the front of the deque and the tail represents the back. The pushFront and pushBack functions call the list’s insertAtFront and insertAtBack methods, respectively; the popFront and popBack functions call the list’s removeAtFront and removeAtBack methods, respectively

### Question 7: Copy Tree

Given a binary tree, create a deep copy. Return the root of the new tree.

**Technique:** Pre-order traversal.

**Approach:** For a full write-up and sample code see [CopyTree](https://www.geeksforgeeks.org/clone-binary-tree-random-pointers/)**.** (Note: the linked solution is to clone a binary tree with random pointers; we asked just to clone a binary tree so only the “copyLeftRightNode” portion of the solution is needed.)

Implement a pre-order traversal with the following steps:

1. If the current node is null return null.
2. Make a copy of the current node.
3. Recursively call the pre-order traversal on the left child and set the copy’s left child to the result.
4. Recursively call the pre-order traversal on the right child and set the copy’s right child to the result.

Call the traversal on the root of the tree and return the result.

**Big O:** O(n) time, O(n) space

### Question 8: Is BST

**Technique:** Generic depth-first traversal **or** level-order traversal.

**Approach:** For a full write-up and sample code see [IsBST](https://leetcode.com/problems/validate-binary-search-tree/editorial/)**.**

*Approach 1:*

Implement any depth-first traversal with the following conditions:

1. If the current node is null or has no children, return false.
2. If the current node has a left child and it is greater than the node, return false.
3. If the current node has a right child and it is less than the node, return false.

<!-- -->

5. Recursively call the traversal on the left child and the right child. Return true if both true, false otherwise.

Call the traversal on the root of the tree and return the result.

*Approach 2:*

Implement a level-order traversal that stores the result in an array. Call the traversal, then iterate through the resulting array, checking if it is sorted. Return true if sorted, false otherwise.

**Big O:** O(n) time, O(logn) space (approach 1) or O(n) space (approach 2)

### Question 9: Dedup Sorted List

**Technique:** Linked list reset/catch-up two-pointer

**Approach:** For a full write-up and sample code see [DedupSortedList](https://www.geeksforgeeks.org/remove-duplicates-from-a-sorted-linked-list/)**.**

Initialize a leading and a trailing pointer to the head of the list. While there is a next node and the data in the next node is the same as the data in the current node, advance the leading pointer. Set the trailing pointer’s next node to the leading pointer’s next node. Reset both pointers to the next node. Continue until the list is exhausted. Return the head.

**Big O:** O(n) time, O(1) space

### Question 10: Move Nth Last to Front

**Technique:** Linked list fixed-distance two-pointer

**Approach:** For a full write-up and sample code see [MoveNthLastToFront](https://www.geeksforgeeks.org/delete-nth-node-from-the-end-of-the-given-linked-list/) (Note: the linked solution is to delete the nth to last node but we asked them to move it to the front. The algorithm for finding the nth to last node and re-linking the adjacent nodes is the same; their solution should just have the additional step of updating the head.)

Initialize a leading and a trailing pointer to the head of the list. Advance the leading pointer n times. Advance both pointers until the leading pointer is the tail (its next pointer is null). Save the trailing pointer’s next as the new head. Set the trailing pointer’s next to the new head’s next. Set the new head’s next to the head and return the new head.

**Big O:** O(n) time, O(1) space

### Question 11: Is Palindrome

**Technique:** Doubly linked list forward-backward two-pointer

**Approach:** For a full write-up and sample code see [IsPalindrome](https://www.geeksforgeeks.org/check-doubly-linked-list-characters-palindrome-not/)**.**

Find the tail of the list. Initialize a forward pointer to the head of the list and a backward pointer to the tail of the list. Compare the data at the two pointers. If it is the same, move both pointers. If it is different, return false. If the pointers are the same or the forward pointer’s previous is the backwards pointer (or, equivalent, the backward pointer’s next is the previous pointer), return true. Repeat.

**Big O:** O(n) time, O(1) space

### Question 12: Disconnect Cycle

**Technique:** Hash linked list nodes

**Approach:** For a full write-up and sample code see [DisconnectCycle](https://www.geeksforgeeks.org/detect-and-remove-loop-in-a-linked-list/)**.**

Initialize a set of node pointers. Add the head of the list to the set. Initialize a current pointer to the head. While its next pointer is not in the set, add it to the set and advance the pointer. If the next pointer is in the set, set the next pointer to null. Return the head.

**Big O:** O(n) time, O(n) space

### Question 13: Left View

**Technique:** Level-order (breadth-first) traversal

**Approach:** For a full write-up and sample code see [LeftView](https://www.geeksforgeeks.org/print-left-view-binary-tree/)**.** (Note: the linked solution is to print the left view. We are asking them to return an array containing the left view.)

Initialize an array representing the left view. Conduct a level order traversal using two queues for the current level and the next level. Whenever the current level is reset (i.e., the root is added or the current level is set to the next level), add the first node in the queue to the left view array. When the traversal is completed, return the array.

**Big O:** O(n) time, O(n) space

### Question 14: Floor in BST

**Technique:** Search BST

**Approach:** For a full write-up and sample code see [FloorInBst](https://www.geeksforgeeks.org/floor-in-binary-search-tree-bst/)**.**

Initialize floor to the value that will be returned if there is no floor in the tree. Search the tree for the value. Every time the value you are searching for is greater than the current node (i.e., you will update current to be its right child), set the return value to the current node. If the value is found, return the value. Otherwise, return the saved floor value when current is null (the value is not found).

**Big O:** O(logn) time, O(1) space
