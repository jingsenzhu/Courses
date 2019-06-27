### Local Search

* Local optimum : a best solution in a neighborhood
* Vertex Cover Problem : Given an undirected graph $G = (V, E)$.  Find a *minimum* subset $S$ of  $V$ such that for each edge $(u, v)$ in $E$, either $u$ or $v$  is in $S$.
* The Metropolis Algorithm
  * Simulated Annealing (模拟退火)
* Hopfield Neural Networks
  * $e=(u,v)$, if $w_e<0$ then $u,v$ want the same state; otherwise want different states
  * $e=(u,v)$ is good if $w_es_us_v<0$ ($s$ : state, = $\pm1$)
  * Node $u$ is satisfied if $\sum_{v:e=(u,v)\in E}w_es_us_v\leq 0$
  * Configuration is stable if all nodes satisfied
  * State-flipping algorithm
    * Stop before at most $\sum_e|w_e|$
* Maximum Cut Problem : find a node partition (A, B) such that the total weight of edges crossing the cut is maximized
  * Local optimal $w(A,B)\geq 0.5w(A^*,B^*)$ global optimal

### Randomized Algorithms

* Hiring problem
* Randomized Permutation Algorithm
* Online Hiring Algorithm 
  * $S_i$ = the $i$th applicant is best = $A\cap B$
    * $A$ = the best one is at position $i$ , $B$ = no one at positions $k+1 \sim i–1$ are hired 
    * $\text{Pr}[A] = 1/N, \text{Pr}[B] = k/(i-1), \text{Pr}[S_i] = \frac{k}{N(i-1)}$
    * $\text{Pr}[S] = \sum_{i=k+1}^N{\text{Pr}[S_i]} = \frac k N \sum_{i=k}^{N-1}{\frac 1 i}$
    * $\text{Pr}[S]\approx f(k) = \frac k N \ln(\frac N k)$, when $k = \frac e N$ largest

### Parallel Algorithms

* Summation problem ($\sum_{i=1}^N A_i$)
  * $\mathbf{B}(h, i)=\mathbf{B}(h-1,2 i-1)+\mathbf{B}(h-1,2 i)$
  * PRAM model
  * WD model
* Performance measure
  * Work load – total number of operations: $W(n)$
  * Worst-case running time: $T(n)$
  * $P(n) = W(n)/T(n)$ processors
* Maximum Finding
  * Partition by $\sqrt N$
    * $T(n) \leq T(\sqrt{n})+c_{1}$, $W(n) \leq \sqrt{n} W(\sqrt{n})+c_{2} n$
      * $T(n) = O(\log\log n)$, $W(n) = O(n\log\log n)$
  * Partition by $h = \log\log n$
    * $T(n) = O(\log\log n)$, $W(n) = O(n)$
  * Random Sampling
    * $T(n) = O(1), W(n) = O(n)$

### External Sorting

* Run : Internal Memory (size denoted $M$)
* k-way Merge
  * Number of passes = $1+\lceil \log_k(N/M) \rceil$
  * Require $2k$ tapes
* To reduce tapes (Polyphase Merge)
  * For k-way merge, $F_N^{(k)} = {F}_{N-{1}}^{(k)}+\cdots+{F}_{{N}-{k}}^{({k})}$
    * $T_1: F_N^{(k)} = {F}_{N-{1}}^{(k)}+\cdots+{F}_{{N}-{k}}^{({k})}$
    * $T_2: {F}_{N-{1}}^{(k)}+\cdots+{F}_{{N}-{k} + 1}^{({k})}$
    * $T_3: {F}_{N-{1}}^{(k)}+\cdots+{F}_{{N}-{k} + 2}^{({k})}$
    * $\cdots$
    * $T_k : {F}_{N-{1}}^{(k)}$
    * $T_{k+1} : 0$
  * k+1 tapes only
* Generate longer run (Replacement selection)