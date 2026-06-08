# 8-Bit-CPU
Implementation of a very rudimentary 8 Bit CPU

# Description 

This is my design of an 8-Bit CPU capable of executing AND, OR, NOT, ADD (2s complement additon), LD (Load), ST (Store), and BR (Branch) instructions.
To implement this project, I started by first figuring out the width of my instructions. To do this, I had to figure out how many instructions I wanted,
how many registers I wanted, and what every bit in my instruction meant. After I had determined this, I mapped out the Registers, ALU, RAM, and Control Flow of my CPU. I
then created a proper FSM for my CPU, outlining state transitions and which signals are on in what state, which I implemented using a ROM. Finally, I verified the 
functionality of my CPU using programs that tested every operation my CPU offered.

# ISA Documentation

## ADD

Instruction: 000 [4] [3:2] [1:0]
- [3:2] refers to both the first source register and the destination register.
- If [4] = 1, [1:0] is a 2s complement offset added to the source register, else if [4] = 0, [1:0] is the 2nd source register
- For this instruction, [3:2] CANNOT be 00
- Ex: 00000101 -> R1 = R1 + R1, 00010101 -> R1 = R1 + 1

## NOT

Instruction: 001 X [3:2] XX
- [3:2] refers to both the source register and the destination register, bits whose value is marked with an X does not matter.
- For this instruction, [3:2] CANNOT be 00
- Ex: 00100110 -> R1 = R1'

## AND 

Instruction: 010 X [3:2] [1:0]
- [3:2] refers to both the source register and the destination register, [1:0] refers to the 2nd source register
- For this instruction, [3:2] CANNOT be 00
- Ex: 01010110 -> R1 = R1 & R2

## OR

Instruction: 011 X [3:2] [1:0]
- [3:2] refers to both the source register and the destination register, [1:0] refers to the 2nd source register
- For this instruction, [3:2] CANNOT be 00
- Ex: 01110110 -> R1 = R1 | R2

## LD

Instruction: 100 X [3:2] [1:0]
- [3:2] is the register you are loading into, while [1:0] is the register that contains the address you are loading from
- For this instruction, [3:2] CANNOT be 00
- Ex: 10010110 -> R1 = M[R2]

## ST

Instruction: 101 X [3:2] [1:0]
- [3:2] is the register whose contents you are loading into memory, [1:0] is the register that contains the address you are loading into
- Ex: 10101001 -> M[R1] = R2

## BR

Instruction: 110 [4][3][2] [1:0]
- [4]= n, [3] = z, [2] = p, [1:0] is the register that contains the address that you branch to if the branch condition is met
- Ex: 11000101 -> if last register operation was positive, PC = R1

# Regsiter Table

In my ISA documentation, I said that some bits map to some registers, below are the specific bits to use to access a specific register
|Register|Bits|
|--------|----|
|Zero Reg|00|
|R1|01|
|R2|10|
|R3|11|



