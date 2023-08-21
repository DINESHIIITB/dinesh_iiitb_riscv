

[week 0](#week_0)

[Day 1](#day-1)

[Day 2](#day-2)

# week_0

## Day 1

<details>
 <summary> Introduced to RISC-V </summary>

Reduced Instruction Set Computer (RISC)

RISC-V is an open-source instruction set architecture (ISA).An instruction set architecture defines the set of instructions a processor can execute. RISC-V offers multiple base instruction sets (RV32I, RV64I, etc.) and optional standard extensions (e.g., M for integer multiplication/division, F for single-precision floating-point, D for double-precision floating-point, and more). This modularity allows designers to tailor the architecture to their specific needs.




1. Compilation:
Use a C compiler (e.g., GCC, Clang) to compile the C source code into assembly code. The compiler translates the high-level C code into low-level assembly code that the hardware can understand.

2. Assembly:
Assemble the generated assembly code using an assembler (e.g., GNU Assembler - GAS). The assembler converts the assembly code into machine code, which consists of binary instructions that the hardware can directly execute. The type of instructions depend on what type of hardware it is, if it is risc v then the instructions are also risc v. 

3. Loading:
Load the generated executable binary onto the target hardware. This can involve transferring the binary to a microcontroller, FPGA, or other hardware platform via appropriate interfaces (e.g., JTAG, USB, SD card).

4. Execution on Hardware:
Run the program on the target hardware. The hardware's CPU fetches and executes the machine code instructions, carrying out the logic specified in the C source code.


 <img src="https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/32af6aef-86ab-477d-8311-ab75c07f1edf" alt="Image" width="800" height="600">

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/0cd016a5-194b-416d-b7af-413719f8308a)


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/08a57f36-4213-49d9-b460-16ebf3c73dea)

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/221a2940-d404-40f0-8115-72e7117bab7a)


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/3808de68-89e8-4d9d-bceb-d3ea9e2a637b)

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/e2daaf2f-d3e1-4f71-8e23-c2575ed7bf27)

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/782461c7-51df-4614-8058-3a7dcc89dd54)





</details>	

<details>
 <summary> Labwork for RISC-V software toolchain </summary>

### C program to computer sum from 1 to n

the leafpad will create .c file  weher we need to write and execute the program
```
leafpad sum1ton.c
gcc sum1ton.c
ls -ltr
./a.out
```


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/03a045ae-ed9f-4578-bc07-bede663b6203)

 


### RISC GCC compile and disammble

1. riscv64-unknown-elf-gcc: This is the RISC-V GCC compiler executable used for compiling C code targeting the RISC-V architecture.
2. -O1: This option specifies the optimization level to be used during compilation. In this case, -O1 indicates a moderate level of optimization.

3. -mabi=lp64: This option specifies the ABI (Application Binary Interface) to use. The lp64 ABI indicates that integers (int type) are 32 bits and pointers are 64 bits.

4. -march=rv64i: This option specifies the target RISC-V architecture and extension. In this case, rv64i indicates a 64-bit base integer (I) instruction set architecture without any additional extensions.

5. -o sum1ton.o: This option specifies the name of the output object file that will be generated after compilation. In this case, the output object file will be named sum1ton.o.

6. sum1ton.c: This is the source C file that you want to compile, named sum1ton.c.

7. -d : This is an option or flag passed to the objdump tool. The -d flag tells objdump to disassemble the contents of the object file, which means it will display the assembly code generated from the binary instructions in the object file.
8. |: This is a pipe operator, which is used to pass the output of one command as the input to another command.
9. less: This is a terminal pager program that allows you to view the contents of a file one screen at a time. It's often used to read and scroll through large text outputs.
10. -Ofast: This is an optimization flag. -Ofast is a high-level optimization level that enables aggressive optimization, potentially sacrificing some level of standard compliance for performance. It's suitable for code where performance is critical.
11. press q to exit form less program

   the assembly codefor main  has 11 intructions which starts from 10184 to 101ac, increments by 4 bytes for each instruction.
 ```
 riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
ls -ltr sum1ton.o
riscv64-unknown-elf-objdump -d sum1ton.o
riscv64-unknown-elf-objdump -d sum1ton.o | less
riscv64-unknown-elf-gcc -ofast -mabi=lp64 -march=rv64i -o sum1ton.o  sum1ton.c

```

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6ba38814-b5bf-4ef4-be62-52112c2a5bf2)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/231be7d9-32e4-4b40-85d4-5f1913260cea)

By searching /main in the command we will get this assembly code

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6cfdecc1-3ece-42ae-9a86-df45adbd0f71)

We got the optimized assembly code by using -Ofast

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/39e57177-5a2e-46cd-953b-a6fa001d5420)


### Spike simulation and Debug

Using the spike command we can execute and debug

-d : used to debug the main line by line

```
spike pk sum1ton.o
spike -d pk sum1ton.o
```

Load upper immediate: This instruction loads the immediate value  into register . The lui (Load Upper Immediate) instruction sets the upper 20 bits of one register to other register. This is often used to set up memory addresses or constants.

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/de602847-0c85-4661-aef4-eda61a52f00c)

addi sp, sp, -16: This instruction subtracts 16 from the value in the stack pointer sp. It allocates space on the stack for local variables or temporary storage.

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/92575dd5-13c0-4683-bbcc-73eadca3fd2d)

### Debugging sum1ton using spike

(spike) until pc 0 100b0

bbl loader

(spike) reg 0 a0

0x0000000000000001

(spike) 
core   0: 0x00000000000100b0 (0x00021537) lui     a0, 0x21

(spike) reg 0 a0
0x0000000000021000

(spike) reg 0 sp
0x0000003ffffffb50

(spike)         
core   0: 0x00000000000100b4 (0xff010113) addi    sp, sp, -16

(spike) reg 0 sp
0x0000003ffffffb40

(spike) reg 0 a0
0x0000000000021000

(spike) 
core   0: 0x00000000000100b8 (0x00f00613) li      a2, 15

(spike) reg 0 a2
0x000000000000000f

(spike) 
core   0: 0x00000000000100bc (0x00500593) li      a1, 5

(spike) reg 0 a1
0x0000000000000005

(spike) 
core   0: 0x00000000000100c0 (0x18050513) addi    a0, a0, 384

(spike) reg 0 a1
0x0000000000000005

(spike) 
core   0: 0x00000000000100c4 (0x00113423) sd      ra, 8(sp)

(spike) reg 0 a0 
0x0000000000021180

(spike) until pc 0 100cc    
sum of number from 1 to 5 is 15

(spike) 
core   0: 0x00000000000100cc (0x00813083) ld      ra, 8(sp)

(spike) reg 0 ra            
0x0000000000010138

(spike) 
core   0: 0x00000000000100d0 (0x00000513) li      a0, 0

(spike) reg 0 a0
0x0000000000000000

(spike) 
core   0: 0x00000000000100d4 (0x01010113) addi    sp, sp, 16

(spike) reg 0 sp
0x0000003ffffffb50

(spike) 
core   0: 0x00000000000100d8 (0x00008067) ret
(spike) 



![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/be98da42-8bbd-4b22-90bf-02a09d8af104)


###64 bit unsigned integers


RISC V double word can represent  is 0 to ((2^n)-1) unsigned numbers

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/c9f6176a-9ee9-49f1-9420-ced0e99f407c)


### 64 bit signed integers

By using 2`s compliment we can represent negative numbers

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/42b09686-1a05-423d-adeb-bc468f90acf4)

* for positive numbers MSB is 0
* for nagative numbers MSB is 1
* RISC V double word can represent  is 0 to ((2^n-1)-1) for positive and -1 to -2^(n-1).

*The instructions operate on singed and unsigned are called as Base integer instructions RV64I

### Lab for Unsigned integers

* The max value of 64 bit unsigned integer is (2^64) -1. So we are checking whether we will get the same value or not if we increase the bit size.
   
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/1bfa0c7f-9ae4-4c8b-9bef-529add8362ac)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/621d9104-0479-45ab-9a89-b2b90a12df35)

RISC V is 64 bit instruction so for both the codes we got the same value

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/00c0fad0-e02b-4b3b-9a1a-bd7776fbc9a5)

And we are decreasing the value of n , we may get the output or not ,it depends on the whether th evalue is in the rangeof  long long

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/e882b0b3-acfa-4bfd-a2d2-405cc985ae58)


![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6252c1cc-43d1-4884-a70d-4c7fb41a2d45)

Checking whether we will get negative valuefor unsigned integers or not.
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/db734e15-14fc-4965-b26f-2df75887fcc0)

Asexpected unsigned integer starts from 0 and we got 0
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/27d54f19-ca18-4c21-bc91-bbaef1c67981)

The long number cant fit in  int so we need to use long long int like the previosu program

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/b31b4f9a-7fe3-4c64-a090-30f18bad9c63)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/0b961fb5-9017-436c-a4b6-08bf4106a1d6)
 
</details>	


## Day 2


<details>
 <summary> Application Binary Interface(ABI) </summary>

 ### Introduction

* Programs can access the register via system calls this interface is called as Application Binary interface. The RISC-V ABI, like other ABIs, specifies rules and conventions for how programs interact with the hardware and the operating system in the RISC-V architecture. 

 ![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/0e072588-3c65-42cf-8311-223005a2df1e)

### Memory allocation for double words

Limited Register Space: Processors have a limited number of registers available for data storage and manipulation. RISC-V, like many other architectures, typically provides a relatively small number of registers (e.g., 32 general-purpose registers). This limited register space is optimized for fast access and execution of instructions but is not sufficient to store all program data and instructions. Memory is used to store both program code (instructions) and data. Registers are used for storing frequently accessed data and intermediate results during program execution. However, there isn't enough space in registers to store the entire program, especially larger programs. Thats we are storing the data in memory 

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6414dc6e-96c2-4593-ab20-6e5c232a12ae)

1. add Instruction:

    * Mnemonic: add
    * Syntax: add rd, rs1, rs2
    * Operation: This instruction adds the values of registers rs1 and rs2 and stores the result in register rd.
```
add x3, x1, x2  # Adds the values in registers x1 and x2, stores the result in x3.
```
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/35ff4875-d3c7-4ebd-b8d5-1b4428bf457d)

2. ld (Load Doubleword) Instruction:

    * Mnemonic: ld
    * Syntax: ld rd, offset(rs1)
    * Operation: This instruction loads a 64-bit (doubleword) value from memory at the address calculated as the sum of the value in register rs1 and the signed 12-bit offset. It loads the value into register rd.
```
ld x7, -16(x8)  # Loads a 64-bit value from memory at the address x8 - 16 into x7.

```
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/a912c7cc-1dd1-41dd-8593-1e00c2f11d94)


3. sd (Store Doubleword) Instruction:

    * Mnemonic: sd
    * Syntax: sd rs2, offset(rs1)
    * Operation: This instruction stores the value in register rs2 into memory at the address calculated as the sum of the value in register rs1 and the signed 12-bit offset. It stores a 64-bit (doubleword) value into memory.
```
sd x5, 32(x6)  # Stores the value in x5 into memory at the address x6 + 32.
```

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/ebfe5706-dda4-4674-87b0-bf4a9923b0b7)


![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/8fd65c8b-4149-41bc-a16d-284784203792)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/083d481a-870a-4767-a5e2-ddbc9cb3dc95)

 
</details>	

<details>
 <summary> Labwork using ABI function calls </summary>

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/31b36470-b438-41dd-8b38-43503d013f8a)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6a66b373-be68-4c97-a210-36682bf20f0e)

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o 1to9_custom.o 1to9_custom.c load.S
spike pk 1to9_custom.o
riscv64-unknown-elf-objdump -d 1to9_custom.o |less
```

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/94d3e103-8858-4a3d-b0c1-48df22b45ca8)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/bdff07ca-e59b-4fb1-bca6-1ca6e3f02fe4)
 
</details>	

<details>
 <summary> Basic verification flow using verilog </summary>

vim rv32im.sh has set of commands that will convert into hexfile,iverilog -o testbench.vvp: This is the Icarus Verilog compiler, used to compile a Verilog testbench (testbench.v) along with the picorv32.v file. This step likely sets up a simulation environment for testing the RISC-V program.chmod -x testbench.vvp: Similar to before, this command removes execute permissions from the resulting Verilog simulation file (testbench.vvp).vvp -N testbench.vvp: This command runs the simulation using the compiled Verilog testbench, likely to test the RISC-V program's behavior.

```
vim rv32im.sh
chmod rv32im.sh
./rv32im.sh
```
 
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/cb8c075e-ded5-4398-b242-35d11ee11e1b)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/ce7bfd67-f640-4a0f-9cff-fdb2423bfef5)


 </details>	



## Day 3

<details>
 <summary> Combinational Logic in TL verilog using makerchip </summary>

Combinational logic refers to digital circuits or systems where the output is solely determined by the current combination of input values, without any regard for past input values or the passage of time. Combinational logic circuits perform fixed logic functions, and their behavior is described entirely by a truth table or Boolean equations

Transaction-Level Verilog (TL-Verilog) is a high-level hardware description language (HDL) extension that simplifies the process of designing digital systems, particularly for complex and high-level abstractions. It's an innovative approach to hardware description, designed to make digital design more accessible, efficient, and scalable. Here's a breakdown of the key features and concepts of TL-Verilog:

1. Abstraction Layers:
        TL-Verilog introduces three abstraction layers for describing digital systems: behavior, transaction, and cycle-accurate.
        The behavior layer allows designers to specify high-level operations without worrying about the implementation details.
        The transaction layer focuses on data transfers between blocks, making it easier to model communication between different components.
        The cycle-accurate layer provides precise timing control for low-level implementation details.
2. Synchronous and Asynchronous Blocks:
        TL-Verilog allows you to define both synchronous and asynchronous blocks within your design.
        Synchronous blocks operate on a clock signal and follow standard digital design principles.
        Asynchronous blocks can operate independently of the clock signal, making them suitable for modeling complex, concurrent behaviors.

3. Pipeline Stages:
        TL-Verilog introduces a pipeline abstraction for modeling pipelined systems easily.
        You can specify pipeline stages and the data flow between them, simplifying the design of processors and other pipelined structures.

4. Implicit and Explicit State Machines:
        TL-Verilog supports both implicit and explicit state machines.
        Implicit state machines are described naturally through high-level constructs, making them more readable and maintainable.
        Explicit state machines provide more control over the state transitions, which can be necessary for certain designs.

5. Interfaces:
        TL-Verilog uses interfaces to define the communication between blocks.
        Interfaces encapsulate signals and methods, promoting modularity and reusability.
        This is particularly helpful for modeling complex interconnects or standard interfaces like AXI or Wishbone.
        
6. No RTL Coding:
        TL-Verilog eliminates the need for low-level RTL coding (Register Transfer Level), such as declaring flip-flops or describing how data propagates through gates.This higher level of abstraction simplifies the design process and reduces the risk of coding errors.
   
8. Automatic Pipelining and Parallelism:
        TL-Verilog can automatically infer pipeline stages and parallelism in your design, optimizing performance while maintaining high-level readability.
   
10. Simulation and Synthesis:
        TL-Verilog code can be simulated and synthesized, making it suitable for both early-stage design exploration and final hardware implementation.


    

 ![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/3803cf2b-628b-4fa7-9f4f-db68f7f23b53)

 ![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/7c8fbd2e-b7e3-4058-a39e-be845e93a48e)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/da0cd7bc-40de-4fbc-9bf3-88039d9fdca0)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/a790a68b-63b7-415b-a2d3-9f506d8e8eab)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/7566dafd-b920-4a0b-ae70-2d2e71bef13f)

Makerchip is an integrated development environment (IDE) primarily designed for digital design and hardware description language (HDL) development. It's a web-based platform that allows users to create, simulate, and test digital circuits and systems using popular HDLs like Verilog and SystemVerilog. Here's an explanation of the key features and components of Makerchip:

1. Editor: Makerchip provides a code editor where you can write and edit your hardware description code. It supports common HDLs like Verilog, SystemVerilog, and Chisel.
2. Simulation: Makerchip includes a built-in simulator that lets you simulate and test your digital designs. You can create testbenches, set input values, and observe the behavior of your circuits in real-time.
3. Waveform Viewer: The IDE has a waveform viewer that allows you to visualize the waveforms generated during simulation. This is helpful for debugging and verifying the correctness of your designs.
4. Block Diagram Editor: Makerchip features a block diagram editor that enables you to create high-level block diagrams of your digital systems. You can connect different components and generate structural code automatically.
5. Code Generation: Makerchip can automatically generate Verilog/SystemVerilog code from your block diagram designs. This feature simplifies the process of converting your high-level designs into HDL code.
6. Collaboration: The IDE allows for collaboration by sharing projects and designs with others. You can work on projects with team members and share your work with the Makerchip community.
7. Tutorials and Examples: Makerchip provides a set of tutorials and examples to help users learn and get started with digital design and HDL programming. These resources are valuable for beginners.

* Execrsise 1 pythagorean theorem

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/e52a868e-1a1a-448a-8358-fa72aea1c1ae)

* Exercise 2 Inverter

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/620c7194-a320-4b83-a9f0-b9d512a6a9d3)

* Exercise 3 Logic gates

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/39103251-b832-48e6-9df7-ea1e8ec2e164)

* Exercise 4 Vectors

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/47d5be3c-520d-4c10-b9ea-6b3e8eaff9ad)

* Exercise 5 1 bit-Mux

  ![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/026e299b-9b5e-4620-8b6c-820623b5a882)

* Exercise 6 8bit-Mux

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/5f328b3f-4aab-4948-884c-283dee21d009)

* Exercise 7 calculator

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/cf360ee4-7cd9-442b-b6ee-64b02ad06562)

 </details>	

<details>
 <summary> Sequential Logic in TL verilog using makerchip </summary>

 
* Fibbonacci series

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/cf9f6ac4-3fbe-47c2-a4ab-f28d507e5248)


![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/be461001-bc30-45c1-94aa-bdf5e788380c)

 
* Counter

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/75f6e030-8e5d-42b5-ae44-aff1c5e65055)

* Calculator that remembers the last value

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/2fa420dc-6459-49d8-a002-a772db7af18e)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/2edd8f63-02e7-4b4c-a678-e7e42504f5be)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/fffed7a9-a0cf-46e9-8deb-eb0740a86678)

```
https://www.makerchip.com/sandbox/#
```

 </details>	


<details>
 <summary> pipeline </summary>

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/daea94a7-82fe-4215-a276-eca8753da9ac)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/9dfcaf37-cc61-4d89-9d8c-b7bf84db3a70)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/4b8a49b7-ff19-476f-9b13-3c4550c78136)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/68db83f2-8e55-4e1f-8a9f-326656b6f6cb)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/cdbf0c8c-56c6-4c59-8f86-b9d410bd7d0e)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/22228006-fddd-4972-be31-0550cdd200f2)

* error conitions with pipeline
  
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/69e6780c-7000-477c-a422-08433c35a4df)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/66c96c8b-57ac-443a-b91b-c45299193e66)

* Calculator using  pipelining
  
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/11353d1b-9047-445c-a0e5-4afacc9f5c44)

* Calculator using  pipelining and output is zero for one cycle and out for one cycle
  
![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/ddaeb6d7-f52a-478f-a88c-e0873400b660)

 
 </details>	


 <details>
 <summary> validity </summary>


 ![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/cd48a090-9ed7-4b5a-813b-926fbd3671ac)


![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/d2d30449-8e49-4c1b-bec8-eec3f46b50fd)

Definition of macro  m4_makerchip_module:

module top(input wire clk, input wire reset, input wire [31:0] cyc_cnt, output wire passed, output wire failed);

* 

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/a5904a8b-25a8-4172-adc9-522d78692a29)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/4d72ae67-c083-4aa4-bb8e-dfd57a35cfca)



  
 </details>	
