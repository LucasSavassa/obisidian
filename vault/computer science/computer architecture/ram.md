a ram is a collection of [[register]]
but no only a simple collection
an **addressable** collection of registers
![[ram diagram.png]]
> at any moment, only one register is selected

the address (k) width is related to the number of registers (n)
$$
k=\log_{2}n
$$
# cost of memory access
- accessing large memory repository is slow, but large memory repository is cheap
- accessing tiny memory repository is fast, but tiny memory repository is expensive
- solution is **memory hierarchy**
# memory hierarchy
- it's possible to combine tiny memory repositories (register) with large memory repository (ram and disk) to design a memory system that is both: **large and fast**
![[memory hierarchy]]
- the cpu chooses which memory layer to use for an operation based on [[computer architecture#addressing mode|addressing mode]]
- 