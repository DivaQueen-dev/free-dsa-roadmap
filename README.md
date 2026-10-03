# Free DSA Roadmap

### Learn data structures and algorithms by pattern. Free resources only.

[![Discord](https://img.shields.io/badge/Join%20Community-Discord-7289da?style=for-the-badge&logo=discord)](https://discord.gg/ETCSm74A59)
[![Stars](https://img.shields.io/github/stars/DivaQueen-dev/free-dsa-roadmap?style=for-the-badge)](https://github.com/DivaQueen-dev/free-dsa-roadmap)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-orange?style=for-the-badge)](CONTRIBUTING.md)

Part of the [Free Tech Roadmap](https://github.com/DivaQueen-dev/free-cs-roadmap) series.

---

> Most people grind hundreds of random problems and wonder why they aren't improving. They are solving problems instead of learning patterns. One pattern unlocks 20 to 30 problems at once. This guide is built around that idea.

No paid courses. No affiliate links. No LeetCode Premium required.

---

## What's in this repo

| File | What it has |
| ---- | ----------- |
| **README.md** (you are here) | The roadmap, resources, problem lists, study plans, progress tracker |
| **[NOTES.md](NOTES.md)** | Topic-wise notes, pattern recognition cues, copy-ready Python templates, a Python interview cheat sheet, and an edge-case checklist |

---

## Table of Contents

1. [How to use this roadmap](#how-to-use-this-roadmap)
2. [Step 1: Pick one language](#step-1-pick-one-language)
3. [Step 2: Learn the fundamentals](#step-2-learn-the-fundamentals)
4. [Step 3: Learn the patterns](#step-3-learn-the-patterns)
5. [Starter problems for each pattern](#starter-problems-for-each-pattern)
6. [Step 4: Practice with a problem list](#step-4-practice-with-a-problem-list)
7. [Study plans](#study-plans)
8. [How to practice properly](#how-to-practice-properly)
9. [Mock interviews and communication](#mock-interviews-and-communication)
10. [Practice platforms](#practice-platforms)
11. [Competitive programming path](#competitive-programming-path)
12. [Reference and cheat sheets](#reference-and-cheat-sheets)
13. [Visualize and drill](#visualize-and-drill)
14. [YouTube channels](#youtube-channels)
15. [Big-O cheat sheet](#big-o-cheat-sheet)
16. [Progress tracker](#progress-tracker)
17. [Common mistakes](#common-mistakes)
18. [FAQ](#faq)
19. [Contributing](#contributing)

---

## How to use this roadmap

Follow the steps in order:

1. Pick one language and stay with it.
2. Learn the basic data structures and Big-O.
3. Learn patterns topic by topic, using the [notes](NOTES.md) for templates.
4. Solve a curated problem list, not random problems.
5. Do timed practice and mock interviews.

If you are short on time, jump to the [study plans](#study-plans). If you are completely new to programming, start with [CS50](https://cs50.harvard.edu) or [CS50P](https://cs50.harvard.edu/python/) before this repo.

Once you are comfortable with DSA, continue with the [System Design roadmap](https://github.com/DivaQueen-dev/free-system-design-roadmap).

---

## Step 1: Pick one language

Stick to one. Do not switch halfway through.

| Language | Why choose it | Docs for built-in structures |
| -------- | ------------- | ---------------------------- |
| Python | Most recommended. Clean syntax and fast to write in interviews. | [collections](https://docs.python.org/3/library/collections.html), [heapq](https://docs.python.org/3/library/heapq.html), [bisect](https://docs.python.org/3/library/bisect.html) |
| Java | Good if your college taught it well. Common in Indian placements. | [Collections Framework tutorial](https://docs.oracle.com/javase/tutorial/collections/) |
| C++ | Best with a competitive programming background. STL is very fast to use. | [cppreference containers](https://en.cppreference.com/w/cpp/container) |

Know your language's built-in structures well: arrays/lists, hash maps, sets, stacks, queues, heaps, and sorting with custom comparators. The [Python cheat sheet in NOTES.md](NOTES.md#python-interview-cheat-sheet) covers the essentials.

---

## Step 2: Learn the fundamentals

Before patterns, you need the building blocks. Cover these in roughly this order:

1. Time and space complexity (Big-O)
2. Arrays and strings
3. Hashing (hash maps and sets)
4. Linked lists
5. Stacks and queues
6. Recursion
7. Sorting and searching
8. Trees and binary search trees
9. Heaps and priority queues
10. Graphs
11. Tries
12. Dynamic programming
13. Greedy algorithms
14. Bit manipulation (basic)

### Free courses

| Resource | What it is | Best for |
| -------- | ---------- | -------- |
| [CS50x](https://cs50.harvard.edu/x/) | Harvard's intro to CS, including basic data structures and algorithms. | Complete beginners |
| [MIT 6.006: Introduction to Algorithms](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/) | Full university course with lectures, notes, and problem sets. | Strong theory foundation |
| [MIT 6.046: Design and Analysis of Algorithms](https://ocw.mit.edu/courses/6-046j-design-and-analysis-of-algorithms-spring-2015/) | The follow-up course: DP, greedy, graph algorithms in depth. | Going deeper after 6.006 |
| [NPTEL](https://nptel.ac.in) | Search for "Data Structures and Algorithms" for IIT courses. Recognised in Indian placements. | Indian students wanting certificates |
| [Programiz DSA](https://www.programiz.com/dsa) | Short, illustrated tutorials on each data structure and algorithm. | Quick first pass |
| [W3Schools DSA](https://www.w3schools.com/dsa/) | Beginner-friendly explanations with animations. | Absolute beginners |

### Free books

| Book | What it is |
| ---- | ---------- |
| [Algorithms, 4th Edition (booksite)](https://algs4.cs.princeton.edu/home/) | Princeton's companion site to the Sedgewick and Wayne book: code, lectures, exercises (Java). |
| [Algorithms by Jeff Erickson](https://jeffe.cs.illinois.edu/teaching/algorithms/) | A full free textbook with strong coverage of recursion, DP, and graphs. |
| [Open Data Structures](https://opendatastructures.org) | Free textbook on how data structures are actually implemented. |
| [Competitive Programmer's Handbook](https://cses.fi/book/book.pdf) | Free PDF by Antti Laaksonen. Concise and practical. |

---

## Step 3: Learn the patterns

This is the most important step. For each pattern: learn the idea, study the template in [NOTES.md](NOTES.md), then solve 4 to 6 problems that use it.

| Pattern | When to use it | Free resource |
| ------- | -------------- | ------------- |
| All patterns, by type | Overview of every pattern | [Sean Prashad LeetCode Patterns](https://seanprashad.com/leetcode-patterns/) |
| Roadmap by topic | Ordered path through topics | [NeetCode Roadmap](https://neetcode.io/roadmap) |
| Two Pointers | Sorted arrays, pairs, palindromes | [Two Pointers study guide](https://leetcode.com/discuss/study-guide/1688903/) |
| Sliding Window | Subarrays or substrings with a condition | [Sliding Window cheatsheet](https://leetcode.com/problems/frequency-of-the-most-frequent-element/solutions/1175088/) |
| Binary Search | Sorted data, or searching on an answer range | [Binary Search template](https://leetcode.com/discuss/study-guide/786126/) |
| Dynamic Programming | Overlapping subproblems, optimal choices | [DP patterns](https://leetcode.com/discuss/general-discussion/458695/), [more DP](https://leetcode.com/discuss/study-guide/1437879/), [AtCoder Educational DP Contest](https://atcoder.jp/contests/dp) |
| Backtracking | Generate all combinations, permutations, subsets | [Backtracking pattern](https://medium.com/leetcode-patterns/leetcode-pattern-3-backtracking-5d9e5a03dc26), [template](https://gist.github.com/RuolinZheng08/cdd880ee748e27ed28e0be3916f56fa6) |
| Trees and traversals | Hierarchical data, DFS/BFS on trees | [Tree traversals guide](https://leetcode.com/discuss/study-guide/937307/) |
| Graphs | Connectivity, shortest paths, dependencies | [Graph patterns for beginners](https://leetcode.com/discuss/study-guide/655708/), [CP-Algorithms graphs](https://cp-algorithms.com) |
| Substring problems | Windows over strings | [Substring template](https://leetcode.com/problems/minimum-window-substring/solutions/26808/) |
| BFS and DFS | Traversal, shortest path in unweighted graphs | [Part 1](https://medium.com/leetcode-patterns/leetcode-pattern-1-bfs-dfs-25-of-the-problems-part-1-519450a84353), [Part 2](https://medium.com/leetcode-patterns/leetcode-pattern-2-dfs-bfs-25-of-the-problems-part-2-a5b269597f52) |
| Bit manipulation | Parity, masks, XOR tricks | [Bit Twiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html) |

### Other patterns worth knowing

Templates for all of these are in [NOTES.md](NOTES.md):

- Fast and slow pointers (cycle detection in linked lists)
- Monotonic stack (next greater element, histograms)
- Heap and top-K elements
- Merge intervals
- Union-Find (disjoint set)
- Topological sort
- Prefix sums
- Greedy
- Trie

---

## Starter problems for each pattern

Solve these in order within each pattern. Numbers refer to LeetCode problem IDs. Difficulty: E = easy, M = medium, H = hard.

| Pattern | Problems |
| ------- | -------- |
| Arrays and hashing | 217 Contains Duplicate (E), 1 Two Sum (E), 49 Group Anagrams (M), 347 Top K Frequent Elements (M), 238 Product of Array Except Self (M), 128 Longest Consecutive Sequence (M) |
| Two pointers | 125 Valid Palindrome (E), 167 Two Sum II (M), 15 3Sum (M), 11 Container With Most Water (M), 42 Trapping Rain Water (H) |
| Sliding window | 121 Best Time to Buy and Sell Stock (E), 3 Longest Substring Without Repeating Characters (M), 567 Permutation in String (M), 76 Minimum Window Substring (H), 239 Sliding Window Maximum (H) |
| Prefix sums | 560 Subarray Sum Equals K (M), 53 Maximum Subarray (M), 152 Maximum Product Subarray (M) |
| Stack | 20 Valid Parentheses (E), 155 Min Stack (M), 150 Evaluate Reverse Polish Notation (M), 22 Generate Parentheses (M), 739 Daily Temperatures (M), 853 Car Fleet (M), 84 Largest Rectangle in Histogram (H) |
| Binary search | 704 Binary Search (E), 875 Koko Eating Bananas (M), 153 Find Minimum in Rotated Sorted Array (M), 33 Search in Rotated Sorted Array (M), 4 Median of Two Sorted Arrays (H) |
| Linked list | 206 Reverse Linked List (E), 141 Linked List Cycle (E), 21 Merge Two Sorted Lists (E), 143 Reorder List (M), 19 Remove Nth Node From End (M), 2 Add Two Numbers (M), 287 Find the Duplicate Number (M), 146 LRU Cache (M), 23 Merge k Sorted Lists (H) |
| Trees | 226 Invert Binary Tree (E), 104 Maximum Depth of Binary Tree (E), 102 Binary Tree Level Order Traversal (M), 98 Validate Binary Search Tree (M), 230 Kth Smallest Element in a BST (M), 235 Lowest Common Ancestor of a BST (M), 105 Construct Binary Tree from Preorder and Inorder (M), 124 Binary Tree Maximum Path Sum (H), 297 Serialize and Deserialize Binary Tree (H) |
| Heap | 215 Kth Largest Element in an Array (M), 621 Task Scheduler (M), 295 Find Median from Data Stream (H) |
| Backtracking | 78 Subsets (M), 46 Permutations (M), 39 Combination Sum (M), 51 N-Queens (H) |
| Tries | 208 Implement Trie (M) |
| Graphs | 200 Number of Islands (M), 133 Clone Graph (M), 994 Rotting Oranges (M), 417 Pacific Atlantic Water Flow (M), 207 Course Schedule (M), 547 Number of Provinces (M), 684 Redundant Connection (M), 721 Accounts Merge (M), 127 Word Ladder (H) |
| Shortest paths and MST | 743 Network Delay Time (M), 787 Cheapest Flights Within K Stops (M), 1584 Min Cost to Connect All Points (M) |
| 1D dynamic programming | 70 Climbing Stairs (E), 198 House Robber (M), 5 Longest Palindromic Substring (M), 647 Palindromic Substrings (M), 91 Decode Ways (M), 322 Coin Change (M), 139 Word Break (M), 300 Longest Increasing Subsequence (M), 416 Partition Equal Subset Sum (M) |
| 2D dynamic programming | 62 Unique Paths (M), 1143 Longest Common Subsequence (M), 72 Edit Distance (M) |
| Greedy | 55 Jump Game (M), 134 Gas Station (M), 56 Merge Intervals (M), 57 Insert Interval (M) |
| Bit manipulation | 136 Single Number (E), 191 Number of 1 Bits (E), 338 Counting Bits (E) |

---

## Step 4: Practice with a problem list

Pick one list and finish it. Do not keep switching lists.

| List | Description | Problems |
| ---- | ----------- | -------- |
| [NeetCode 150](https://neetcode.io/practice) | Hand-picked problems covering every pattern. The best curated list for most people. | 150 |
| [Blind 75 / Grind 75](https://www.techinterviewhandbook.org/grind75/) | The classic essential list. Grind 75 lets you set your available time and builds a schedule. | 75 |
| [LeetCode Top Interview 150](https://leetcode.com/studyplan/top-interview-150/) | The official LeetCode study plan. | 150 |
| [Striver's A2Z Sheet](https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2/) | Basics to advanced, with video explanations. Best for thorough prep from scratch. | 456 |
| [Striver's SDE Sheet](https://takeuforward.org/interviews/strivers-sde-sheet-top-coding-interview-problems/) | Focused list for software interviews. | 191 |
| [HackerRank Interview Preparation Kit](https://www.hackerrank.com/interview/preparation-kits) | Topic-wise problems with tests, free. Good for building basics. | Varies |
| [InterviewBit](https://www.interviewbit.com/courses/programming/) | Structured topic-wise practice. | Varies |
| [Leetracer](https://leetracer.com/screener) | Filter questions by company, free. | Varies |

### Which list should I choose?

- Short on time (about 1 month): Blind 75 or Grind 75.
- Standard prep (about 3 months): NeetCode 150.
- Starting from zero or want full coverage: Striver's A2Z, then NeetCode 150 for revision.
- Targeting specific companies: use Leetracer after you finish a core list.

---

## Study plans

### 1 month: crunch mode

```
Week 1:  Arrays, strings, two pointers, sliding window (20 problems)
Week 2:  Trees, linked lists, stacks and queues (20 problems)
Week 3:  Binary search, graphs, DP basics (20 problems)
Week 4:  Mock interviews, behavioral prep, resume polish
Target:  Complete Blind 75
```

### 3 months: solid prep

```
Month 1: Fundamentals and all patterns, 100 problems from NeetCode 150
Month 2: 50 more problems, core CS subjects, system design basics
Month 3: Mock interviews, behavioral prep, resume, start applying
Target:  Complete NeetCode 150
```

### 6 months: thorough prep

```
Month 1-2: Language mastery, fundamentals, 50 problems
Month 3-4: All patterns, 200 problems
Month 5:   System design, behavioral prep, core CS subjects
Month 6:   Daily mock interviews, apply weekly
Target:    300+ problems, 10+ mock interviews
```

### A sample week (3-month plan)

| Day | Focus |
| --- | ----- |
| Mon | Learn one new pattern (video plus notes), solve 2 easy problems |
| Tue | Solve 2 medium problems on the same pattern |
| Wed | Learn the next pattern, solve 2 easy problems |
| Thu | Solve 2 medium problems on that pattern |
| Fri | Revise: re-solve 2 problems from earlier weeks without help |
| Sat | One timed mock: 2 problems in 60 minutes |
| Sun | Rest, or light reading of notes |

Adjust to your own schedule. Consistency matters more than the exact plan: 1 to 2 focused hours every day beats a 10-hour weekend binge.

---

## How to practice properly

### The loop for every problem

1. **Read and restate** the problem in your own words. Check constraints and edge cases.
2. **Think for 15 to 20 minutes** before looking at any hint. Write down a brute-force approach first.
3. **Optimize.** Ask which pattern fits and what the time complexity is.
4. **Code it** without autocomplete help, as you would in an interview.
5. **Test** with small cases and edge cases (empty input, single element, duplicates).
6. **If stuck, look at a hint, not the full solution.** Then close it and write the solution yourself.
7. **Log it.** Write down the pattern, the key insight, and what tripped you up.

### Spaced revision

Re-solve problems you struggled with after 3 days, 1 week, and 1 month. A simple spreadsheet with columns for problem, pattern, difficulty, date solved, and revision dates is enough.

### Time yourself

Typical interview targets: easy in 10 to 15 minutes, medium in 20 to 30, hard in 35 to 45. Start timing once you are about a third of the way through your list.

### Talk out loud

In real interviews you explain your thinking. Practice doing it while you solve, to a friend, a rubber duck, or a recording.

---

## Mock interviews and communication

Technical ability gets you shortlisted. Clear communication gets you the offer. In every interview, follow this sequence:

1. **Clarify.** Ask about input size, duplicates, negative numbers, empty input, and expected output format.
2. **Examples.** Walk through one or two small examples, including an edge case.
3. **Brute force.** State the simple solution and its complexity, even if you won't code it.
4. **Optimize.** Explain what is wasteful and which pattern or data structure fixes it.
5. **Code.** Write clean code, and narrate as you go.
6. **Test.** Trace through your example by hand, then try an edge case.
7. **Analyze.** State time and space complexity.

### Where to get mocks for free

- Pair up with a study partner in our [Discord](https://discord.gg/ETCSm74A59) and take turns interviewing each other.
- Use the question banks in [Tech Interview Handbook](https://www.techinterviewhandbook.org) and timed lists like [Grind 75](https://www.techinterviewhandbook.org/grind75/).
- Record yourself solving a problem aloud and watch it back.
- Ask a senior or alumnus to run one mock before your placement season.

For behavioral rounds, see the [Behavioral section](https://github.com/DivaQueen-dev/free-cs-roadmap#-behavioral-interviews) of the main roadmap.

---

## Practice platforms

| Platform | Best for |
| -------- | -------- |
| [LeetCode](https://leetcode.com) | Interview-style problems. The free tier is enough. |
| [NeetCode](https://neetcode.io) | Curated lists with free video solutions. |
| [GeeksforGeeks Practice](https://practice.geeksforgeeks.org) | Topic-wise problems, common in Indian placements. |
| [HackerRank](https://www.hackerrank.com) | Used by many companies for online assessments, so worth getting used to. |
| [CodeChef](https://www.codechef.com) | Contests, popular in India. Good for building speed. |
| [Codeforces](https://codeforces.com) | Competitive programming contests and a huge problem archive. |
| [AtCoder](https://atcoder.jp) | High-quality contests with clean problem statements. |
| [Codewars](https://www.codewars.com) | Small, gamified challenges for language fluency. |
| [Exercism](https://exercism.org) | Language practice with mentor feedback. |

---

## Competitive programming path

Competitive programming is optional for jobs but builds strong problem-solving speed. A simple progression:

1. Learn the basics from the [Competitive Programmer's Handbook](https://cses.fi/book/book.pdf).
2. Work through the [CSES Problem Set](https://cses.fi/problemset/) in order. It is a well-structured set covering sorting, DP, graphs, trees, and more.
3. Study techniques on [CP-Algorithms](https://cp-algorithms.com), the standard reference for algorithms and proofs.
4. Follow the [USACO Guide](https://usaco.guide) for a structured path from beginner to advanced.
5. Take the [Codeforces EDU courses](https://codeforces.com/edu/courses) for guided lessons with practice.
6. Enter regular contests on Codeforces, CodeChef, or AtCoder and upsolve problems you couldn't finish.

If placements are close, prioritise LeetCode-style practice and do contests on the side.

---

## Reference and cheat sheets

| Resource | What it is |
| -------- | ---------- |
| [NOTES.md](NOTES.md) | Notes and Python templates for every pattern in this repo |
| [Big-O Cheat Sheet](https://www.bigocheatsheet.com) | Complexities of common structures and sorting algorithms |
| [Tech Interview Handbook: algorithm cheatsheet](https://www.techinterviewhandbook.org/algorithms/study-cheatsheet/) | Per-topic time complexities, tips, and things to watch for |
| [CP-Algorithms](https://cp-algorithms.com) | In-depth algorithm references |
| [Bit Twiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html) | Classic bit manipulation tricks |
| [GeeksforGeeks DSA](https://www.geeksforgeeks.org/dsa/dsa-tutorial-learn-data-structures-and-algorithms/) | Articles on nearly every topic, with code in several languages |

---

## Visualize and drill

| Resource | What it is |
| -------- | ---------- |
| [VisuAlgo](https://visualgo.net) | Watch algorithms run step by step. Great for trees, graphs, and sorting. |
| [Algorithm Visualizer](https://algorithm-visualizer.org) | Interactive code plus animation for common algorithms. |
| [Data Structure Visualizations (USFCA)](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html) | Step-through animations for classic data structures. |
| [Python Tutor](https://pythontutor.com) | Visualize how your own code executes, line by line. Excellent for recursion and linked lists. |
| [Codewars](https://www.codewars.com) | Gamified challenges for building fluency. |

---

## YouTube channels

| Channel | Best for |
| ------- | -------- |
| [NeetCode](https://www.youtube.com/@NeetCode) | Clear explanations of interview problems. |
| [Take U Forward (Striver)](https://www.youtube.com/@takeUforward) | DSA roadmap and placement prep, popular in India. |
| [Greg Hogg](https://www.youtube.com/@GregHogg/playlists) | Clean, pattern-focused explanations. |
| [Abdul Bari](https://www.youtube.com/@Abdul_Bari) | Algorithms from first principles. |
| [Back To Back SWE](https://www.youtube.com/@BackToBackSWE) | Detailed walkthroughs of harder problems. |
| [CrackFAANG](https://www.youtube.com/@crackfaang/playlists) | FAANG-focused interview prep. |
| [William Fiset](https://www.youtube.com/@WilliamFiset-videos) | Graph theory and data structure implementations, explained very clearly. |
| [mycodeschool](https://www.youtube.com/@mycodeschool) | Classic linked list, pointers, and recursion lessons. |
| [Aditya Verma](https://www.youtube.com/@TheAdityaVerma) | Dynamic programming and recursion series, popular in India. |
| [Kunal Kushwaha](https://www.youtube.com/@KunalKushwaha) | DSA with Java, beginner friendly. |
| [Errichto](https://www.youtube.com/@Errichto) | Competitive programming techniques and contest walkthroughs. |
| [Reducible](https://www.youtube.com/@Reducible) | Visual explanations of how algorithms work. |

---

## Big-O cheat sheet

### Common complexities

| Complexity | Name | Typical example |
| ---------- | ---- | --------------- |
| O(1) | Constant | Hash map lookup, array index |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Single pass through an array |
| O(n log n) | Linearithmic | Merge sort, heap sort |
| O(n^2) | Quadratic | Nested loops, bubble sort |
| O(2^n) | Exponential | Naive recursion for subsets |
| O(n!) | Factorial | Generating all permutations |

### Input size hints

A rough guide for what complexity fits typical time limits:

| Input size n | Likely target |
| ------------ | ------------- |
| up to 10 to 12 | O(n!) or O(2^n) may work (backtracking) |
| up to 20 to 25 | O(2^n) |
| up to 500 | O(n^3) |
| up to 5,000 | O(n^2) |
| up to 100,000 to 1,000,000 | O(n log n) or O(n) |
| above 10^8 | O(log n) or O(1) |

### Data structure operations (average case)

| Structure | Access | Search | Insert | Delete |
| --------- | ------ | ------ | ------ | ------ |
| Array | O(1) | O(n) | O(n) | O(n) |
| Linked list | O(n) | O(n) | O(1) at known node | O(1) at known node |
| Hash map | n/a | O(1) | O(1) | O(1) |
| Balanced BST | O(log n) | O(log n) | O(log n) | O(log n) |
| Heap | O(1) for min/max | O(n) | O(log n) | O(log n) |

### Sorting algorithms

| Algorithm | Best | Average | Worst | Space | Stable |
| --------- | ---- | ------- | ----- | ----- | ------ |
| Bubble sort | O(n) | O(n^2) | O(n^2) | O(1) | Yes |
| Insertion sort | O(n) | O(n^2) | O(n^2) | O(1) | Yes |
| Merge sort | O(n log n) | O(n log n) | O(n log n) | O(n) | Yes |
| Quick sort | O(n log n) | O(n log n) | O(n^2) | O(log n) | No |
| Heap sort | O(n log n) | O(n log n) | O(n log n) | O(1) | No |
| Counting sort | O(n + k) | O(n + k) | O(n + k) | O(k) | Yes |

---

## Progress tracker

Copy this into your own notes or fork the repo and tick boxes as you go.

**Fundamentals**
- [ ] Big-O and complexity analysis
- [ ] Arrays and strings
- [ ] Hash maps and sets
- [ ] Linked lists
- [ ] Stacks and queues
- [ ] Recursion
- [ ] Sorting and binary search
- [ ] Trees and BSTs
- [ ] Heaps
- [ ] Graphs (BFS, DFS)
- [ ] Tries
- [ ] Dynamic programming
- [ ] Greedy
- [ ] Bit manipulation

**Patterns**
- [ ] Two pointers
- [ ] Sliding window
- [ ] Prefix sums
- [ ] Fast and slow pointers
- [ ] Monotonic stack
- [ ] Binary search on answer
- [ ] Merge intervals
- [ ] Top-K with heaps
- [ ] Backtracking
- [ ] Union-Find
- [ ] Topological sort
- [ ] Shortest paths (Dijkstra)
- [ ] 1D and 2D DP

**Milestones**
- [ ] 50 problems solved and logged
- [ ] 100 problems solved and logged
- [ ] Finished a core list (Blind 75 or NeetCode 150)
- [ ] 5 timed mock interviews
- [ ] Re-solved 20 earlier problems from memory

---

## Common mistakes

- **Grinding without reviewing.** Solving 500 problems you barely understood is worse than 150 you understand deeply.
- **Jumping to the solution too early.** Struggling for 15 to 20 minutes is where the learning happens.
- **Switching languages or lists.** Pick one of each and finish.
- **Skipping easy problems.** They build the fluency harder problems depend on.
- **Ignoring edge cases.** Interviewers watch for empty inputs, negatives, duplicates, and overflow.
- **Only coding in the LeetCode editor.** Practice in a plain editor sometimes, and explain out loud.
- **Skipping revision.** Without spaced review, patterns fade within weeks.
- **Memorising solutions.** Memorise the idea and the template, not the code.

---

## FAQ

**How many LeetCode problems do I need to solve?**
150 well-understood problems across all patterns beats 500 you barely understood. Measure progress by pattern mastery, not problem count.

**Should I do competitive programming or just LeetCode?**
For getting a job this year, focus on LeetCode-style pattern practice. For long-term problem-solving strength, competitive programming helps too. If placements are close, stay focused on one track.

**Do I need LeetCode Premium?**
No. This repo uses only free resources. [Leetracer](https://leetracer.com/screener) gives you company-tagged questions for free.

**Is DSA enough to get a job?**
It gets you through the coding rounds. You also need projects, core CS subjects (OS, DBMS, networks), and for experienced roles, system design. See the [main roadmap](https://github.com/DivaQueen-dev/free-cs-roadmap).

**I am from a non-CS branch. Can I still do this?**
Yes. Follow the same steps. The [main roadmap](https://github.com/DivaQueen-dev/free-cs-roadmap) has a dedicated non-CS path.

**How long until I'm interview-ready?**
Most people with consistent daily practice are ready in 3 to 6 months from the basics. The plans above give a rough structure.

**Which is better: Python, Java, or C++?**
Whichever you know best. Python is fastest to write, C++ is fastest to run, Java is common in Indian campus placements. Interviewers rarely care which you pick.

**I keep losing motivation. What do I do?**
Set a daily minimum so small that skipping it would feel silly (one problem, 30 minutes). Find a study partner in our [Discord](https://discord.gg/ETCSm74A59).

---

## Contributing

Found a better resource, a broken link, or an error? Open an issue or a pull request.

We accept: free resources you have personally verified, with a clear description, in the right section.
We don't accept: paid resources, affiliate links, or low-quality content.

---

## Related repos

| Repo | What's inside |
| ---- | ------------- |
| [free-cs-roadmap](https://github.com/DivaQueen-dev/free-cs-roadmap) | The main hub: all domains, resume tips, getting hired |
| [free-system-design-roadmap](https://github.com/DivaQueen-dev/free-system-design-roadmap) | System design fundamentals and interview problems |
| [free-ai-ml-llm-roadmap](https://github.com/DivaQueen-dev/free-ai-ml-llm-roadmap) | AI/ML, deep learning, RAG and LLMs |

---

Built for students who deserve a fair shot but can't afford a paywall. If this helped you, share it with one person who needs it and star the repo.

[Join Discord](https://discord.gg/ETCSm74A59)
