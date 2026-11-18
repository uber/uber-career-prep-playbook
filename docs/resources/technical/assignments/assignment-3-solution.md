# Practice Assignment 3 Solution Guide: Graphs & Data Structure Selection

Read [Practice Assignment 3](assignment-3.md) to see the instructions given to the fellows, input/output examples accompanying the problem statements, and summaries of the problem-solving techniques the fellows are asked to identify and use. Please see the UCP Workshop 3 Technical Session deck for details on each of these problem-solving techniques.

### Question 1: Build an Adjacency List/Set Representation of a Graph

**Approach:**

To get the neighbors of a node, look up the node in the map and iterate through the value (list or set). For a full write-up and sample code see: [DFS](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/); [BFS](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/); [topological sort with Khan’s](https://www.geeksforgeeks.org/topological-sorting-indegree-based-solution/); and [topological sort with DFS](https://www.geeksforgeeks.org/topological-sorting/).

### Question 2: Build a Heap

**Approach:**

Store the heap in an array where the parent of the node at i is located at (i-1)/2 and the children are located at (2\*i)+1 and (2\*i)+2. The root is located at index 0. To add an element, insert at the end of the array and “bubble it up” until it reaches the correct position (i.e., compare it to its parent, and if they are out of order, swap them). To delete the root, swap it with the last element, then “heapify” it (i.e., find the correct parent between it and its two children; if it is not the root, swap it, and repeat on the swapped child). For a full write-up and sample code see [binary heap](https://www.geeksforgeeks.org/binary-heap/).

### Question 3: Build a Priority Queue

**Approach:**

Use a max heap and store a pair of data and a priority (integer) in each location. Use the priority for all comparisons. For a full write-up and sample code see [priority queue](https://www.geeksforgeeks.org/priority-queue-set-1-introduction/).

### Question 4: Number of Islands

Given a binary matrix in which 1s represent land and 0s represent water, return the number of islands (contiguous 1s surrounded by 0s or the edge of the matrix).

**Technique:** Graph, generic traversal

**Approach:** For a full write-up and sample code see [BFS solution](https://www.geeksforgeeks.org/islands-in-a-graph-using-bfs/) or [DFS solution](https://www.geeksforgeeks.org/find-the-number-of-islands-using-dfs/).

Initialize an island count to zero. Conduct either a BFS or DFS traversal starting with an arbitrary node (i.e., location on the grid); choose a corner for simplicity and traverse rows or columns with two nested loops. Every time the search is started with a new, previously unvisited node, increment the island count. When the search is exhausted (the number of visited nodes is the same as the number of locations in the grid), return the count.

**Big O:** O(n) time, O(n) space

### Question 5: First K Binary Numbers

Given a number, k, return an array of the first k binary numbers, represented as strings.

**Technique:** Queue

**Approach:** For a full write-up and sample code see [FirstKBinaryNumbers](https://www.geeksforgeeks.org/interesting-method-generate-binary-numbers-1-n/). (Note: the linked solution starts with “1” as the first binary number but we are asking them to start with “0”. This is a special case because we do not wish to put “0” in the queue and append to it since none of the other numbers start with “0”.)

Initalize a result array with the string “0”. Initalize a count to 1. Initalize a queue and push “1” to the queue. While the count is less than k, add the front of the queue, s, to the array, push s + “0” and s + “1” to the queue, and pop the queue. Increment the count. When the count equals k, return the array.

**Big O:** O(n) time, O(n) space

### Question 6: Road Networks

In some states, it is not possible to drive between any two towns because they are not connected to the same road network. Given a list of towns and a list of pairs representing roads between towns, return the number of road networks. (For example, a state in which all towns are connected by roads has 1 road network, and a state in which none of the towns are connected by roads has 0 road networks.)

**Technique:** Graph, generic traversal

**Approach:** For a full write-up and sample code see [RoadNetworks](https://www.geeksforgeeks.org/connected-components-in-an-undirected-graph/). (Note: this is a word problem version of finding the number of connected components in an undirected graph, which is the problem the linked solution is for.)

Initalize a network count to zero. Conduct either a BFS or DFS traversal starting with an arbitrary node (i.e., town); iterate over the list of towns for simplicity. Every time the search is started with a new, previously unvisisted node, incremement the network count. When the search is exhuasted (the number of visited nodes is the same as the number of nodes), return the count.

**Big O:** O(n) time, O(n) space

### Question 7: Reverse Words

Given a string, return the string with the order of the space-separated words reversed.

**Technique:** Stack

**Approach:** For a full write-up and sample code see [ReverseWords](https://www.geeksforgeeks.org/reverse-the-sentence-using-stack/).

Initalize a temporary string, a result string, and a stack. Iterate through the input string, adding each character to the temporary string until a space is reached. Add the temporary string to the stack, then reset it to the empty string. Repeat until the input string is exhuasted, ending by pushing whatever remains in the temporary string (if not empty) to the stack. Then pop the stack, adding each word followed by a space (skipping the space when the stack is empty) to the result string. Return the result string.

**Big O:** O(n) time, O(n) space

### Question 8: Alternating Path

Given an origin and a destination in a directed graph in which edges can be blue or red, determine the length of the shortest path from the origin to the destination in which the edges traversed alternate in color. Return -1 if no such path exists.

**Technique:** Graph, BFS

**Approach:** For a full write-up and sample code see [AlternatingPath](https://www.geeksforgeeks.org/shortest-alternate-colored-path/).

Run a BFS from the origin to find the destination. Keep track of the color of the previous edge and explore only edges of the opposite color (for example, by using pairs in the queue to store both the node and the previous edge color). Also keep track of the length of the path (either by using a triple in the queue, or by using two queues and incrementing a count every time one queue is emptied, indicating we are moving a node further from the origin in the BFS).

**Big O:**

### Question 9: Merge K Sorted Arrays

Given an array of k sorted arrays, merge the k arrays into a single sorted array.

**Technique:** Min heap

**Approach:** For a full write-up and sample code see [MergeKSortedArrays](https://www.geeksforgeeks.org/merge-k-sorted-arrays-set-2-different-sized-arrays/).

Initalize a min heap. Initalize a result array. Initialize an index in each array to 0. Add the elements at those indices to the heap. While the heap is not empty, repeat the following steps:

1. Add the top element of the heap to the result.
2. Increment the index for the array the top element came from. If it is still in bounds, add that element to the heap.
3. Remove the top element from the heap.

Return the result array.

**Big O:** O(n) time, O(1) extra space, O(n) space for return value

### Question 10: Prerequisite Courses

Given a list of courses that a student needs to take to complete their major and a map of courses to their prerequisites, return a valid order for them to take their courses assuming they only take one course for their major at once.

**Technique:** Graph, topological sort (either Kahn’s or DFS implementation works)

**Approach:** For a full write-up and sample code see [PrerequisiteCourses](https://leetcode.com/problems/course-schedule/solutions/335888/c-topological-sort-with-explanation/).

**Big O:**

### Question 11: Vacation Destinations

Given an origin city, a maximum travel time k, and pairs of destinations that can be reached directly from each other with corresponding travel times in hours, return the number of destinations within k hours of the origin. Assume that having a stopover in a city adds an hour of travel time.

**Technique:** Graph, DFS

**Approach:** This problem is equivalent to count nodes within k distance of source in a weighted graph with one additional step: incrementing the total path weight by one for each node after the source. Branches can be trimmed (i.e., recursion terminated) once the total path weight exceeds k.

Perform a DFS from the origin city. Have the recursive call accept a set of destinations and a distance. Make the initial call with an empty set and a distance of zero. If the distance from the current node to a neighbor plus one (if the current node isn’t the origin) plus the distance so far is less than k, make the recursive call to that neighbor with this value as the new distance and adding the neighbor to the set. When the recursion terminates, return the set.

**Big O:** O(n) time, O(n) space
