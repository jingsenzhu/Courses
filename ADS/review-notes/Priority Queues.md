### Leftist Heaps and Skew Heaps
#### Leftist Heaps

* Target :  Speed up merging in $O(N)$.
* Null path length Npl(X) of node X: the length of the shortest path from X to a node without two children
  * Npl(NULL) = -1
  * Npl(X) = min { Npl(C) + 1 for all C as children of X }
* **Leftist heap priority**: for every node X in the heap, the null path length of the **left** child is **at least as large as** that of the right child
* A leftist tree with r nodes on the right path must have at least $2^r – 1$ nodes.
* Merge
  * Recursive version (omitted)
  * Iterative version
    * Sort right paths without changing their left children
    * Swap children if necessary
* Delete: delete root and merge subtrees
* Insert: Merge 1 new node and the heap

#### Skew Heaps

* Merge: Always swap the left and right children
* Amortized analysis
  * $D_i$ = the root of the resulting tree
  * $\Phi(D_i)$ = number of **heavy** nodes
    * Node p is heavy if the number of descendants of p’s right subtree (itself included) is at least half of the number of descendants of p, and light otherwise
  * $T_\text{amortized} = 3\lfloor \log_2N\rfloor+1$

### Binomial Queues

* $B_k$ consists of a root with $k$ children, which are $B_0,B_1,\ldots,B_{k-1}$.  $B_k$ has exactly $2^k$ nodes.  The number of nodes at depth $d$ is $\binom{k}{d}$
* A priority queue of any size can be uniquely represented by a collection of binomial trees
  * Binary representation of the size
* FindMin: $O(\log N)$
* Merge: Addition of binary numbers
* Implementation
  * left-child-next-sibling structure
  * the subtrees of a binomial tree are linked in decreasing sizes
* A binomial queue of $N$ elements can be built by $N$ successive insertions in $O(N)$ time.
  * Amortized analysis: $c_i$ = cost of the $i$th insertion, $\Phi_i$ = number of trees after the $i$th insertion 
    * $\hat{c}_i = c_i + \Phi_i - \Phi_{i-1} = 2$

