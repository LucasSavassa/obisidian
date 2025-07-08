the father of modern computer architecture, the [[von neumann architecture]] implements the [universal turing machine](https://en.wikipedia.org/wiki/Universal_Turing_machine)

1. transistors are arrenged to **true** and **false** data ( *operands* )
2. transistors are arrenged to build logic gates ( *operators* )
3. logic gates are arrenged to build complex operators ( add 16 bits, register 16 bits etc. )
4. registers are arrenged to build the memory ( *von neumann architecture* )
5. complex operators are arrenged to build the arithmetic logic unit ( *von neumann architecture* )
6. complex operators are arrenged to build the control unit ( *von neumann architecture* )
7. the arithmetic logic unit and the control unit are used to build the central processing unit
8. an [instruction set architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture) is defined to operate the computer
9. the central processing unit is designed to implement the [instruction set architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture)
10. an assembly language is defined to facilitate human programming tasks
11. an assembler compiles assembly language to binary programs

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