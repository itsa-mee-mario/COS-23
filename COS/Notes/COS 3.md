
## Topic:  MIPS Assembly
>[!aside] 
> Status: #in-progress
> Date: 2023-10-13

### Summary:

- - - 

# Registers
32 Special Registers, for fast location of data. data must be in registers to perform arithmetic, register $zero always equals 0, and register $at is reserved by the assembler to handle large constants.
![[Pasted image 20231017105404.png]]

# Memory Words
- Only accessed by data transfer instructions
- Byte addresses, sequential words differ by 4
`Memory[0] ... Memory[4294967292]`


# Arithmetic
1. Add(/Subtract) : Add the value in s3 and s2, store in s1
	```
	add $s1 $s2, $s3
	```

2. Add immediate: add 20 to s2, store in s1. used to add constants
	```
	addi $s1 $s2, 20
	```

# Data Transfer Instructions
### Common Syntax : ```
```
Command $s1, 20($s2)$
```
1. Load Word “lw” :
	1. Word from memory to register
	2. s1 ← Memory[s2 + 20]
2. Store Word “sw”
	1. Word from register to memory
	2. Memory[s2 + 20] ← s1
3. Load Half / Load Half Unsigned “lh(u)”:
	1. Halfword memory to register
4. Store Half “sh”
	1. Halfword register to memory
5. Load Byte / Load Byte Unsigned “lb(u)”
	1. Byte memory to register
6. Store Byte “sb”
	1. Byte register to memory
7. Load Linked word “ll”
	1. Load word as 1st half of atomic swap
8. Store Condition word “sc”
	1. Store word as 2nd half of atomic swap
	2. Memory[s2 + 20] ← s1 ; s1 = 0 or 1
	
==9. Load Upper Immediate “lui” // command `lui $s1, 20`
	1. Loads constant in upper 16 bits
	2. s1 ← 20 * 2^16== 





# Using Load and Save

```C
A[12] = h + A[8];
```

Can be represented in MIPS as

```MIPS
lw $t0, 32($s3);        # load A[8] into temporary register t0
add $t0, $s2, $t0       # t0 gets t0 + h (stored in s2)
sw $t0, 48($s3)         # store the value at t0 in A[12]
```

