 the father of modern computer architecture, the [[von neumann architecture]] implements the [universal turing machine](https://en.wikipedia.org/wiki/Universal_Turing_machine)

1. transistors are arranged to **true** and **false** data ( *operands* )
2. transistors are arranged to build logic gates ( *operators* )
3. logic gates are arranged to build complex operators ( add 16 bits, register 16 bits etc. )
4. registers are arranged to build the memory ( *von neumann architecture* )
5. complex operators are arranged to build the arithmetic logic unit ( *von neumann architecture* )
6. complex operators are arranged to build the control unit ( *von neumann architecture* )
7. the arithmetic logic unit, the control unit and the memory are used to build the central processing unit
8. an [[instruction set architecture]] is defined to operate the computer
9. the central processing unit is designed to implement the [[instruction set architecture]]
10. an assembly language is defined to facilitate human programming tasks
11. an assembler translates programs written in assembly language to binary code as defined in the instruction set architecture

# cpu
![[from transistor to cpu]]
# isa

| **Mnemonic** | **Category** | **Description** | **Binary Opcode** | binary          | assembly    |
| ------------ | ------------ | --------------- | ----------------- | --------------- | ----------- |
| `ADD`        | math         | `R1 = R2 + R3`  | `00000`           | 00000 0001 0010 | `ADD R1 R2` |
| `SUB`        | math         | `R1 = R2 - R3`  | `00001`           | 00001 0001 0010 | `SUB R1 R2` |
| `AND`        | logic        | `R1 = R2 & R3`  | `00100`           | 00100 0001 0010 | `AND R1 R2` |
| `OR`         | logic        | `R1 = R2 \| R3` | `00101`           | 00101 0001 0010 | `OR R1 R2`  |
| `NOT`        | logic        | `R1 = ~R2`      | `00111`           | 00111 0001 0000 | `NOT R1`    |
| `LD`         | memory       | Load `R1`       | `01000`           | 01000 0001 0000 | `LOAD R1`   |
| `ST`         | memory       | Store `R1`      | `01001`           | 01001 0001 0000 | `STORE R1`  |
| `JMP`        | flow         | jump            | `01011`           | 01011 0001 0000 | `JUMP R1`   |
| `HLT`        | system       | turn off        | `11111`           | 00000 0000 0000 | `OFF`       |
# assembler
translates `ADD R1 R2` to `00000 0001 0010`
translates `assembly` to `binary`

# addressing mode
- to perform an operation, the cpu needs to know which and where the operands are.
- addressing mode refers to this, where the operands are
- there are four types:
	- **register**: `ADD R1 R2` *(add an register value to another register value)*
	- **direct**: `ADD R1 RAM[0]` *(increment register with memory address `RAM[0]` value)*
	- **indirect**: `ADD R1 RAM[R2]` *(increment register with memory address `RAM[R2]` value)*
	- **immediate**: `ADD R1 2` *(add value to register)*
# buses
![[Pasted image 20250731091742.png]]
- to execute an operation, the cpu needs two information: operands and operators
- to write and read from memory, the cpu needs three information: memory address, data, and read/write signal
- buses are used to connect the information in all components
- they are called buses because they deliver data to many hops