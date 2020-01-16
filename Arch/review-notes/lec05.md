### Pipelining: Basics & Hazards

#### Balanced Pipeline

* Equal-length pipe stages
  * Performance
    * Time per instruction by pipeline = Time per instruction by unpipelined / Number of stages
    * Speedup = Number of stages

#### Pipelining Terminology

* Latency: the time for an instruction to complete.
* Throughput of a CPU: the number of instructions completed per second.
* Clock cycle: time duration of one lockstep 
  * everything in CPU moves in lockstep;
* Processor Cycle: time required between moving an instruction one step down the pipeline;
  	= time required to complete a pipe stage;
  	= max(times for completing all stages);
  	= one or two clock cycles, but rarely more.
* CPI: clock cycles per instruction

#### RISC’s 5-Stage Pipeline

at most 5 clock cycles per instruction
IF ID EX MEM WB

* **I**nstruction **F**etch cycle
  * send PC to memory and fetch the current instruction
  * PC = PC + 4
* **I**nstruction **D**ecode/register fetch cycle
  * decode the instruction
  * read the registers (corresponding to register source specifiers)
* **Ex**ecution/effective address cycle
  * ALU operates on the operands from ID
  * Memory reference instruction: Add base register and offset
  * Register-Register ALU instruction: performs the operation specified by opcode 
  * Register-Immediate ALU instruction: ALU operates on the first value read from the register file and the sign-extended immediate
* **Mem**ory access
  * load
  * store
* **W**rite-**B**ack cycle
  * Register-Register ALU or load instruction: write the result into the register file
* Memory
  * separate instruction and data mems to eliminate conflicts 
* Register
  * in one clock cycle, write before read
* Pipeline Register
  * pipeline registers store the results of a stage and use them as the input of the next stage

#### Pipeline Hazards

* Structural hazard
  * Solution: Stall Instruction
* Data Hazard
  * Root cause: data dependency
  * Solution: Forwarding
  * Solution: Generalized Forwarding
  * Solution: Stall Instruction
* Control Hazard 
  * Branch hazard
    * Redo IF
    * Freeze or flush the pipeline
    * Predicted-untaken
      * when the branch is untaken, pipelining as if no hazard
      * if the branch is taken, restart the IF at the branch target 
    * Predicted-taken
    * Delayed branch

