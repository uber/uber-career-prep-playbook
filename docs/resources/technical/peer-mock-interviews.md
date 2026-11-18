# Peer Mock Interviews

Resources for fellows who run mock interviews with each other: tips for peer interviewers and the question bank, with solutions.

## Directions

- Select one of the questions **you were asked in a previous mock interview**.
- If your partner finishes early, choose another question **you were asked in a previous mock interview.**
- **Do not** use a question your partner was already asked in a previous mock interview. We have paired you to ensure you and your partner were asked at least two different questions in the first three mock interviews.

## Tips for Interviewers

1. **Ask questions you have already solved!**
2. Give your partner an example of an input and the correct solution.
3. Answer clarifying questions. If the problem doesn’t say, feel free to decide what you want and go with it!
4. Nervous or overeager interviewees tend to jump right into coding or trying to write something down. If this happens, ask your partner to talk through their ideas first.
5. If your interviewee is quiet, ask them to talk through their ideas aloud. If there’s a silence of more than a couple of minutes, get your interviewee talking again.
6. That said, give your interviewee time to think. This is one of the hardest parts of being an interviewer – there are often a lot of pauses and it can be awkward or painful. Two minutes of quiet can feel like a very long time.
7. If you’re not sure if the interviewee is stuck or just thinking and quiet, ask them to explain what they’re thinking. This will help you avoid giving premature or unnecessary hints.
8. If the interviewee is making progress, stay quiet. Sometimes it’s also hard to keep your mouth shut, and it can feel weird to sit there and observe in silence, but when the interviewee is excelling, the interviewer does very little talking!
9. Take notes! *Note things that go well and poorly so you can give feedback afterwards without interrupting the flow or atmosphere of the interview.* Also write down how long the interviewee spends on each part (developing the initial algorithm, translating it into code, testing, etc) to understand where they struggle and excel.
10. Encourage the interviewee to work through examples by hand and/or draw an illustration of the problem if they’re confused or stuck.
11. Brainstorm “little hints”, “medium hints”, and “big hints” you can give if the interviewee gets stuck. “Little hints” tend to be open-ended (i.e., “how would you do this problem if you were solving it by hand?”) while “big hints” point the partner to the correct algorithm (i.e., “what would happen if you used data structure X instead of data structure Y?) While “medium hints” unsurprisingly are somewhere in the middle (for example, they might indicate the area in which you want to make a change without giving away the specific change, such as “is there another data structure you could use instead?”).
12. If the interviewee is stuck, help them talk about their thoughts so far before giving a hint. Often talking through the problem will get an partner unstuck without any hints by acting as a “rubber duck.” Questions like “and then what?” or “what about when…?” without bringing in any new information are often sufficient to keep the ideas and words flowing.
13. If you do have to give hints, give them one at a time, in increasing order of specificity (i.e., start with a “small hint” and only work up to a “big hint” if the interviewee is still stuck and running out of time). Leave plenty of space between the hints to give the interviewee time to work with them.
14. Keep track of the time! When time is almost up, tell your partner you’re almost out of time, and ask them to wrap up their solution as best as possible, such as by explaining what they would do if they had more time. It helps you get a sense of how their thinking has progressed and creates a better experience for them.
15. **Stay in character until the interview is over! You’re the interviewer, not a peer or teacher. The best mocks are the ones that most closely replicate a true interview.**
16. **After the interview ends, break your interviewer character and switch to peer/teacher mode. Leave enough time to give face-to-face constructive feedback. Give honest feedback so your partner can avoid repeating mistakes from mock interviews in real interviews! Not pointing out mistakes is not neutral - it actually encourages interviewees to repeat those mistakes. Include feedback on both technical skills and soft skills, and be sure to also point out what the interviewee did well so they know to keep doing it.**

## Workshop 1: Hashing, Arrays, & Strings

1. [First Element Occurring K Times in an Array *(Follow-Up: Last element occurring K times in array)*](#first-element-occurring-k-times-in-an-array)
2. [Missing Elements in a Range](#missing-elements-in-a-range)
3. [Pangrams](#pangrams)
4. [Isomorphic Strings](#isomorphic-strings)

### First Element Occurring K Times in an Array

Given an array and an integer k, return the first element that occurs k times.

#### Example

Input: \[3, 4, 1, 5, 4, 2, 3, 5, 3, 4\]

Output: k=2 ⇒ 4, k=3 ⇒ 3

#### Solution

##### Brute Force

For each element in the array, iterate through the array and count the number of occurrences. If it occurs k or more times, return the element, otherwise continue to the next element.

**Complexity:**

Time: O(n^2)

Space: O(1)

##### Optimal

Keep a map of element counts. Iterate through the array, incrementing the count of each element in a map. If the count equals k, return the element.

**Complexity:**

Time: O(n)

Space: O(n)

**C++ Sample Code**

```cpp
#include <unordered_map>
#include <vector>
#include <iostream>

using namespace std;

int firstKRepeats(vector<int> &vec, int k) {
    auto counts = unordered_map<int, int>();
    for (int x: vec) {
       counts[x]++;
       if (counts[x] == k)
           return x;
    }
    // Agree on a value to return here.
    // If you stipulate the values are positive, -1 works well.
    return -1;
}
```

#### Follow-Up

What about if we wanted the last element occurring K times?

Instead of returning when we find an element that occurs k times, we can update a variable keeping track of the last time an element occurring k times was seen. Note that iterating backwards does **not** work, because an element that occurs more than k times may incorrectly be returned. Time and space complexity are the same as in the original problem.

### Missing Elements in a Range

Given an array and two integers, lo and hi, defining a range, return the values in the range missing from the array.

#### Example

Input: \[8, 12, 18, 11, 15\], lo = 7, hi = 16

Output: \[7, 9, 10, 13, 14, 16\]

#### Solution

##### Brute Force

Sort the array, then perform a binary search for the low value. Traverse from where it is (or is not found) until the high value and store the missing numbers in an array. (Equivalently, search for the high value and traverse backwards to the low value.)

**Complexity:**

Time: O(nlogn)

Space: O(logn) or O(n) extra space, depending on the sorting algorithm; most built-in sorts are quicksort, which is O(logn). Also O(k) required space for the return value, where k is the size of the range.

##### Almost Optimal

Iterate over the array, creating a set of the array elements. Iterate over the range, checking the set for the value at each iteration and adding it to an array if not present.

**Complexity:**

Time: O(n + k) or, equivalently, O(max(n, k))

Space: O(n) extra space. Also O(k) required space for the return value, where k is the size of the range.

##### Optimal

Iterate over the array, adding each element in the range to a set. Iterate over the range, checking the set for the value at each iteration and adding it to an array if not present.

**Complexity:**

Time: O(n + k) or, equivalently, O(max(n, k))

Space: O(min(n, k)) extra space. Also O(k) required space for the return value, where k is the size of the range.

**C++ Sample Code**

```cpp
#include <unordered_set>
#include <vector>
#include <iostream>

using namespace std;

vector<int> missingFromRange(vector<int> &vec, int lo, int hi) {
    auto present = unordered_set<int>();
    auto missing = vector<int>();
    for (int x: vec)
       if (x >= lo && x <= hi)
           present.insert(x);
    for (int i = lo; i <= hi; i++)
       if (present.count(i) == 0)
           missing.push_back(i);
    return missing;
}
```

### Pangrams

A pangram is a phrase or sentence containing every letter (a-z) in the English alphabet. Given a string, determine if it is a pangram.

#### Example

Input: “The quick brown fox jumps over the dog”

Output: False

Input: “The quick brown fox jumps over the lazy dog”

Output: True

#### Solution

##### Brute Force

Convert the string to lowercase. Iterate over the lowercase alphabet and search the string for the letter. If the letter is not found, return false. If the end of the alphabet is reached, return true.

**Complexity:**

Time: O(n); O(n\*m) where m is the size of the alphabet

Space: O(1)

##### Optimal

Create an alphabet array of 0s of size 26. Convert the string to lowercase. Iterate over the string. Convert the current character to an integer and shift (so a-z are 0-25). If the integer representation is 0-25, set the value at that index to 1. Iterate over the alphabet array. If a 0 is encountered, return false. If the end of the array is reached, return true. (Equivalently, a set or map can be used.)

**Complexity:**

Time: O(n); O(n+m) where m is the size of the alphabet (considering the alphabet size as a constant, the brute force and optimal are the same; if the candidate codes the brute force solution and states this encourage them to think of a solution that scales for a larger alphabet)

Space: O(n)

**C++ Sample Code**

```cpp
#include <vector>
#include <algorithm>

using namespace std;

bool is_pangram(string str) {
    lower = transform(str.begin(), str.end(), tolower);
    auto alpha = vector<bool>(26, False);
    for (char c: str) {
       int ascii_shift = c - 'a';
       if (ascii_shift >= 0 && ascii_shift < 26)
            alpha[ascii_shift] = True;
    }
    for (bool b: alpha)
       if (!b) return False
    return True;
}
```

### Isomorphic Strings

Two strings are considered isomorphic if the characters in one string can be replaced to get the characters in the other string. No two distinct characters can be replaced by the same character, but a character can be replaced with itself.

#### Example

Input: “egg”, “add”

Output: True

Input: “foo”, “bar”

Output: False

#### Solution

##### Brute Force

Return false if the strings are of unequal length. Iterate over the length of the strings. For each index, iterate backwards in each string until the same character is found or the beginning is reached. If the previous occurrence of each character is not the same, return false. If the end of the strings are reached, return true. *Note: many variations of the same solution exist.*

**Complexity:**

Time: O(n^2)

Space: O(1)

##### Optimal

Return false if the strings are of unequal length. Create two maps representing the mappings from string one to string two and vice versa. Iterate over the length of the strings. If the current characters are not in the maps keyed on the respective strings, add them with the character in the other string as the value. If one is in its map and not the other, return false. If they are both in the map, return false if they do not correspond, and continue if they do. Return true if the end of the strings are reached. *Note: many variations of the same solution exist.*

**Complexity:**

Time: O(n)

Space: O(n)

**C++ Sample Code**

```cpp
#include <string>
#include <vector>
#include <unordered_map>

using namespace std;

bool are_isomorphic(string str1, string str2) {
     if (str1.size() != str2.size()) return False;
     auto map1 = unordered_map<char, char>();
     auto map2 = unordered_map<char,char>();
     for (int i = 0; i < str1.size(); i++) {
         if ((map1.find(str1[i]) == map1.end()) != (map2.find(str2[i]) == map2.end()))
              return False
         if((map1.find(str1[i]) == map1.end()) {
              map1[str1[i]] = str2[i];
              map2[str2[i]] = str1[i];
         } else if (map1[str1[i]] != str2[i] || map2[str2[i]] != str1[i])
              return False;
     }
     return True;
}
```

## Workshop 2: Two-Pointer, Sorting, & Searching Arrays & Strings

1. [Subarrays of Size K Containing Duplicates](#subarrays-of-size-k-containing-duplicates)
2. [Max Stock Profit with Single Buy/Sell *(Follow-Up: Max stock profit with unlimited buys/sells)*](#max-stock-profit-with-single-buysell)
3. [Number of Triplets with Zero Sum *(Follow-Up: Number of triplets with given sum)*](#number-of-triplets-with-zero-sum)
4. [Max Meetings in a Room](#max-meetings-in-a-room)

### Subarrays of Size K Containing Duplicates

Given an array of integers and an integer k, return the number of unique subarrays of size k that contain duplicate elements.

#### Example

Input: \[4, 5, 3, 7, 4, 2, 3, 8, 7, 1, 5, 3\]

Output: k=4 ⇒ 0, k=5 ⇒ 2, k=6 ⇒ 5

#### Solution

##### Brute Force

Create a count. Iterate through the array. For each index, iterate through the rest of the array until a duplicate is encountered. If the indices are k or fewer apart, increment the count.

**Complexity:**

Time: O(n^2)

Space: O(1)

##### Optimal

Create a map of integers to integers. Add the first k elements to the map, incrementing their counts. Initialize a count of subarrays to zero if there are no duplicates in the first k elements and 1 otherwise. Iterate over the array until i + k is out-of-bounds. For each index i, decrement the count of the element at i in the map and increment the count of the element at i + k. Check the map for values greater than 1; if there are any, increment the count of subarrays.

**Complexity:**

Time: O(n) or O(n\*k)

Space: O(1) or O(k)

**C++ Sample Code**

```cpp
#include <unordered_map>
#include <vector>

using namespace std;

int dupKSubArrays(vector<int> &vec, int k) {
    auto window = unordered_map<int>();
    int count = 0;
    for (int i = 0; i < k; i++) {
        window[vec[i]]++;
        if (window[vec[i]] > 1)
            count = 1;
    }
    for (int i = 0; i < vec.size() - k; i++) {
        window[vec[i]]--;
        window[vec[i+k]]++;
        for (int element : window)
            if (element.second > 1) {
                count++;
                break;
           }
    }
    return count;
}
```

### Max Stock Profit with Single Buy/Sell

Given an array of integers representing the price of a stock over time, return the maximum profit that can be made on a share by buying and selling at most once.

#### Example

Input: \[50, 48, 44, 49, 31, 36, 32, 39, 51, 26, 25, 28\]

Output: 20 (buy at 31, sell at 51)

#### Solution

##### Brute Force

Keep track of the max profit (initialized to zero) in a variable. Use a nested loop to check the profit at every possible buy/sell combination and compare to the max profit so far.

**Complexity:**

Time: O(n^2)

Space: O(1)

##### Optimal

Use two variables to keep track of the max profit and the buy point (both initialized to zero). Iterate through the array. If the current value is less than the value at the buy point, update the buy point to the current index. Otherwise, compute the profit with the current index as the sell point and compare to the max profit so far.

**Complexity:**

Time: O(n)

Space: O(1)

**C++ Sample Code**

```cpp
#include <vector>

using namespace std;

int stockProfit(vector<int> &vec) {
    int profit = 0;
    int buy = 0;
    for (int i = 0; i < vec.size(); i++)
        if (vec[i] < vec[buy])
             buy = i;
        else if (vec[i] - vec[buy] > profit) {
             profit = vec[i] - vec[buy];
    return profit;
}
```

#### Follow-Up

What if we were allowed unlimited buys and sells?

Iterate over the array. If the next element is greater than the current element, add the difference to the profit.

### Number of Triplets with Zero Sum

Given an array of integers, return the number of unique triplets that sum to zero.

#### Example

Input: \[8, 2, 3, 5, -2, 1, -1, 3\]

Output: 2 (Triplets are (-2, -1, 3), (-2, -1, 3))

Input: \[5, 0, -5, -2, 4, 1, -3, 6\]

Output: 3 (Triplets are (5, 0, -5), (5, -2, -3), (-5, 4, 1))

#### Solution

##### Brute Force

Keep a count of triplets. Use a triple nested loop to iterate through every possible triplet of indices and check whether the sum of the elements equals zero and if so, increment the count.

**Complexity:**

Time: O(n^3)

Space: O(1)

##### Optimal

Create a map of integers to integers. Iterate through the array and increment the count of each element. Use a nested loop to iterate through every possible pair of indices. Calculate the target value by negating the sum of the two elements. If the target is in the map and the count of the target is greater than or equal to the occurrences of the target in the triplet, increment the count.

**Complexity:**

Time: O(n^2)

Space: O(n)

**C++ Sample Code**

```cpp
#include <unordered_map>
#include <vector>

using namespace std;

int tripletsZeroSum(vector<int> &vec) {
    auto counts = unordered_map<int>();
    int count = 0;
    for (int element : vec)
        counts[element]++;
    for (int i = 0; i < vec.size(); i++)
        for (int j = i+1; j < vec.size(); j++) {
            int target = -1 * (vec[i] + vec[j]);
           if (counts.find(target) == counts.end())
               continue;
           if (vec[i] == target && vec[j] == target && counts[target] < 3)
               continue;
           if (vec[i] == target || vec[j] == target && counts[target] < 2)
               Continue;
           count++;
        }
    return count;
}
```

#### Follow-Up

What about if we wanted the number of triplets summing to any given target?

Pass the target sum to the function and calculate the value to lookup in the map by subtracting the sum of the pair from that value.

### Max Meetings in a Room

Given an array of numeric pairs representing the start and end times of scheduled meetings, find the maximum number of meetings that can be held in a room if only one meeting can occur in the room at once.

#### Example

Input: \[(8.5, 9.5), (11, 11.25), (9, 11), (11.5, 13), (10, 10.75), (8, 9)\]

Output: 4 (The following meetings can occur in the given order: (8, 9), (10, 10.75), (11, 11.25), 11.5, 13))

#### Solution

##### Brute Force

Check if any of the meetings overlap. If not, return the number of meetings. Otherwise, try removing each of the overlapping meetings and repeat.

**Complexity:**

Time: O(n!) (Do not even let the candidate code this solution.)

Space: O(1)

##### Optimal

Sort the meetings by end time. Initialize a count to one and index (to track the last selected meeting) to 0. Iterate through the meetings starting at index 1. If the last selected meeting’s end time is less than or equal to the current meeting’s start time, the meeting can be held in the same room; increment the count and update the index to the current index.

**Complexity:**

Time: O(nlogn)

Space: O(1)

**C++ Sample Code**

```cpp
#include <vector>
#include <algorithm>

using namespace std;

int maxMeetingsRoom(vector<pair<float, float>> &vec) {
    if (!vec.size())
       return 0;
    sort(vec.begin(), vec.end(), [](const pair<int, int> &left, const pair<int, int> &right) {
        if (left.second != right.second)
            return left.second < right.second;
        else
            return left.first < right.first;
    });
    int count = 1;
    int ind = 0;
    for (int i = 1; i < vec.size(); i++)
        if (vec[i].first >= vec[ind].second) {
            count++;
            ind = i;
        }
    return count;
}
```

## Workshop 3: Linked Lists & Trees

1. [Reverse Linked List in Groups of k](#reverse-linked-list-in-groups-of-k)
2. [Max Height of Binary Tree](#max-height-of-a-binary-tree)
3. [Number of Nodes within k Distance of Root](#number-of-nodes-within-k-distance-of-root)
4. [Median of a Sorted Linked List](#median-of-a-sorted-linked-list)

### Reverse Linked List in Groups of k

Given the head node of a linked list, reverse the linked list in groups of k.

#### Example

Input: 4 ⇒ 8 ⇒ 5 ⇒ 3 ⇒ 6 ⇒ 6 ⇒ 9 ⇒ 1

k=2:

Output: 8 ⇒ 4 ⇒ 3 ⇒ 5 ⇒ 6 ⇒ 6 ⇒ 1 ⇒ 9

k =3:

Output: 5 ⇒ 8 ⇒ 4 ⇒ 6 ⇒ 6 ⇒ 3 ⇒ 1 ⇒ 9

#### Solution

##### Brute Force

Iterate over the linked list and copy it to a temporary array. Iterate over the array using the indices to reverse the elements in groups of k. (One optimal variation of this is to use nested loops with an outer loop that increments i by k, rather than the typical 1, and an inner loop that iterates only over i to i +k, reversing the elements.) Iterate over the linked list again, overwriting the data with the corresponding element in the array.

**Complexity:**

Time: O(n)

Space: O(n)

##### Good

Reverse the first k elements recursively using a counter for k. Recurse on the remainder of the list, setting element k’s next to the result.

**Complexity:**

Time: O(n)

Space: O(n/k) (O(1) explicit, O(n/k) implicit recursive stack space)

##### Optimal

Reverse the first k elements iteratively using a counter for k. Recurse on the remainder of the list, setting element k’s next to the result.

**Complexity:**

Time: O(n)

Space: O(1)

**C++ Sample Code**

```cpp
using namespace std;

Node *kReverse(Node *head, int k) {
    int count = 0;
    Node *curr = head;
    Node *next = nullptr;
    Node *prev = nullptr;
    Node *newHead = nullptr;
    Node *newTail = nullptr;
    Node *tail = nullptr;
    while (curr) {
        count = k;
        join = curr;
        prev = nullptr;
        while (curr && count--) {
            next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        if (!newHead)
             newHead = prev;
        if (tail)
             tail->next = prev;
        tail = newTail;
    }
    return newHead;
}
```

### Max Height of a Binary Tree

Given a binary tree, find the longest path from the root to a leaf (node with no children).

#### Example

Input:

1

/ \\

2 3

/ \\

4 5

/

6

Output: 4

Input:

1

/ \\

2 3

/ \\ /

4 5 6

Output: 3

#### Solution

##### Brute Force

Use any traversal to find every leaf node. Then use any traversal to find the distance to each leaf node. Return the maximum.

**Complexity**

Time: O(n^2)

Space: O(n)

*Note: do not let the candidate code this solution!*

##### Good

Use a post-order traversal to calculate the heights of the left and right subtrees and return the max plus one.

**Complexity:**

Time: O(n)

Space: O(n) (O(1) explicit, O(n) implicit stack space)

##### Good

Use a level-order traversal using either two queues for current and previous level or pushing null values (if permitted in the language of choice) to mark the end of levels. If the former, keep a level count that is incremented every time the current level is reset; if the latter, keep a level count that is incremented whenever a null value is popped.

**Complexity:**

Time: O(n)

Space: O(n)

##### Optimal

The Morris traversal algorithm makes this possible in O(1) space. **It is not expected that candidates will find this solution; therefore the sample solution below is a “good” solution.**

**C++ Sample Code**

```cpp
#include <algorithm>
using namespace std;

int maxDepth(Node *root) {
    if (!root)
        return 0;
    return 1 + max(maxDepth(root->left), maxDepth(root->right));
}
```

### Number of Nodes within K Distance of Root

Given a binary tree, count the number of nodes within k distance of the root.

#### Example

Input:

1

/ \\

2 3

/ \\

4 5

/

6

k = 3

Output: 5

Input:

1

/ \\

2 3

/ \\ /

4 5 6

k = 3

Output: 6

#### Solution

##### Brute Force

Use any traversal to find every node. Then use any traversal to find the depth of each node. Count the number of values less than or equal to k.

**Complexity**

Time: O(n^2)

Space: O(n)

*Note: do not let the candidate code this solution!*

##### Better

Use a level-order or pre-order traversal to find the depth of each node. Count the number of values less than or equal to k.

**Complexity**

Time: O(n)

Space: O(n)

*Note: do not let the candidate code this solution!*

##### Good

Use a level-order traversal using either two queues for current and previous level. Keep two counts: a level count that is incremented every time the current level is reset; and a node count that is incremented every time a node is popped. When the level count exceeds k, return the node count.

**Complexity:**

Time: O(n)

Space: O(n)

*Note that while Big O space and time are the same as the “Better” solution, because this solution terminates early, in practice it is much better.*

##### Optimal

Use a pre-order traversal that accepts the distance from the root and k. Increment the distance; if it is greater than k, return 0; otherwise return one plus the counts from the left and right subtrees.

**Complexity:**

Time: O(n)

Space: O(k) (O(1) explicit, O(k) implicit stack space)

*Note: in the worst case (k=n), the max space for the “Good” solution is n/2 and the max space for the “Optimal” solution is n, since we typically consider k \<\< n, the solutions are labelled this way. However, both are acceptable. If the candidate considers and weighs this, that is the ideal, although not expected.*

**C++ Sample Code**

```cpp
#include <algorithm>
using namespace std;

int countWithinK(Node *root, int k, int depth) {
    if (!root || depth+1 > k)
        return 0;
    return 1 + countWithinK(root->left, k, depth+1), countWithinK(root->right, k, depth+1));
}

int countWithinK(Node *root, int k) {
    return countWithinK(root, k, 0);
}
```

### Median of a Sorted Linked List

Given a sorted singly list of integers, return the median value.

#### Example

Input: 1 ⇒ 3 ⇒ 4 ⇒ 5 ⇒ 6 ⇒ 6 ⇒ 9

Output: 5

Input: 1 ⇒ 3 ⇒ 4 ⇒ 5 ⇒ 6 ⇒ 6 ⇒ 8 ⇒ 9

Output: 5.5

#### Solution

##### Brute Force

Copy the linked list into an array and use the indices to find the median.

**Complexity:**

Time: O(n)

Space: O(n)

*Note: do not let the candidate code this solution!*

##### Good

Iterate over the list to find its length. Then iterate again to find the middle(s).

**Complexity:**

Time: O(n)

Space: O(1)

##### Optimal

Use fast-slow pointers to find the middle(s) at the same time as the length.

**Complexity:**

Time: O(n)

Space: O(1)

*Note: the Big O is the same as the “Good” solution but a traversal is eliminated, making this the better solution.*

**C++ Sample Code**

```cpp
using namespace std;

Node *median(Node *head) {
    Node *slow = head;
    Node *fast = head;
    int count = 0;
    while (fast) {
        count++;
        fast = fast->next;
        if (fast) {
            count++;
            fast = fast->next;
            if (fast->next)
                slow = slow->next;
        }
    }
    if (count % 2)
        return slow->next->value;
    return (slow->value + slow->next->value) / 2;
}
```
