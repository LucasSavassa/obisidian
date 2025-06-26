boolean logic refers to a domain of symbols that help to express logical operations.
it uses variables that can assume two values: **1** or **0**.
there are three operators: **and**, **or**, **not**.
these operators can be combined to create new operators
# values
boolean logic uses two values
- 0
- 1
# operators
1 digit for 2 values can create 2 combinations:
 - 1
 - 0
2 digits for 2 values can create 4 combinations:
- 0 0
- 0 1
- 1 0
- 1 1
3 digits for 2 values can create 8 combinations:
- 0 0 0
- 0 0 1
- 0 1 0
- 0 1 1
- 1 0 0
- 1 0 1
- 1 1 0
- 1 1 1
**n** digits for 2 values can create $2^n$ combinations
## one digit operators
### .(a)
| a   | .   |
| :-- | --- |
| 0   | 0   |
| 1   | 1   |
### not(a)
| a   | not |
| :-- | --- |
| 0   | 1   |
| 1   | 0   |

## two digits operators
### and(a,b)

| a   | b   | and |
| :-- | --- | --- |
| 0   | 0   | 0   |
| 1   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 1   | 1   |
### or(a,b)

| x   | y   | or  |
| :-- | --- | --- |
| 0   | 0   | 0   |
| 1   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 1   | 1   |

# functions
f(a,b,c) = ( a **and** b ) **or** ( **not** ( c ) )

| a   | b   | c   | f   |
| :-- | :-- | :-- | :-- |
| 0   | 0   | 0   | 1   |
| 0   | 0   | 1   | 0   |
| 0   | 1   | 0   | 1   |
| 0   | 1   | 1   | 0   |
| 1   | 0   | 0   | 1   |
| 1   | 0   | 1   | 0   |
| 1   | 1   | 0   | 1   |
| 1   | 1   | 1   | 1   |

# identities
## commutative
a **and** b = b **and** a
a **or** b = b **or** a
## associtive
a **or** ( b **or** c ) = ( a **or** b ) **or** c
a **and** ( b **and** c ) = ( a **and** b ) **and** c
## distributive
a **or** ( b **and** c ) = ( a **or** b ) **and** ( a **or** c )
a **and** ( b **or** c ) = ( a **and** b ) **or** ( a **and** c )
# morgan laws
## not( a or b ) = not( a ) and not( b )


# how to convert the truth table to a boolean function
| a   | b   | c   | f   |
| :-- | :-- | --- | --- |
| 0   | 0   | 0   | 1   |
| 0   | 0   | 1   | 0   |
| 0   | 1   | 0   | 1   |
| 0   | 1   | 1   | 0   |
| 1   | 0   | 0   | 0   |
| 1   | 0   | 1   | 0   |
| 1   | 1   | 0   | 1   |
| 1   | 1   | 1   | 1   |
## step 1: write a function for each row equal to 1
|       | a     | b     | c     | f     |                                    |     |
| :---- | :---- | :---- | ----- | ----- | ---------------------------------- | --- |
| **>** | **0** | **0** | **0** | **1** | not( a ) and not( b ) and not( c ) |     |
|       | 0     | 0     | 1     | 0     |                                    |     |
| **>** | **0** | **1** | **0** | **1** | not( a ) and ( b ) and not( c )    |     |
|       | 0     | 1     | 1     | 0     |                                    |     |
|       | 1     | 0     | 0     | 0     |                                    |     |
|       | 1     | 0     | 1     | 0     |                                    |     |
| **>** | **1** | **1** | **0** | **1** | ( a ) and ( b ) and not( c )       |     |
| **>** | **1** | **1** | **1** | **1** | ( a ) and ( b ) and ( c )          |     |
## step 2: merge all functions with or
( not( a ) and not( b ) and not( c ) )
or ( not( a ) and ( b ) and not( c ) )
or ( ( a ) and ( b ) and not( c ) )
or ( ( a ) and ( b ) and ( c ) )
## step 3: simplify the expression using identities and morgan laws
