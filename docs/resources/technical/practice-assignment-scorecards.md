# Practice Assignment Scorecards

Each practice assignment is reviewed by a volunteer using a scorecard. There is one scorecard per assignment (0–4). They share the same layout: a short header, one section per problem, and a general feedback section at the end. This page contains everything you need to recreate them as Google Forms.

## Set up

Create **five** Google Forms, one per assignment, and give each one:

- **Title:** `UCP Open Source | Practice Assignment N Feedback Form` (N = 0–4)
- **Settings → Responses → Collect email addresses:** **Verified**, so that every scorecard is tied to its reviewer

Build each form with these parts, in order:

1. The [header questions](#header-questions) (first section)
2. One new **section** for each problem, titled `Question N: <problem name>`, using the [implementation](#implementation-problem-section) or [problem-solving](#problem-solving-section) layout. The [problem lists](#problem-lists) below say which to use.
3. A final section titled `General Feedback`, with the [general feedback questions](#general-feedback-questions)

!!! tip
    Build the first problem section, then use the section's **⋮ → Duplicate section** menu to copy it for each remaining problem, and just change the title.

## Header questions

| # | Question | Type | Required |
|---|----------|------|----------|
| 1 | Student's name (first & last) | Short answer | Yes |
| 2 | Link to student's assignment | Short answer | Yes |

## Implementation problem section

Use for problems where the student builds a data structure (for example, “Build a Stack”). Each section has two items.

### Item 1: Rating grid

| Setting | Value |
|---------|-------|
| Question title | Rate the solution from 0-3 on the following competencies. |
| Type | Multiple-choice grid |
| Required | No |
| Rows | Code Style<br>Testing<br>Correctness<br>Problem-Solving & Optimality<br>Speed (based on self-reported time) |
| Columns | `0`<br>`1`<br>`2`<br>`3` |

### Item 2: Interview rating

| Setting | Value |
|---------|-------|
| Question title | If this question were an internship interview, how would you evaluate it? |
| Type | Dropdown |
| Required | No |
| Options | `Double Thumbs Up`<br>`Thumbs Up`<br>`Thumbs Down`<br>`Double Thumbs Down` |

## Problem-solving section

Use for problems where the student solves an algorithm problem. Each section has three items.

### Item 1: Rating grid

Exactly the same as Item 1 in the implementation section.

### Item 2: Identification grid

| Setting | Value |
|---------|-------|
| Question title | Did the student correctly identify the following aspects of the solution? (Select "No" if not provided.) |
| Type | Multiple-choice grid |
| Required | No |
| Rows | Problem Type<br>Time Complexity<br>Space Complexity |
| Columns | `No`<br>`Yes` |

### Item 3: Interview rating

Exactly the same as Item 2 in the implementation section.

## General feedback questions

Add these to the final `General Feedback` section. Give the section the description *Please evaluate the student overall, considering the solutions to all the questions.*

| # | Question | Type | Required | Options |
|---|----------|------|----------|---------|
| 1 | If the whole assignment were an internship interview, how would you evaluate it? | Multiple choice | Yes | `Double Thumbs Up`<br>`Thumbs Up`<br>`Thumbs Down`<br>`Double Thumbs Down` |
| 2 | Pros / Areas of Strength | Paragraph | Yes | – |
| 3 | Cons / Areas of Improvement | Paragraph | Yes | – |
| 4 | Conclusion | Paragraph | Yes | – |

## Problem lists

Create one section per row, in this order.

### Practice Assignment 0: Arrays, Strings, & Hashing

| Section title | Layout |
|---------------|--------|
| Question 1: ZeroSum | Problem-solving |
| Question 2: UniqueSum | Problem-solving |
| Question 3: First Occurrence | Problem-solving |

*Add this description to the “ZeroSum” section:* Please evaluate both the original question and the follow-up together.

### Practice Assignment 1: Arrays & Strings

| Section title | Layout |
|---------------|--------|
| Question 1: Max Mean Sub Array | Problem-solving |
| Question 2: Reverse Vowels | Problem-solving |
| Question 3: Zero Sum Sub Array | Problem-solving |
| Question 4: Backspace String Compare | Problem-solving |
| Question 5: Shortest Substring | Problem-solving |
| Question 6: Missing Integer | Problem-solving |
| Question 7: K Anagrams | Problem-solving |
| Question 8: Merge Intervals | Problem-solving |
| Question 9: Dedup Array | Problem-solving |

### Practice Assignment 2: Linked Lists & Trees

| Section title | Layout |
|---------------|--------|
| Question 1: Build a Singly Linked List | Implementation |
| Question 2: Build a Doubly Linked List | Implementation |
| Question 3: Build a Binary Search Tree | Implementation |
| Question 4: Build a Queue | Implementation |
| Question 5: Build a Stack | Implementation |
| Question 6: Build a Deque | Implementation |
| Question 7: Copy Tree | Problem-solving |
| Question 8: Is BST | Problem-solving |
| Question 9: Dedup Sorted List | Problem-solving |
| Question 10: Move Nth Last to Front | Problem-solving |
| Question 11: Is Palindrome | Problem-solving |
| Question 12: Disconnect Cycle | Problem-solving |
| Question 13: Left View | Problem-solving |
| Question 14: Floor in BST | Problem-solving |

### Practice Assignment 3: Graphs & Data Structure Selection

| Section title | Layout |
|---------------|--------|
| Question 1: Graph Algorithms Using Adjacency List/Set Representation  | Implementation |
| Question 2: Build a Heap | Implementation |
| Question 3: Build a Priority Queue | Implementation |
| Question 4: Number of Islands | Problem-solving |
| Question 5: First K Binary Numbers | Problem-solving |
| Question 6: Road Networks | Problem-solving |
| Question 7: Reverse Words | Problem-solving |
| Question 8: Alternating Path | Problem-solving |
| Question 9: Merge K Sorted Arrays | Problem-solving |
| Question 10: Prerequisite Courses | Problem-solving |
| Question 11: Vacation Destinations | Problem-solving |

### Practice Assignment 4: Tries & Repeated Computation

| Section title | Layout |
|---------------|--------|
| Question 1: Build a Trie | Implementation |
| Question 2: Boggle | Problem-solving |
| Question 3: Running Median | Problem-solving |
| Question 4: Catalan Numbers | Problem-solving |
| Question 5: Min Cost Stair Climbing | Problem-solving |
| Question 6: Word Break | Problem-solving |
| Question 7: Largest Square of 1s | Problem-solving |
| Question 8: Coin Change | Problem-solving |
| Question 9: Adopt a Pet | Problem-solving |

