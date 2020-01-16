### Memory Hierarchy Design

#### Ten Advanced Cache Optimizations

1. Small and Simple First-Level Caches
   * Small size: support fast clock cycle and reduce power
   * Lower associativity: reduce hit time and power
2. Way Prediction
3. Pipelined Cache Access
   * Increase cache bandwidth
   * Higher latency
4. Nonblocking/lockup-free Caches
   * Increase cache bandwidth
   * leverage out-of-order execution 
5. Multibanked Caches
   * Increase cache bandwidth
   * support simultaneous accesses
   * Sequential interleaving
6. Critical Word First & Early Restart
   * Critical Word First
   * Early Restart
7. Merging Write Buffer
   * Reduce miss penalty
8. Compiler Optimizations
   * loop interchange
   * Blocking
9. Hardware Prefetching
   * Instruction prefetch: fetch two blocks on a miss
10. Compiler Prefetching
    * Reduce miss penalty/rate

* Reduce hit time
  * small and simple first-level caches;
  * way prediction;
  * decrease power;
* Increase cache bandwidth
  * pipelined/multibanked/nonblocking cache;
* Reduce miss penalty
  * critical word first;
  * merging write buffers;
* Reduce miss rate
  * compiler optimizations; decrease power;
* Reduce miss penalty or miss rate via parallelism
  * hardware/compiler prefetching; increase power;

#### Main Memory

* Measures
  * Latency
    * access time: the time between when a read is requested and when the desired word arrives
    * cycle time: the minimum time between unrelated requests to memory
  * Bandwidth
* SRAM (Static Random Access Memory)
  * 6 transistors per bit
  * Don’t need to refresh, so access time is very close to cycle time
* DRAM (Dynamic Random Access Memory)
  * Single transistor per bit
  * Reading destroys the information
  * Refresh periodically 
  * cycle time > access time
* DRAM Organization
  * in banks, each bank consists of rows, each row consists of columns
  * row buffer
* DRAM Improvement
  * Timing signals: repeated access to row buffer
  * Leverage spatial locality: array to buffer 1024-4096 bits
  * Clock signal
  * SDRAM: synchronous DRAM
  * Wider DRAM
  * DDR: double data rate
    * transfer data on both the rising edge and falling edge of the DRAM clock signal
  * Multiple Banks
  * Reducing power consumption in SDRAMs
    * dynamic power
* Flash Memory
  * type of EEPROM (electronically erasable programmable read-only memory)
  * hold contents w/o power
  * Difference from DRAM
    * erased before overwritten
    * static and less power
    * limited number of write
    * cheaper, slower than SDRAM; more expensive, faster than disk
* Memory Dependability 
  * Soft error: changes to a cell’s contents, not a change in the circuitry
  * Hard error: change in circuitry and are repeatable
* (Dynamic) error detection
  * Parity only
  * ECC (error correcting codes) only
  * Chipkill
* Virtual Memory
  * 4 tasks
    * 2 modes: user process; kernel/supervisor process
    * processor state user process can use but not write 
    * system call
    * limit memory accesses to protect memory state of a process
* Virtual Machines

