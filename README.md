**VSD INTERNSHIP**

**TASK 1:-**

**Installation of RISC-V toolchain using VDI. Uploading the snapshot of compiled C code and RISC-V Objdmp.**

Installation:

A. Oracle Virtual machine.

B. Gedit editor.

**Flow**

1.) Open Gedit and write the C code to find the sum of n numbers.

2.) Compile the above code using gcc and get the output.

3.) Now, compile and run the same code using the RISC-V Simulator and search for main using the command: "riscv64-unknown-elf-objdump -d sum.o | less" and then type out "/main".

4.) Changing it from O1 to Ofast.

5.) Search for main usin the commands: "riscv64-unknown-elf-objdump -d sum.o | less" and then type out "/main".

**TASK 2:-**

**Performing SPIKE Simulation and Observation with -O1 anf -Ofast. Debugging a simple C code with Interactive Debugging Mode using Spike and Uploading snapshot of compiled C code, RISC-V Objdmp.**
**A. SPIKE Simulation and Observation with -O1 anf -Ofast. Upload snapshot of compiled C code, RISC-V Objdmp.**

**What is SPIKE in RISC-V?**

A RISC-V ISA is a simulator, enabling the testing and analysis of RISC-V programs without the need for actual hardware.

Spike is a free, open-source C++ simulator for the RISC-V ISA that models a RISC-V core and cache system. It can be used to run programs and a Linux kernel, and can be a starting point for running software on a RISC-V target.

**What is pk (Proxy Kernel)?**

The RISC-V Proxy Kernel, pk , is a lightweight application execution environment that can host statically-linked RISC-V ELF binaries.

A Proxy Kernel in the RISC-V ecosystem simplifies the interaction between complex hardware and the software running on it, making it easier to manage, test, and develop software and hardware projects.

**Flow:**

1.) The C Code to find the sum of n numbers is the same code as used in Task 1. Following the instructions as shown below in the snapshot, we can observe the same output when 'gcc' command or 'spike' command is used.

2.) Enter the below given instructions and debug using SPIKE:

riscv64-unknown-elf-objdump -d sum1ton.o | less ( here -d is given for Debug)
Screenshot 2024-10-29 133549

B. Write a simple C program for any simple application and compile with RISC-V GCC/SPIKE.

**TASK 3:-**

**RISC-V Instruction Types (R,I,S,B,U,J):**

**The RISC-V instruction set architecture (ISA) defines several types of instructions, each with a specific format. Below is a summary of the main instruction types:**

1.) R-Type (Register-Register):

Purpose: Used for operations that involve two source registers and one destination register.

Fields:

opcode: Operation code

rd: Destination register

func3: Function modifier

rs1: Source register 1

rs2: Source register 2

func7: Function modifier (additional)

Example: add x1, x2, x3

2.) I-Type (Immediate):

Purpose: Used for operations with one source register and an immediate value, including loads.

Fields:

opcode: Operation code

rd: Destination register

func3: Function modifier

rs1: Source register

imm[11:0]: Immediate value

Example: addi x1, x2, 10

3.) S-Type (Store):

Purpose: Used for store instructions, which write a register's value to memory.

Fields:

opcode: Operation code

imm[11:5]: Immediate value (upper 7 bits)

func3: Function modifier

rs1: Source register (base address)

rs2: Source register (data to store)

imm[4:0]: Immediate value (lower 5 bits)

Example: sw x2, 0(x1)

4.) B-Type (Branch):

Purpose: Used for conditional branch instructions.

Fields:

opcode: Operation code

imm[12]: Immediate value (bit 12)

imm[10:5]: Immediate value (bits 10 to 5)

func3: Function modifier

rs1: Source register 1

rs2: Source register 2

imm[4:1]: Immediate value (bits 4 to 1)

imm[11]: Immediate value (bit 11)

Example: beq x1, x2, label

5.) U-Type (Upper Immediate):

Purpose: Used for instructions that operate with a large immediate value.

Fields:

opcode: Operation code

rd: Destination register

imm[31:12]: Immediate value

Example: lui x1, 0x10000

6.) J-Type (Jump):

Purpose: Used for jump instructions with a large immediate value.

Fields:

opcode: Operation code

rd: Destination register

imm[20]: Immediate value (bit 20)

imm[10:1]: Immediate value (bits 10 to 1)

imm[11]: Immediate value (bit 11)

imm[19:12]: Immediate value (bits 19 to 12)

Example: jal x1, label

32-bit Instruction Codes in RISC-V Instruction Type Format for 15 Unique Instructions:
1.) addi x1, x2, 10

Instruction Format: I-type
Binary Encoding: 000000000010 00010 000 00001 0010011
32-bit Instruction Code: 0x00210093
2.) li x5, 0x0

Instruction Format: I-type (using addi x5, x0, 0x0) Binary Encoding: 000000000000 00000 000 00101 0010011 32-bit Instruction Code: 0x00000293

3.) lui x10, 0x20000

Instruction Format: U-type
Binary Encoding: 00100000000000000000 01010 0110111
32-bit Instruction Code: 0x20000537
4.) mv x1, x2

Instruction Format: I-type (using addi x1, x2, 0)
Binary Encoding: 000000000000 00010 000 00001 0010011
32-bit Instruction Code: 0x00010093
5.) sw x5, 0(x10)

Instruction Format: S-type
Binary Encoding: 0000000 00101 01010 010 00000 0100011
32-bit Instruction Code: 0x0050a023
6.) lw x5, 0(x10)

Instruction Format: I-type
Binary Encoding: 000000000000 01010 010 00101 0000011
32-bit Instruction Code: 0x0000a283
7.)jal x0, 0x100

Instruction Format: J-type
Binary Encoding: 00000000000100000000 00000 1101111
32-bit Instruction Code: 0x0000086f
8.) beq x1, x2, label

Instruction Format: B-type (assuming offset is 0x4)
Binary Encoding: 000000 00010 00001 000 00010 1100011
32-bit Instruction Code: 0x00210063
9.) bne x1, x3, label

Instruction Format: B-type (assuming offset is 0x4)
Binary Encoding: 000000 00011 00001 001 00010 1100011
32-bit Instruction Code: 0x00310063
10.) slli x5, x1, 1

Instruction Format: I-type
Binary Encoding: 0000000 00001 00101 001 00001 0010011
32-bit Instruction Code: 0x00109093
11.) srli x6, x2, 2

Instruction Format: I-type
Binary Encoding: 0000000 00010 00110 101 00010 0010011
32-bit Instruction Code: 0x0022b093
12.) and x3, x4, x5

Instruction Format: R-type
Binary Encoding: 0000000 00101 00100 111 00011 0110011
32-bit Instruction Code: 0x005201b3
13.) or x2, x3, x4

Instruction Format: R-type
Binary Encoding: 0000000 00100 00011 110 00010 0110011
32-bit Instruction Code: 0x004181b3
14.) sub x3, x5, x2

Instruction Format: R-type
Binary Encoding: 0100000 00010 00101 000 00011 0110011
32-bit Instruction Code: 0x402282b3
15.) xor x1, x2, x3

Instruction Format: R-type
Binary Encoding: 0000000 00011 00010 100 00001 0110011
32-bit Instruction Code: 0x003100b3

**TASK 4:-**

**By making use of RISC-V Core: Verilog Netlist and Testbench, perform an experiment of Functional Simulation and observe the waveforms**

**GTKWAVE Generation Process:**

Follow the guidelines given below to generate the waveform using Verilog code and GTKWAVE.

1.) Clone the Repository.
Clone the RISC-V Verilog repository using the 'git clone' command.

git clone https://github.com/vinayrayapati/rv321 link

2.) Navigate to the Cloned Directory.
Change the directory to the cloned repository.

cd rv321

3.) Compile the Verilog Code and Testbench.
Run the following iverilog command to compile the Verilog code and testbench.

'iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v'

4.) Simulate the Verilog Code.
After compiling, simulate the Verilog code by running the compiled file.

'./iiitb_rv321'

5.) Open the Waveform in GTKWAVE.
Once the simulation generates the .vcd (Value Change Dump) file, you can visualize the waveform in GTKWAVE.

'gtkwave iiitb_rv321.vcd'

It will open the new window of GTKWAVE.

Tap the 'iiitb_rv32i_tb' in the 'SST' section.

Now, drag the command in the same way presented under 'time' section.


Select the instructions from EX_MEM_IR[31:0] to present the instructions used in Task 3 and Analysing the Output Waveform of various instructions that we have covered in TASK-3.

Instruction 1 : ADD r1, r1, r2
values stored in two different registe

Instruction 2 : SUB r3, r1, r2
Values stored in two different register

Instruction 3 : AND r2, r1, r3
Untitled design

Instruction 4 : OR r8, r2, r5
Untitled design (1)

Instruction 5 : XOR r8, r1, r4
Your paragraph text

Instruction 6 : SLL r15, r11, r2
Your paragraph text (1)

Instruction 7 : SLT r10, r2, r4
32 bits instruction

To conclude : The output waveform for the list of instructions are obtained in GTKWAVE.

