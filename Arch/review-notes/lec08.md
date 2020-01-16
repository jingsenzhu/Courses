### Memory Hierarchy Cache Performance

#### Cache Performance

* Cache Locality

  * Temporal locality 
  * Spatial locality

* Time required for cache miss depends on:

  * Latency: the time to retrieve the first word of the block
  * Bandwidth: the time to retrieve the rest of this block

* Cache Miss Metrics

  * Memory stall cycles per mem access
  * Miss rate
  * Miss penalty

* Performance equations

  * CPU execution time $=(\mathrm{CPU} \text { clock cycles }+\text { Memory stall cycles) } \times$ Clock cycle time

  * $$
    \text{Memory stall cycles} = \text{Number of misses} \times \text{Miss penalty}
    \\
        \begin{array}{l}
        {=\mathrm{IC} \times \frac{\text { Misses }}{\text { Instruction }} \times \text { Miss penalty }} \\
        {=\mathrm{IC} \times \frac{\text { Memory accesses }}{\text { Instruction }} \times \text { Miss rate } \times \text { Miss penalty }}
        \end{array}
    $$

  * Memory stall clock cycles $=\mathrm{IC} \times$ Reads per instruction $\times$ Read miss rate $\times$ Read miss penalty $+\mathrm{IC} \times$ Writes per instruction $\times$ Write miss rate $\times$ Write miss penalty


#### Block Placement

* Direct Mapped: Block address MOD Numbers of blocks in cache
* Fully Associative
* Set Associative: Block address MOD Numbers of sets in cache
* Block Identification
  * Address = Block address + Block offset
  * Block address = tag + index
    * index: select the set
    * tag: check all blocks in the set
    * Fully Associative: no index field
  * Block offset: the address of the desired data/word within the block
* Block Replacement
  * Direct Mapped: only one block
  * Set / Fully Associative:
    * Random
    * LRU: use temporal locality
    * FIFO
* Write Strategy
  * Write hit
    * Write-through
    * Write-back
  * Write miss
    * Write allocate
    * No-write allocate

#### Mem Access Time

* Average memory access time = Hit time + Miss rate $\times$ Miss penalty
  * Miss rate = $\frac{\frac{\text { Misses }}{1000 \text { Instructions }} / 1000}{\frac{\text { Memory accesses }}{\text { Instruction }}}$
  * Split instruction and data cache:
    * Average memory access time = %instructions$\times$(Hit time + Instruction miss rate $\times$ Miss penalty) + %data$\times$(Hit time + Data miss rate $\times$ Miss penalty) 
      * %instructions = 1 / (Memory access/instruction)
* Processor Performance
  * CPU time = (CPU execution clock cycles + Memory stall clock cycles)$\times$Clock cycle time

#### Cache optimization (6 basic)

* Root causes of miss rates
  * Compulsory: cold-start/first-reference misses
  * Capacity: cache size limit
  * Conflict: collision misses: associativity

1. Larger Block Size
   * Reduce compulsory misses (spatial locality)
   * Increase conflict/capacity misses (Fewer block in the cache)
   
2. Larger Cache
   * Reduce capacity misses
   * Increase hit time, cost, and (static & dynamic) power
   
3. Higher Associativity
   * Reduce conflict misses
   * Increase hit time and power
   * higher associativity -> higher clock cycle time
   
4. Multilevel Cache
   * Reduce miss penalty
   * Reduce power
   * Average memory access time = Hit time$_\text{L1}$ + Miss rate$_\text{L1}$$\times$(Hit time$_\text{L2}$+Miss rate$_\text{L2}\times$Miss penalty$_\text{L2}$​)
   * Average mem stalls per instruction = Misses per instruction $_{\mathrm{L} 1} \times$ Hit time $_{\mathrm{L} 2}$ + Misses per instr$_\text{L2}\times$ Miss penalty $_\text{L2}$
   * Local miss rate VS Global miss rate
     * L1: Miss rate$_\text{L1}$
     * L2: Miss rate$_\text{L2}\times$Miss rate$_\text{L1}$
   
5. Prioritize read misses over writes
   
   * Reduce miss penalty
   * Introduce write buffer
   
6. Avoid address translation during indexing cache
   
   * reduce hit time
   * use page offset to index cache
   
   * Virtually indexed, physically tagged 
     * page offset to index the cache
     * physical address for tag match
   * For direct-mapped cache, it cannot be bigger than the page size



