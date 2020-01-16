### Fundamentals of Computer Design - Basics

#### 5 Classes of Computers

* PMD: Personal Mobile Device
* Desktop
* Server
* Cluster/WSC (warehouse-scale computer)
* Embedded computer

#### Parallelism

* Application Parallelism
  * DLP: Data-Level Parallelism
  * TLP: Task-Level Parallelism
* Hardware Parallelism
  * ILP: Instruction-Level Parallelism
    * pipelining
  * Vector Architectures and GPUs
  * TLP: Thread-Level Parallelism
  * RLP: Request-Level Parallelism

#### Classes of Parallel Arch

**S**ingle/**M**ultiple **I**nstruction/**D**ata stream

* SISD
  * ILP
* SIMD
  * DLP
* MISD
  * Not used
* MIMD
  * T(ask)LP

#### Instruction Set Architecture (ISA)

* register-memory ISA
* load-store ISA
* Memory Addressing
  * Byte addressing
  * Aligned address
* Addressing Modes
  * Register, Immediate, Displacement
* Operations
  * Four general categories
    * Data transfer: `LW, SW, ...`
    * Arithmetic Logical: `ADD, AND, SLT, ...`
    * Control: `BEQ, J, ...`
    * Floating point
* Control Flow Instructions
  * conditional branches
  * unconditional jumps
  * procedure calls
  * returns
* Encoding an ISA
  * Fixed length: ARM, MIPS – 32 bits
  * Variable length: 80x86 – 1~18 bytes

#### Computer Architecture

* ISA
* Organization
* Hardware