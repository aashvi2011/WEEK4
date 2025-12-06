# WEEK4
WEEK 4 — RISC-V Notes
# 🔹 Introduction

RISC-V is the language of the computer, defining how hardware understands instructions.

Programs written in high-level languages are compiled into assembly, then converted into machine language (binary).

Machine instructions (bits) are what the computer actually executes at the hardware layout level.

# 🔹 Software-to-Hardware Flow
High-level Program (C/C++/Java)
        ↓
Compiler → Assembly Code
        ↓
Assembler → Machine Code (Binary)
        ↓
Hardware executes instructions

# 🔹 System Software

System software contains three main components:

Operating System

Compiler

Assembler

# OS Responsibilities:

Handles memory, I/O operations, allocation & deallocation.

Converts applications into assembly language, then binary for hardware execution.

Outputs small functions in C/C++/Java, which compiler converts into hardware-specific instructions.

Compiler:

Converts high-level programs (C/C++) into assembly instructions.

Assembler:

Converts assembly instructions into binary machine code.

Binary is fed to hardware — the hardware recognizes patterns and executes functions accordingly.

# 🔹 Instruction Set Architecture (ISA)

Defines how the programmer communicates with the computer.

C, C++, Java are abstract interfaces to the instruction set.

Common pseudo-instructions: mv, li, ret

Base integer instructions set: RV64I

Every CPU implementation must support RV64I

Multiply extension: RV64M (mulw, divw)

Floating-point extensions: RV64F / RV64D

Examples: flw, fadd.s, fmul.s

# 🔹 Registers & Data Representation
Type	Size
Doubleword	64-bit
Word	32-bit
1 Byte	8 bits

MSB = bit 63

LSB = bit 0

Pattern capacity:

64-bit → 2⁶⁴ ≈ 1.84 × 10¹⁹

32-bit → 2³² = 4,294,967,296

# 🔹 Negative Number Representation

Uses Two’s Complement

Invert bits

Add 1

⚠ Bug note:
Using int instead of long long int causes overflow for 64-bit values because int holds only 32 bits.

# 🔹 ABI, System Calls & Hardware Interface

ABI (Application Binary Interface) allows direct register and system call access.

RISC-V contains 32 registers (x0–x31).

Data is loaded either:

directly from a register

or from memory address

Example (loading into register)

ld x8, 16(x23)   # load doubleword at address x23+16 into x8


Storing back to memory

sd x8, 8(x23)


Registers are limited — hence storage back to memory is necessary.

# 🔹 Endianness

Little-endian (RISC-V default): MSB is stored at the higher address (on top)

Big-endian: LSB stored on top

# 🔹 Instruction Format Overview

All RISC-V instructions are 32 bits.

Fields include:

opcode — operation type

rs1 — source register

rs2 — source register (if needed)

rd — destination register

# Types of Instructions:

Type	Description
R-type	operates only on registers
I-type	register + immediate
S-type	store instructions

All registers use 5-bit addressing →
2⁵ = 32 registers → x0 to x31
