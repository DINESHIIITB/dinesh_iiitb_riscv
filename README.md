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
   
 ```
 riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
ls -ltr sum1ton.o
```

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6ba38814-b5bf-4ef4-be62-52112c2a5bf2)

![image](https://github.com/DINESHIIITB/dinesh_iiitb_riscv/assets/140998565/6cfdecc1-3ece-42ae-9a86-df45adbd0f71)



 
</details>	

