# dinesh_iiitb_riscv

[week 0](#week_0)

[Day 0](#day-0)

# week_0

## Day 0

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


![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6cfdecc1-3ece-42ae-9a86-df45adbd0f71)

Optimized assumbly code of using -Ofast

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/39e57177-5a2e-46cd-953b-a6fa001d5420)


### Spike simulation and Debug

Using the spike command we execute and debug

-d : used to debug the main line by line

```
spike pk sum1ton.o
spike -d pk sum1ton.o
```

Load upper immediate: This instruction loads the immediate value  into register . The lui (Load Upper Immediate) instruction sets the upper 20 bits of one register to other register. This is often used to set up memory addresses or constants.

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/de602847-0c85-4661-aef4-eda61a52f00c)

addi sp, sp, -16: This instruction subtracts 16 from the value in the stack pointer sp. It allocates space on the stack for local variables or temporary storage.

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/92575dd5-13c0-4683-bbcc-73eadca3fd2d)

Debugging sum1ton using spike

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










 
</details>	

