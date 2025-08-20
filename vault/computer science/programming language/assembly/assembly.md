- assembly languages are a symbolic version of an ISA
- generally speaking, each ISA (x86, ARM, RISC-V) has an assembly language
- ISA defines the instructions in binary
- Assembly language defines a human-friendly syntax that is translated to the instructions defined by the ISA 
![[assembly 2025-08-18 08.23.06.excalidraw]]
# common features in assembly language
- parse commands to binary (assembly specification + ISA specification)
- predefined memory locations (e.g. **SCREEN** or **KEYBOARD**)
- variables (find and assign a random register to store values for a variable)
- got o labels (similar to methods)
# techniques
- one-pass assembler: loops through assembly code only once and translates lines to binary
- two-pass assembler: loops through assembly code twice, first to do preprocessing, then to translate symbols to binary