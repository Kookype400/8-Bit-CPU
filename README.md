# 8-Bit-CPU
Implementation of a very rudimentary 8 Bit CPU

# Description 

This is my design of an 8-Bit CPU capable of executing AND, OR, NOT, ADD (2s complement additon), LD (Load), ST (Store), and BR (Branch) instructions.
To implement this project, I started by first figuring out the width of my instructions. To do this, I had to figure out how many instructions I wanted,
how many registers I wanted, and what every bit in my instruction meant. After I had determined this, I mapped out the Registers, ALU, RAM, and Control Flow of my CPU. I then
created a proper FSM for my CPU, outlining state transitions and which signals are on in what state, which I implemented using a ROM. Finally, I verified the functionality of
my CPU using programs that tested every operation my CPU offered.

# ISA Documentation

## ADD

Opcode: 000 [4] [3:2] [1:0]


