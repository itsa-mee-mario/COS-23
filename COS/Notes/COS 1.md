
## Topic: Number Systems
>[!aside] 
> Status: #done
> Date: 2023-10-13

### Summary: Converting between different number representations

- - -
# Notes

# Base Conversion
![[Pasted image 20231013181053.png]]

# Complements
### Radix Complement

the **method of complements** is a technique to encode a symmetric range of positive and negative integers. Used to add and subtract these integers.

The $r$‘s complement of $N$ is given by $r^{n}- N$, where $N$ is a number in base $r$ (eg. 2’s complement of a binary number, 7’s complement of an octal number)

- https://www2.cs.uh.edu/~jhuang/JCH/LD/complements.pdf
### Diminished Radix Complement 

![[Pasted image 20231013182932.png]]

![[Pasted image 20231013183136.png]]

>[!note] 
>Negative Numbers are represented in base $r$ as their complements


# Subtraction
## Subtraction with Radix complement

Given two positive numbers $M$ and $N$, in base $r$, having integral part of $n$ digits:
1. Add $M$ to the ($r$‘s complement of $N$) [[#Radix Complement]]
2. End-carry condition:
	1. If end carry exists, discard it
	2. Else, take the $r$‘s complement of the result and place a negative sign 
## Subtraction with Diminished Radix Complement

1. add $M$ to the $(r-1)$‘s complement of $N$ 
2. Inspect end-carry:
	1. If end carry occurs, discard it (remove $r^{n}$) and add an end-around carry ($r^{-m}$)
	2. if does not occur, take $r-1$‘s complement of the result and place in a negative sign



# Integer Representation
## 2’s Complement Representation
#### Convert Decimal to Two's Complement

1. Convert the number to binary (ignore the sign for now) e.g. 5 is 0101 and -5 is 0101
2. If the number is a positive number then you are done. e.g. 5 is 0101 in binary using two's complement notation.
3. If the number is negative then
	1. find the complement (invert 0's and 1's) e.g. -5 is 0101 so finding the complement is 1010
	2. Add 1 to the complement 1010 + 1 = 1011. Therefore, -5 in two's complement is 1011.

```
 2  =  0010
 -3 =  1101 +
 -------------
 -1 =  1111
```

1. To convert a positive number to its negative in 1’s/2’s complement, invert
all the bits including the sign bit (and add 1 in 2’s complement).

2. Include the sign bit in all arithmetic operations in 1’s/2’s complement.
#### Converting Two's Complement to Decimal

Converting 1111 to decimal:
1. The number starts with 1, so it's negative, so we find the complement of 1111, which is 0000.
2. Add 1 to 0000, and we obtain 0001.
3. Convert 0001 to decimal, which is 1.
4. Apply the sign = -1.

