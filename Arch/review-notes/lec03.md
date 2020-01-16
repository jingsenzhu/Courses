### Fundamentals of Computer Design - Trends and Performance

#### Trends

* Trends in Technology

  * Integrated circuit logic technology
    * Moore's Law
  * Semiconductor DRAM
  * Semiconductor flash
    * EEPROM: Electronically erasable programmable read-only memory
  * Magnetic disk technology
  * Network technology

* Performance Trends

  * Bandwidth/Throughput: the total amount of work done in a given time
  * Latency/Response Time: the time between the start and the completion of an event

* Power and energy

  * Dynamic Energy: switch transistors 
    * $\text{Energy}_{\text{dynamic}} \propto \text{Capacitive load}\times\text{Voltage}^2$ (energize pulse of the logic transition: 0->1->0 or 1->0->1)
    * $\text{Energy}_{\text{dynamic}} \propto 1/2\times\text{Capacitive load}\times\text{Voltage}^2$ (The energy of a single transition 0->1 or 1->0)
  * Power: $\text{Power}_{\text{dynamic}} \propto 1/2\times\text{Capacitive load}\times\text{Voltage}^2\times\text{Frequency switched}$
    * Slowing clock rate: reduce power but not energy
  * Improve efficiency
    * DVFS: dynamic voltage-frequency scaling
    * design for typical case  (PMD, laptop)
    * overclocking – *Turbo mode*

* Cost

* Dependability

  * Measures
    * Module reliability
      * MTTF (mean time to failure), MTTR(epair), MTBF = MTTF + MTTR
    * Module availability = MTTF / (MTTF + MTTR)

* Measuring Performance

  * X is n times faster than Y, if $\frac{\text{Execution time}_Y}{\text{Execution time}_X}=n$
    * $n=\frac{\text{Execution time}_Y}{\text{Execution time}_X}=\frac{\text{Performance}_X}{\text{Performance}_Y}$

* Quantitative Principles

  * Parallelism

  * Locality

    * temporal locality: recently accessed items
    * spatial locality: items whose address are near one another

  * **Amdahl’s Law**

    * Speedup $=\frac{\text { Performance for entire task using the enhancement when possible }}{\text { Performance ior entire task, without using the enhancement }}$

    * Speedup $= \frac{\text { Execution time for entire task without using the enhancement }}{\text { Execution time for entire task using the enhancement when possible }}$

    * $$
      \text{Execution time} _{\mathrm{new}}= \text{Execution time}_{\mathrm{old}} \times\left(\left(1-\text { Fraction }_{\text {enhanced }}\right)+\frac{\text { Fraction }_{\text {enhanced }}}{\text { Speedup }_{\text {enhanced }}}\right)
      $$

    * $$
      \text { Speedup}_\text{overall } =\frac{\text { Execution time }_\text{old}}{\text { Execution time }_\text{new}}=\frac{1}{(1-\text { Fraction }_\text{enhanced})+\frac{\text { Fraction }_{\text{enhanced}}}{\text { Speedup }_\text{enhanced}}}
      $$

  * CPU Time for program

    * CPU time = Clock cycles for a program $\times$ clock cycle time = Clock cycles for a program / Clock rate
    * CPI (Clock Cycles per Instruction) = Clock cycles for a program / Clock rate
      * Clock cycles = IC $\times$ CPI
      * CPU Time = IC $\times$ CPI $\times$ Clock cycle time
    * Multiple instructions
      * $\text { CPU time }=\left(\sum_{i=1}^{n} \mathrm{IC}_{i} \times \mathrm{CPI}_{i}\right) \times \text { Clock cycle time }$
      * $\mathrm{CPI}=\frac{\sum_{i=1}^{n} \mathrm{IC}_{i} \times \mathrm{CPI}_{i}}{\text { Instruction count }}=\sum_{i=1}^{n} \frac{\mathrm{IC}_{i}}{\text { Instruction count }} \times \mathrm{CPI}_{i}$

  

