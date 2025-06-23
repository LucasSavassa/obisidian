 # summary
a bit is a digit the can assume two values, 1 and 0.

it's possible to represent anything with infinite bits
any number, any object ...

it is possible to represent any operation with infinite bits
addition, multiplication, boolean operation ...

the number of different things that can be represented with **n** bits is:
![[binary]]
since the first value is 0, the maximum number is 2^n - 1

# from binary to decimal
![[attachments/binary arithmetic]]
# from decimal to binary
![[from decimal to binary]]
# addition
## half adder
![[half adder.png]]
## full adder
![[full adder.png]]
# negative numbers
negative numbers can be in many ways
the most intuitive one is not so good
## sign bit: most intuitive one
simply use one bit to represent negative numbers
![[negative numbers with sign bit.png]]
## two complement: most correct one
negative numbers are represented as 2^n - x
![[negative numbers with two complement.png]]
### representing -X using two complement
![[two complement]]
