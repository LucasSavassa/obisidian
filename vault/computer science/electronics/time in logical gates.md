after input changes, it'll take some time for output to change
![[elapsed time from gate input to output.png]]

[[cmos]] can take from 100ps to 1ns
[[ttl]] can take from 5ns to 15ns

if logic gates and logic paths are connected directly, it's output become unpredictable in a given moment

to circumvent this issue, modern designs install [[register]] between each computational task. this is called a pipeline.

a clock ([[oscillator]]) changes time from continuous to discrete
 ![[time with oscillator]]
 each cicle of the oscillator is one unit of time

in synchronous digital design, this unit of time is divided in two

t1 - update
t2 - store

during t1 logic gates update their value
during t2 the new output is stored in a register
 ![[time in synchronous digital design example 1]]
in t1, write is turned off in registers
in t1, read is turned on in registers

in t1, components read input from register

in t2, read is turned off in registers
in t2, write is turned on in registers

in t2, components write output to register

all registers and memory units share the same clock

they obtain the clock value through the [[clock tree]]

components are implemented using asynchronous digital design (combinational logic)
computers are implemented using synchronous digital design (sequential logic)
 
