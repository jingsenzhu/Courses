### NP-Completeness

* Undecidable Problems
  * Halting problem
* NP (Nondeterministic polynomial-time)
  * The problem is NP if we can prove any solution is true in polynomial time. (多项式时间验证)
  * $P\subseteq NP$
* NP-Complete Problems
  * An NP-complete problem has the property that any problem in NP can be polynomially reduced to it.
  * $NPC=NP\cap NP\text{-}hard$
* Examples of NPC
  * Hamiltonian cycle problem
  * traveling salesman problem 
  * Circuit-SAT
  * Clique problem
  * Vertex cover problem
* Language
  * $L\in NP \implies \bar{L}\in \text{co-}NP$

### Approximation

* Approximation Ratio $\rho(n)$ : for input size $n$, cost $C$ and optimal cost $C^*$ : $\max(\frac C {C^*}, \frac {C^*} C) \leq \rho(n)$
  
  * The approximation algorithm is called a $\rho(n)$-approximation algorithm
  
* Approximation scheme: there is a value $\varepsilon > 0$ such that for any fixed $\varepsilon$, the scheme is a $(1+ \varepsilon)$-approximation algorithm.
  * polynomial-time approximation scheme (PTAS): for any fixed $\varepsilon > 0$, the scheme runs in time polynomial in the size n of its input instance, e.g. $O(n^{2/\varepsilon})$
  * fully polynomial-time approximation scheme (FPTAS): polynomial for both $n$ and $\varepsilon$, e.g. $O((1/\varepsilon)^2n^3)$
  
* Bin Packing (Let $M$ be optimal number)
  * Next Fit : $\leq 2M-1$
  * First Fit : $\leq 17(M-1)/10$
  * Best Fit: $\leq 1.7M$
  * On-line Algorithms
    * at least $\frac {5M} 3$
  * Off-line Algorithms
    * at least $\frac {11M} 9 + \frac 6 9$
  
* The Knapsack Problem — 0-1 version
  * Greedy: approximation ratio 2
  
  * Dynamic Programming
  
    * $W_{i,p}$ = the minimum weight of a collection from $\{1, …, i \}$ with total profit being  exactly $p$
  
    * $$
      \boldsymbol{W}_{i, p}=\left\{\begin{array}{l}{\infty} &i=0 \\ {\boldsymbol{W}_{i-1, p}} &p_i>p \\ {\min \left\{\boldsymbol{W}_{i-1, p}, \boldsymbol{w}_{i}+\boldsymbol{W}_{i-1, p-p_{i}}\right\}} &otherwise\end{array}\right.
      $$
  
    * $O(n^2p_{max})$
  
* The K-center Problem

  * Greedy : 2-approximation
  * unless P=NP, not exists $\rho<2$

