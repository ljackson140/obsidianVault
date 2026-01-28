**Big-O Key:**  
`n` = number of items, `m` = number of edges, `U` = universe size (for bitsets), `σ` = alphabet size (for tries)

### 1) Array / Dynamic Array (`T[]`, `List<T>`)

**Use when**

- Fast random access by index
- Iterating sequentially
- You know (or can grow) the size
- Cache-friendly workloads

**Ops & Complexity**

- Access by index: **O(1)**
- Append (amortized for dynamic arrays): **O(1)**
- Insert/Delete in middle: **O(n)**
- Search (unsorted): **O(n)**, (sorted + binary search): **O(log n)**

**Trade-offs**

- Resizing copies occasionally (for dynamic)
- Middle inserts/deletes are costly

---

### 2) Linked List (`LinkedList<T>`)

**Use when**

- Frequent inserts/removals at known positions (with references)
- Implementing queues/deques with stable node references

**Ops**

- Insert/Delete given node: **O(1)**
- Search by value: **O(n)**
- No random indexing

**Trade-offs**

- Poor cache locality
- Higher memory overhead (pointers)
- Usually slower than arrays for general iteration

---

### 3) Stack (`Stack<T>`)

**Use when**

- LIFO tasks: recursion elimination, backtracking, parsing, undo operations

**Ops**

- Push/Pop/Top: **O(1)**

**Trade-offs**

- Access to only top element

---

### 4) Queue (`Queue<T>`), Deque (`LinkedList<T>` or `Deque`)

**Use when**

- FIFO processing: BFS, job scheduling
- **Deque** for push/pop at both ends: sliding windows, monotonic queues

**Ops**

- Enqueue/Dequeue (Queue): **O(1)**
- Add/Remove Front/Back (Deque): **O(1)**

---

### 5) Hash Set / Hash Map (`HashSet<T>`, `Dictionary<TKey,TValue>`)

**Use when**

- Fast membership / frequency counting
- Deduplication
- Associative array (key → value)

**Ops**

- Insert/Find/Delete: **O(1)** average, **O(n)** worst-case (rare; depends on hashing)

**Trade-offs**

- No ordering (use `SortedDictionary`/`SortedSet` if needed)
- Requires good hash function & equality implementation
- Collisions degrade performance

---

### 6) Ordered Set / Ordered Map (`SortedSet<T>`, `SortedDictionary<TKey,TValue>`)

**Use when**

- Need **sorted** keys and fast queries
- Range queries, predecessor/successor, min/max

**Ops**

- Insert/Find/Delete: **O(log n)**
- Iterate in order: **O(n)**

**Trade-offs**

- Slower than hash-based structures for pure membership
- Backed by balanced BST (Red-Black Tree typically)

---

### 7) Binary Search Tree (BST), AVL, Red-Black Trees

**Use when**

- You need ordered data + **log time** insert/find/delete
- Augment nodes (e.g., order statistics, intervals)

**Ops**

- Insert/Find/Delete: **O(log n)** (balanced)
- Traversal: sorted order in **O(n)**

**Trade-offs**

- Self-balancing trees (AVL/RB) are harder to implement (use standard libraries)
- Unbalanced BST can degrade to **O(n)**

---

### 8) Heap / Priority Queue (`PriorityQueue<TElement,TPriority>` in .NET)

**Use when**

- Always need the smallest/largest item quickly
- Scheduling, Dijkstra’s, top-K, median-of-stream (with two heaps)

**Ops**

- Insert: **O(log n)**
- Peek min/max: **O(1)**
- Pop min/max: **O(log n)**

**Trade-offs**

- No fast arbitrary deletion or membership check
- Not sorted globally—just heap-ordered

---

### 9) Trie (Prefix Tree)

**Use when**

- Fast prefix lookups / autocomplete / dictionary words
- Many strings with shared prefixes
- Character-by-character search

**Ops**

- Insert/Search a word of length `L`: **O(L)**
- Prefix queries: **O(L)**

**Trade-offs**

- Memory-heavy (branching at each node)
- Better for small alphabets or compressed tries (radix)

---

### 10) Graph Representations

**Adjacency List**

- **Use when**: Sparse graphs
- Space: **O(n + m)**
- BFS/DFS: **O(n + m)**

**Adjacency Matrix**

- **Use when**: Dense graphs, constant-time edge checks
- Space: **O(n²)**
- Edge check: **O(1)**

**Trade-offs**

- Lists scale better for most real-world sparse graphs
- Matrix simplifies some algorithms (e.g., Floyd–Warshall)

---

### 11) Disjoint Set (Union–Find)

**Use when**

- Dynamic connectivity, Kruskal’s MST, connected components over unions

**Ops**

- `find` / `union`: **Amortized ~O(α(n))** (inverse Ackermann—effectively constant) with path compression + union by rank

**Trade-offs**

- Doesn’t give full set contents without extra structures
- Only answers connectivity / representative queries

---

### 12) Segment Tree / Fenwick Tree (Binary Indexed Tree)

**Use when**

- Range queries and point/range updates over arrays: sums, mins, maxes

**Segment Tree**

- Range query / point update: **O(log n)**
- Supports many functions (min/max/gcd/lazy range updates)

**Fenwick Tree**

- Prefix sums / point updates: **O(log n)**
- Simpler and more memory-efficient than segment tree
- Limited to invertible prefix operations (e.g., sum)

**Trade-offs**

- More implementation complexity than prefix sums
- Segment trees heavier but more flexible

---

### 13) Bitset / BitArray (`BitArray`)

**Use when**

- Memory-compact boolean flags across a known integer range
- Fast set membership when values map to indices

**Ops**

- Set/Clear/Test: **O(1)**
- Space: **O(U / 8)** bytes

**Trade-offs**

- Only for dense, bounded, non-negative domains
- May need mapping for negatives or sparse values

---

### 14) Bloom Filter (Probabilistic)

**Use when**

- **Space-efficient** membership test where **false positives are OK**, false negatives not allowed
- Caching layers, pre-filters

**Ops**

- Insert/Test: **O(k)** hash ops, usually constant small `k`

**Trade-offs**

- Cannot remove (without counting variants)
- Returns probabilistic answers—not suitable when exactness is required

---

### 15) LRU Cache

**Use when**

- You need a bounded-capacity cache that evicts least-recently-used entries

**Implementation**

- **HashMap + Doubly Linked List** → **O(1)** get/put/move-to-front

**Trade-offs**

- More moving parts; available as libraries in some ecosystems

---

### 16) Skip List

**Use when**

- Ordered structure with probabilistic balancing
- Alternative to balanced trees; simple to implement

**Ops**

- Insert/Find/Delete: **O(log n)** expected
- Iterate in order: **O(n)**

**Trade-offs**

- Constant factors higher than trees
- Not common in standard libraries

---

### 17) String/Sequence Specialists

**Rope**

- **Use when**: Many edits/concats on huge strings (text editors) — balanced trees of string chunks.
- Concat/split/insert: **O(log n)**.

**Suffix Array / Suffix Tree**

- **Use when**: Substring queries, pattern search, LCP computation at scale.
- Heavy to implement; used in advanced text search.

---

### 18) B-Tree / B+Tree

**Use when**

- Disk/page-friendly ordered indexes (databases, filesystems)
- Minimizes I/O; wide branching

**Ops**

- Insert/Find/Delete: **O(log n)** with excellent constants due to block layout

**Trade-offs**

- Overkill in-memory unless simulating paging
- Use DB/indexing engines rather than hand-rolling

---

# ⚖️ Quick Decision Guide

- **Need fast membership or dedup?** → `HashSet<T>`
- **Need counts/frequencies?** → `Dictionary<TKey,int>`
- **Need sorted keys or range queries?** → `SortedSet<T>` / `SortedDictionary<TKey,TValue>`
- **Need min/max often?** → `PriorityQueue<TElement,TPriority>`
- **Stream top-K elements?** → Min-heap of size `K`
- **Prefix search/autocomplete?** → Trie
- **Dynamic connectivity?** → Union–Find
- **Range sum/min with updates?** → Fenwick or Segment Tree
- **Exact graph algorithms (BFS/DFS/Dijkstra)?** → Adjacency List
- **Bitwise presence in small known domain?** → Bitset
- **Low-memory pre-check membership (allow false positives)?** → Bloom filter
- **Queue/Stack behavior?** → `Queue<T>` / `Stack<T>`
- **Frequent middle inserts/removals with known nodes?** → `LinkedList<T>`
- **Heavy string edits?** → Rope

---

# 🧠 Practical C# Tips

- For custom keys in `HashSet<T>`/`Dictionary<TKey,TValue>`, implement **`Equals`** and **`GetHashCode`** or provide an `IEqualityComparer<T>`.
- `SortedSet<T>`/`SortedDictionary<TKey,TValue>` use comparisons—implement `IComparable<T>` or provide an `IComparer<T>`.
- .NET’s `PriorityQueue<TElement,TPriority>` is min-heap by default (use negated priorities or wrap to simulate max-heap).
- Avoid mutating objects used as keys in hash-based or ordered structures.