# DSA Notes and Templates

Concise notes, pattern recognition cues, and copy-ready Python templates. Use these alongside the [roadmap](README.md). Memorise the idea behind each template, not the exact code.

## Contents

1. [How to recognise a pattern](#how-to-recognise-a-pattern)
2. [Arrays and hashing](#arrays-and-hashing)
3. [Two pointers](#two-pointers)
4. [Sliding window](#sliding-window)
5. [Prefix sums](#prefix-sums)
6. [Stack and monotonic stack](#stack-and-monotonic-stack)
7. [Binary search](#binary-search)
8. [Linked lists](#linked-lists)
9. [Trees](#trees)
10. [Heaps and top-K](#heaps-and-top-k)
11. [Backtracking](#backtracking)
12. [Graphs](#graphs)
13. [Union-Find](#union-find)
14. [Topological sort](#topological-sort)
15. [Shortest paths](#shortest-paths)
16. [Tries](#tries)
17. [Dynamic programming](#dynamic-programming)
18. [Greedy and intervals](#greedy-and-intervals)
19. [Bit manipulation](#bit-manipulation)
20. [Python interview cheat sheet](#python-interview-cheat-sheet)
21. [Edge-case checklist](#edge-case-checklist)

---

## How to recognise a pattern

| If the problem says... | Think about... |
| ---------------------- | -------------- |
| Sorted array, find a pair or triplet | Two pointers |
| Longest or shortest subarray/substring with a condition | Sliding window |
| Sum of a range, or subarray sums equal to k | Prefix sums plus a hash map |
| Next greater or smaller element, histogram | Monotonic stack |
| Sorted input, or "minimum value such that..." | Binary search (possibly on the answer) |
| Cycle, middle of a list | Fast and slow pointers |
| Top K, K-th largest, running median | Heap |
| All combinations, permutations, subsets | Backtracking |
| Shortest path in an unweighted graph or grid | BFS |
| Connected components, "are these connected?" | DFS, BFS, or Union-Find |
| Task ordering, prerequisites | Topological sort |
| Shortest path with weights | Dijkstra |
| Overlapping subproblems, "count the ways", "min/max cost" | Dynamic programming |
| Prefix searches, autocomplete | Trie |
| Overlapping intervals, scheduling | Sort, then sweep (greedy) |
| Constraint n <= 20 | Bitmask or backtracking |
| "Do it in O(1) space" with numbers | XOR or in-place tricks |

When stuck, ask: can I sort it, can I use a hash map to remember something, can I process it with two pointers, or can I break it into smaller identical problems?

---

## Arrays and hashing

**Key ideas**
- A hash map turns "have I seen this?" from O(n) into O(1). Most "find a pair" and "count something" problems become one pass with a map.
- Frequency counting: `Counter` in Python.
- Grouping: use a canonical key (for anagrams, the sorted string or a tuple of letter counts).
- In-place tricks (swap, two-pass) help when space is restricted.

**Template: Two Sum with a hash map**

```python
def two_sum(nums, target):
    seen = {}                      # value -> index
    for i, x in enumerate(nums):
        if target - x in seen:
            return [seen[target - x], i]
        seen[x] = i
    return []
```

**Template: product of array except self (no division)**

```python
def product_except_self(nums):
    n = len(nums)
    res = [1] * n
    left = 1
    for i in range(n):
        res[i] = left
        left *= nums[i]
    right = 1
    for i in range(n - 1, -1, -1):
        res[i] *= right
        right *= nums[i]
    return res
```

**Watch out for:** mutating a list while iterating; assuming input is sorted; forgetting duplicates.

---

## Two pointers

**Key ideas**
- Works when moving a pointer has a predictable effect (usually on sorted data).
- Opposite ends: pairs, palindromes, container problems.
- Same direction: removing duplicates, partitioning, merging.

**Template: pair with target sum in a sorted array**

```python
def two_sum_sorted(nums, target):
    l, r = 0, len(nums) - 1
    while l < r:
        s = nums[l] + nums[r]
        if s == target:
            return [l, r]
        if s < target:
            l += 1
        else:
            r -= 1
    return []
```

**Template: 3Sum (sort, fix one, two pointers)**

```python
def three_sum(nums):
    nums.sort()
    res = []
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i - 1]:
            continue                       # skip duplicate first elements
        l, r = i + 1, len(nums) - 1
        while l < r:
            s = nums[i] + nums[l] + nums[r]
            if s < 0:
                l += 1
            elif s > 0:
                r -= 1
            else:
                res.append([nums[i], nums[l], nums[r]])
                l += 1
                while l < r and nums[l] == nums[l - 1]:
                    l += 1
    return res
```

**Watch out for:** skipping duplicates correctly; off-by-one at the loop boundaries.

---

## Sliding window

**Key ideas**
- Maintain a window `[left, right]`. Expand `right` each step. Shrink `left` while the window is invalid.
- Fixed-size window: slide by adding the new element and removing the old one.
- Variable-size window: use for "longest/shortest subarray with condition".
- Each element enters and leaves at most once, so the total is O(n).

**Template: variable window (generic)**

```python
from collections import defaultdict

def window(s):
    count = defaultdict(int)
    left = 0
    best = 0
    for right, ch in enumerate(s):
        count[ch] += 1                    # add s[right] to the window
        while invalid(count):             # shrink until valid again
            count[s[left]] -= 1
            left += 1
        best = max(best, right - left + 1)
    return best
```

**Template: longest substring without repeating characters**

```python
def longest_unique(s):
    last = {}                              # char -> last index seen
    left = best = 0
    for right, ch in enumerate(s):
        if ch in last and last[ch] >= left:
            left = last[ch] + 1
        last[ch] = right
        best = max(best, right - left + 1)
    return best
```

**Watch out for:** deciding what "invalid" means precisely; updating the answer at the right moment (inside or after the while loop).

---

## Prefix sums

**Key ideas**
- `prefix[i]` = sum of the first `i` elements. Sum of range `[l, r]` = `prefix[r+1] - prefix[l]`.
- Combined with a hash map, counts subarrays with a given sum in O(n).

**Template: subarray sum equals k**

```python
def subarray_sum(nums, k):
    seen = {0: 1}                          # prefix sum -> how many times seen
    total = count = 0
    for x in nums:
        total += x
        count += seen.get(total - k, 0)    # earlier prefix that gives sum k
        seen[total] = seen.get(total, 0) + 1
    return count
```

**Template: Kadane's algorithm (max subarray)**

```python
def max_subarray(nums):
    best = cur = nums[0]
    for x in nums[1:]:
        cur = max(x, cur + x)              # extend or restart
        best = max(best, cur)
    return best
```

**Watch out for:** negative numbers break sliding window for sums, so use prefix sums with a map instead.

---

## Stack and monotonic stack

**Key ideas**
- Stack: last in, first out. Good for matching brackets, undo, evaluating expressions, DFS.
- Monotonic stack: keep the stack sorted (increasing or decreasing). Each element is pushed and popped once, so O(n).
- Use it for "next greater/smaller element" and "largest rectangle" problems.

**Template: valid parentheses**

```python
def is_valid(s):
    pairs = {')': '(', ']': '[', '}': '{'}
    stack = []
    for ch in s:
        if ch in pairs:
            if not stack or stack.pop() != pairs[ch]:
                return False
        else:
            stack.append(ch)
    return not stack
```

**Template: next greater element**

```python
def next_greater(nums):
    res = [-1] * len(nums)
    stack = []                             # indices with decreasing values
    for i, x in enumerate(nums):
        while stack and nums[stack[-1]] < x:
            res[stack.pop()] = x
        stack.append(i)
    return res
```

**Template: daily temperatures (days until warmer)**

```python
def daily_temperatures(temps):
    res = [0] * len(temps)
    stack = []
    for i, t in enumerate(temps):
        while stack and temps[stack[-1]] < t:
            j = stack.pop()
            res[j] = i - j
        stack.append(i)
    return res
```

**Watch out for:** deciding whether to store values or indices (indices are usually more useful); strict vs non-strict comparison.

---

## Binary search

**Key ideas**
- Works on any monotonic condition, not just sorted arrays.
- "Search on the answer": if you can check "is value x feasible?" quickly and feasibility is monotonic, binary search the answer.
- Compute `mid = lo + (hi - lo) // 2` to avoid overflow in other languages.
- Choose one loop style and use it consistently.

**Template: classic search**

```python
def binary_search(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = lo + (hi - lo) // 2
        if nums[mid] == target:
            return mid
        if nums[mid] < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return -1
```

**Template: smallest feasible value (search on answer)**

```python
def min_feasible(lo, hi, feasible):
    # feasible(x) is False...False True...True
    while lo < hi:
        mid = lo + (hi - lo) // 2
        if feasible(mid):
            hi = mid                       # mid might be the answer
        else:
            lo = mid + 1
    return lo
```

Example: Koko Eating Bananas. `feasible(speed)` = can she finish within `h` hours at this speed.

```python
import math

def min_eating_speed(piles, h):
    return min_feasible(1, max(piles),
                        lambda k: sum(math.ceil(p / k) for p in piles) <= h)
```

**Watch out for:** infinite loops (make sure the range shrinks each iteration); rotated arrays (decide which half is sorted first); using `bisect` from the standard library when you only need lower/upper bound.

---

## Linked lists

**Key ideas**
- Use a dummy head node to simplify edge cases (inserting or deleting at the head).
- Fast and slow pointers find the middle, detect cycles, and find the start of a cycle.
- Reversing a list is a building block for many problems (palindrome check, reorder list).
- Draw the pointers before coding.

**Template: reverse a linked list**

```python
def reverse(head):
    prev = None
    while head:
        nxt = head.next
        head.next = prev
        prev = head
        head = nxt
    return prev
```

**Template: detect a cycle**

```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow is fast:
            return True
    return False
```

**Template: merge two sorted lists (dummy node)**

```python
def merge_two(a, b):
    dummy = tail = ListNode()
    while a and b:
        if a.val <= b.val:
            tail.next, a = a, a.next
        else:
            tail.next, b = b, b.next
        tail = tail.next
    tail.next = a or b
    return dummy.next
```

**Watch out for:** losing a reference to the rest of the list before reassigning `next`; null checks on `fast.next`.

---

## Trees

**Key ideas**
- Most tree problems are recursion: solve for the left and right subtrees, then combine.
- DFS (preorder, inorder, postorder) uses recursion or a stack. BFS uses a queue and gives level order.
- Inorder traversal of a BST gives sorted values.
- For "path" problems, a recursive helper often returns one value up and updates a global answer.

**Template: DFS recursion**

```python
def max_depth(root):
    if not root:
        return 0
    return 1 + max(max_depth(root.left), max_depth(root.right))
```

**Template: BFS level order**

```python
from collections import deque

def level_order(root):
    if not root:
        return []
    res, q = [], deque([root])
    while q:
        level = []
        for _ in range(len(q)):            # process exactly one level
            node = q.popleft()
            level.append(node.val)
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
        res.append(level)
    return res
```

**Template: validate a BST (carry bounds down)**

```python
def is_valid_bst(root, lo=float('-inf'), hi=float('inf')):
    if not root:
        return True
    if not (lo < root.val < hi):
        return False
    return (is_valid_bst(root.left, lo, root.val) and
            is_valid_bst(root.right, root.val, hi))
```

**Template: path problem with a global answer (max path sum)**

```python
def max_path_sum(root):
    best = float('-inf')

    def gain(node):
        nonlocal best
        if not node:
            return 0
        left = max(gain(node.left), 0)     # ignore negative branches
        right = max(gain(node.right), 0)
        best = max(best, node.val + left + right)   # path through this node
        return node.val + max(left, right)          # path extendable upward

    gain(root)
    return best
```

**Watch out for:** comparing only a node with its children when validating a BST (you must carry bounds); recursion depth on skewed trees.

---

## Heaps and top-K

**Key ideas**
- A heap gives the min (or max) in O(1) and insert/remove in O(log n).
- Python's `heapq` is a min-heap. For a max-heap, push negated values.
- Top K largest: keep a min-heap of size K. Anything smaller than the heap's top is discarded.
- Running median: two heaps (max-heap for the lower half, min-heap for the upper half).

**Template: K-th largest element**

```python
import heapq

def kth_largest(nums, k):
    heap = []
    for x in nums:
        heapq.heappush(heap, x)
        if len(heap) > k:
            heapq.heappop(heap)            # drop the smallest
    return heap[0]
```

**Template: top K frequent**

```python
import heapq
from collections import Counter

def top_k_frequent(nums, k):
    count = Counter(nums)
    return heapq.nlargest(k, count.keys(), key=count.get)
```

**Template: merge K sorted lists**

```python
import heapq

def merge_k_lists(lists):
    heap = []
    for i, node in enumerate(lists):
        if node:
            heapq.heappush(heap, (node.val, i, node))   # i breaks ties
    dummy = tail = ListNode()
    while heap:
        _, i, node = heapq.heappop(heap)
        tail.next = node
        tail = node
        if node.next:
            heapq.heappush(heap, (node.next.val, i, node.next))
    return dummy.next
```

**Watch out for:** pushing tuples whose second element isn't comparable (add an index as a tie-breaker).

---

## Backtracking

**Key ideas**
- Build a solution step by step. At each step, choose, explore, then undo the choice (backtrack).
- Prune early: stop exploring a branch as soon as it can't lead to a valid answer.
- Typical shapes: subsets (include/exclude), permutations (use each element once), combinations (start index to avoid repeats).
- Sort first and skip equal neighbours to avoid duplicate results.

**Template: subsets**

```python
def subsets(nums):
    res, path = [], []

    def backtrack(start):
        res.append(path[:])                # copy the current path
        for i in range(start, len(nums)):
            path.append(nums[i])
            backtrack(i + 1)
            path.pop()                     # undo

    backtrack(0)
    return res
```

**Template: permutations**

```python
def permutations(nums):
    res, path = [], []
    used = [False] * len(nums)

    def backtrack():
        if len(path) == len(nums):
            res.append(path[:])
            return
        for i in range(len(nums)):
            if used[i]:
                continue
            used[i] = True
            path.append(nums[i])
            backtrack()
            path.pop()
            used[i] = False

    backtrack()
    return res
```

**Template: combination sum (reuse allowed)**

```python
def combination_sum(candidates, target):
    res, path = [], []

    def backtrack(start, remaining):
        if remaining == 0:
            res.append(path[:])
            return
        for i in range(start, len(candidates)):
            if candidates[i] > remaining:
                continue
            path.append(candidates[i])
            backtrack(i, remaining - candidates[i])   # i, not i + 1: reuse allowed
            path.pop()

    backtrack(0, target)
    return res
```

**Watch out for:** appending `path` instead of `path[:]` (all results end up identical); forgetting to undo state.

---

## Graphs

**Key ideas**
- Represent as an adjacency list: `graph[u] = [v1, v2, ...]`. Use a set for visited nodes.
- DFS: go deep. Good for connected components, cycle detection, path existence.
- BFS: go level by level. Gives the shortest path in unweighted graphs.
- Grids are graphs. Neighbours are up, down, left, right (add diagonals if allowed).
- Always mark nodes visited when you add them to the queue (BFS) to avoid duplicates.

**Template: build an adjacency list**

```python
from collections import defaultdict

graph = defaultdict(list)
for a, b in edges:
    graph[a].append(b)
    graph[b].append(a)                     # omit for directed graphs
```

**Template: DFS on a grid (count islands)**

```python
def num_islands(grid):
    R, C = len(grid), len(grid[0])
    count = 0

    def dfs(r, c):
        if not (0 <= r < R and 0 <= c < C) or grid[r][c] != '1':
            return
        grid[r][c] = '0'                   # mark visited
        for dr, dc in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            dfs(r + dr, c + dc)

    for r in range(R):
        for c in range(C):
            if grid[r][c] == '1':
                dfs(r, c)
                count += 1
    return count
```

**Template: BFS shortest path on a grid**

```python
from collections import deque

def shortest_path(grid, start, goal):
    R, C = len(grid), len(grid[0])
    q = deque([(start[0], start[1], 0)])
    seen = {start}
    while q:
        r, c, d = q.popleft()
        if (r, c) == goal:
            return d
        for dr, dc in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            nr, nc = r + dr, c + dc
            if (0 <= nr < R and 0 <= nc < C
                    and (nr, nc) not in seen and grid[nr][nc] != '#'):
                seen.add((nr, nc))
                q.append((nr, nc, d + 1))
    return -1
```

**Template: detect a cycle in a directed graph (DFS colours)**

```python
def has_cycle_directed(n, graph):
    WHITE, GRAY, BLACK = 0, 1, 2
    state = [WHITE] * n

    def dfs(u):
        state[u] = GRAY
        for v in graph[u]:
            if state[v] == GRAY:
                return True                # back edge
            if state[v] == WHITE and dfs(v):
                return True
        state[u] = BLACK
        return False

    return any(state[u] == WHITE and dfs(u) for u in range(n))
```

**Watch out for:** infinite loops from missing visited checks; marking visited too late in BFS; recursion limits on large graphs (use an explicit stack).

---

## Union-Find

**Key ideas**
- Tracks which elements belong to the same group. Operations: `find` (which group?) and `union` (merge groups).
- With path compression and union by size, each operation is nearly O(1).
- Use it for connected components, detecting cycles in undirected graphs, and Kruskal's MST.

**Template**

```python
class DSU:
    def __init__(self, n):
        self.parent = list(range(n))
        self.size = [1] * n

    def find(self, x):
        while self.parent[x] != x:
            self.parent[x] = self.parent[self.parent[x]]   # path compression
            x = self.parent[x]
        return x

    def union(self, a, b):
        ra, rb = self.find(a), self.find(b)
        if ra == rb:
            return False                   # already connected (cycle)
        if self.size[ra] < self.size[rb]:
            ra, rb = rb, ra
        self.parent[rb] = ra
        self.size[ra] += self.size[rb]
        return True
```

Example: redundant connection. Return the first edge where `union` returns `False`.

---

## Topological sort

**Key ideas**
- Orders nodes of a directed acyclic graph so every edge goes from earlier to later.
- Kahn's algorithm: repeatedly remove nodes with in-degree 0. If you can't remove all nodes, there is a cycle.
- Typical use: course schedule, build order, task dependencies.

**Template: Kahn's algorithm**

```python
from collections import deque

def topo_sort(n, edges):                   # edge (a, b) means a before b
    graph = [[] for _ in range(n)]
    indegree = [0] * n
    for a, b in edges:
        graph[a].append(b)
        indegree[b] += 1

    q = deque(i for i in range(n) if indegree[i] == 0)
    order = []
    while q:
        u = q.popleft()
        order.append(u)
        for v in graph[u]:
            indegree[v] -= 1
            if indegree[v] == 0:
                q.append(v)
    return order if len(order) == n else []   # empty list means cycle
```

---

## Shortest paths

**Key ideas**
- Unweighted graph: BFS.
- Non-negative weights: Dijkstra with a min-heap, O((V + E) log V).
- Negative weights: Bellman-Ford, O(V * E). Also used for "at most K edges" problems.
- Skip stale heap entries (`if d > dist[u]: continue`).

**Template: Dijkstra**

```python
import heapq

def dijkstra(graph, src):                  # graph[u] = [(v, weight), ...]
    dist = {src: 0}
    heap = [(0, src)]
    while heap:
        d, u = heapq.heappop(heap)
        if d > dist.get(u, float('inf')):
            continue                       # stale entry
        for v, w in graph[u]:
            nd = d + w
            if nd < dist.get(v, float('inf')):
                dist[v] = nd
                heapq.heappush(heap, (nd, v))
    return dist
```

**Template: Bellman-Ford with at most K edges (cheapest flights within K stops)**

```python
def cheapest_flights(n, flights, src, dst, k):
    dist = [float('inf')] * n
    dist[src] = 0
    for _ in range(k + 1):
        nxt = dist[:]                      # use last round's values only
        for a, b, w in flights:
            if dist[a] + w < nxt[b]:
                nxt[b] = dist[a] + w
        dist = nxt
    return dist[dst] if dist[dst] != float('inf') else -1
```

---

## Tries

**Key ideas**
- A tree where each edge is a character. Shared prefixes share nodes.
- Insert, search, and prefix lookup are all O(length of the word).
- Use for autocomplete, prefix matching, word search with many words.

**Template**

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.end = False


class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for ch in word:
            node = node.children.setdefault(ch, TrieNode())
        node.end = True

    def search(self, word):
        node = self._find(word)
        return node is not None and node.end

    def starts_with(self, prefix):
        return self._find(prefix) is not None

    def _find(self, s):
        node = self.root
        for ch in s:
            if ch not in node.children:
                return None
            node = node.children[ch]
        return node
```

---

## Dynamic programming

**Key ideas**
- DP is recursion plus remembering results. Use it when the same subproblem is solved repeatedly.
- Steps for any DP problem:
  1. Define the state: what does `dp[i]` (or `dp[i][j]`) mean in words?
  2. Write the transition: how does the state depend on smaller states?
  3. Set the base cases.
  4. Decide the order (top-down with memoisation, or bottom-up).
  5. Optimise space if only the last row or few values are needed.
- Start with the brute-force recursion, add `@cache`, then convert to a table if needed.

**Common DP families**

| Family | State | Examples |
| ------ | ----- | -------- |
| Linear (1D) | `dp[i]` = best answer for the first i items | Climbing stairs, house robber, decode ways |
| Knapsack | `dp[i][w]` or `dp[w]` | Coin change, subset sum, partition equal subset |
| Subsequence | `dp[i]` = best ending at i | Longest increasing subsequence |
| Two strings (2D) | `dp[i][j]` over prefixes | LCS, edit distance |
| Grid | `dp[r][c]` | Unique paths, minimum path sum |
| Interval | `dp[l][r]` | Burst balloons, palindrome partitioning |

**Template: top-down with memoisation**

```python
from functools import cache

def climb_stairs(n):
    @cache
    def f(i):
        if i <= 1:
            return 1
        return f(i - 1) + f(i - 2)
    return f(n)
```

**Template: 1D bottom-up (house robber)**

```python
def rob(nums):
    prev2 = prev1 = 0
    for x in nums:
        prev2, prev1 = prev1, max(prev1, prev2 + x)
    return prev1
```

**Template: unbounded knapsack (coin change, minimum coins)**

```python
def coin_change(coins, amount):
    INF = float('inf')
    dp = [0] + [INF] * amount
    for a in range(1, amount + 1):
        for c in coins:
            if c <= a:
                dp[a] = min(dp[a], dp[a - c] + 1)
    return dp[amount] if dp[amount] != INF else -1
```

**Template: 0/1 subset sum (partition equal subset sum)**

```python
def can_partition(nums):
    total = sum(nums)
    if total % 2:
        return False
    target = total // 2
    dp = [True] + [False] * target
    for x in nums:
        for s in range(target, x - 1, -1):   # go backwards: each item used once
            dp[s] = dp[s] or dp[s - x]
    return dp[target]
```

**Template: longest increasing subsequence in O(n log n)**

```python
import bisect

def length_of_lis(nums):
    tails = []
    for x in nums:
        i = bisect.bisect_left(tails, x)
        if i == len(tails):
            tails.append(x)
        else:
            tails[i] = x
    return len(tails)
```

**Template: two strings (longest common subsequence)**

```python
def lcs(a, b):
    m, n = len(a), len(b)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if a[i - 1] == b[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
    return dp[m][n]
```

**Template: edit distance**

```python
def edit_distance(a, b):
    m, n = len(a), len(b)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(m + 1):
        dp[i][0] = i                       # delete all of a[:i]
    for j in range(n + 1):
        dp[0][j] = j                       # insert all of b[:j]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if a[i - 1] == b[j - 1]:
                dp[i][j] = dp[i - 1][j - 1]
            else:
                dp[i][j] = 1 + min(dp[i - 1][j],      # delete
                                   dp[i][j - 1],      # insert
                                   dp[i - 1][j - 1])  # replace
    return dp[m][n]
```

**Watch out for:** unclear state definition (write it in words first); wrong iteration direction in knapsack (forwards allows reuse, backwards means each item once); mutable default arguments in memoisation.

---

## Greedy and intervals

**Key ideas**
- Greedy makes the locally best choice at each step. It works only when that choice never needs to be undone. Always try to justify why (an exchange argument) or test against small cases.
- Many greedy problems start with sorting.
- Interval problems: sort by start (merging) or by end (scheduling the most non-overlapping intervals).

**Template: merge intervals**

```python
def merge(intervals):
    intervals.sort(key=lambda x: x[0])
    res = [intervals[0]]
    for start, end in intervals[1:]:
        if start <= res[-1][1]:            # overlaps with the last merged one
            res[-1][1] = max(res[-1][1], end)
        else:
            res.append([start, end])
    return res
```

**Template: jump game**

```python
def can_jump(nums):
    farthest = 0
    for i, x in enumerate(nums):
        if i > farthest:
            return False
        farthest = max(farthest, i + x)
    return True
```

**Template: non-overlapping intervals (minimum removals)**

```python
def erase_overlap_intervals(intervals):
    intervals.sort(key=lambda x: x[1])     # sort by end time
    end = float('-inf')
    removed = 0
    for s, e in intervals:
        if s >= end:
            end = e                        # keep this interval
        else:
            removed += 1                   # overlaps: drop it
    return removed
```

---

## Bit manipulation

**Useful identities**

| Expression | Meaning |
| ---------- | ------- |
| `x & 1` | Is x odd? |
| `x >> 1` | Divide by 2 (floor) |
| `x << 1` | Multiply by 2 |
| `x & (x - 1)` | Clear the lowest set bit |
| `x & -x` | Isolate the lowest set bit |
| `x ^ x == 0`, `x ^ 0 == x` | XOR cancels pairs |
| `1 << k` | A mask with only bit k set |
| `(x >> k) & 1` | Value of bit k |
| `x & (x - 1) == 0` and `x > 0` | x is a power of two |

**Template: count set bits**

```python
def count_bits(x):
    count = 0
    while x:
        x &= x - 1                         # removes the lowest set bit
        count += 1
    return count
```

**Template: single number (every other element appears twice)**

```python
def single_number(nums):
    res = 0
    for x in nums:
        res ^= x
    return res
```

**Template: subsets with bitmasks (n <= 20)**

```python
def all_subsets(nums):
    n = len(nums)
    return [[nums[i] for i in range(n) if mask >> i & 1]
            for mask in range(1 << n)]
```

**Watch out for:** Python integers are unbounded (no overflow), but in Java or C++ watch for 32-bit overflow and signed shifts.

---

## Python interview cheat sheet

**Containers**

```python
from collections import Counter, defaultdict, deque
import heapq, bisect

count = Counter("aabbc")                   # Counter({'a': 2, 'b': 2, 'c': 1})
count.most_common(2)                       # top 2 by frequency

groups = defaultdict(list)                 # missing keys start as []
groups["x"].append(1)

q = deque([1, 2, 3])
q.append(4); q.popleft()                   # O(1) at both ends

heap = []
heapq.heappush(heap, 5); heapq.heappop(heap)    # min-heap
heapq.heappush(heap, -5)                   # max-heap trick: negate
heapq.heapify(lst)                         # in-place O(n)

bisect.bisect_left(arr, x)                 # first index where arr[i] >= x
bisect.bisect_right(arr, x)                # first index where arr[i] > x
```

**Sorting**

```python
nums.sort()                                # in place
sorted(nums, reverse=True)                 # new list
points.sort(key=lambda p: (p[0], -p[1]))   # multiple keys
words.sort(key=len)
```

**Useful built-ins**

```python
float('inf'), float('-inf')                # sentinels
divmod(17, 5)                              # (3, 2)
a // b, a % b                              # floor division, modulo
enumerate(nums), zip(a, b)
any(...), all(...)
sum(x for x in nums if x > 0)
max(nums, key=lambda x: abs(x))
```

**itertools**

```python
from itertools import permutations, combinations, accumulate, product
list(permutations([1, 2, 3]))
list(combinations([1, 2, 3], 2))
list(accumulate([1, 2, 3, 4]))             # [1, 3, 6, 10] prefix sums
```

**Strings and lists**

```python
s[::-1]                                    # reverse
"".join(chars)                             # build a string from a list
list(s)                                    # string to list of chars
ord('a'), chr(97)                          # char <-> code
s.isalnum(), s.isdigit(), s.lower()
nums[:]                                    # shallow copy
```

**Common traps**

```python
grid = [[0] * C for _ in range(R)]         # correct
grid = [[0] * C] * R                       # WRONG: all rows are the same list

import sys
sys.setrecursionlimit(10**6)               # deep recursion (use with care)

from functools import cache                # memoisation decorator (Python 3.9+)
```

**Complexity of common Python operations**

| Operation | Cost |
| --------- | ---- |
| `list.append`, `list.pop()` | O(1) |
| `list.pop(0)`, `list.insert(0, x)` | O(n), use `deque` instead |
| `x in list` | O(n) |
| `x in set` / `x in dict` | O(1) average |
| `list.sort()` | O(n log n) |
| String concatenation in a loop | O(n^2) overall, use `"".join` |
| Slicing `a[i:j]` | O(j - i) |

---

## Edge-case checklist

Run through this before you say "done" in an interview:

- Empty input (empty array, empty string, null tree, empty graph)
- Single element
- Two elements
- All elements equal
- Duplicates
- Already sorted, and reverse sorted
- Negative numbers and zero
- Very large values (overflow in Java and C++)
- Even and odd lengths
- Target not present
- Disconnected graph; graph with a cycle; self loops
- Tree that is a single node or a straight line
- Off-by-one at the first and last index
- Integer division and negative numbers (floor vs truncation differs between languages)
- Input modified in place: is that allowed?

When you finish, state the time and space complexity out loud and mention one trade-off you considered.
