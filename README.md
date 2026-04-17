# Simple 16-bit Microprogrammed Processor (Logisim)

Implementation of a microprogrammed processor designed in Logisim as part of the *Fundamentals of Computer Engineering 2* course at the University of Belgrade, School of Electrical Engineering.

## Overview

The project implements a simple processor with:
- byte-addressable memory with capacity of 2<sup>16</sup> bytes
- one-address instruction format
- 16-bit signed/unsigned data
- little-endian memory layout (least significant byte at lower address)
- stack-based operations
- interrupt handling via interrupt vector table (IVT)

The processor consists of the following main components:
- **FETCH** - instruction fetch phase
- **ADDR** - operand address calculation and fetch
- **EXEC** - instruction execution
- **INTR** - interrupt handling
- **COMMON** - shared registers and logic

Control units (except COMMON) are implemented as **microprogrammed control units**, with control logic stored in ROM.

## Architecture

### Registers
- PC - Program Counter
- SP - Stack Pointer
- A - Accumulator
- PSW - Program Status Word
- IVTP - Interrupt Vector Table Pointer
- MAR - Memory Address Register
- MDR - Memory Data Register
- IR - Instruction Register
- 8 general-purpose registers

### Instruction Set
- zero-address instructions (HALT, PUSH, POP, RTI, etc.)
- conditional and unconditional jumps
- arithmetic and logical operations (ADD, XOR, TST)
- memory and register operations (LD, ST)
- subroutine calls (JSR)
- string processing (STRLEN)

### Addressing Modes
- immediate
- memory direct / indirect
- register direct / indirect
- pre-increment / post-decrement
- register indirect with offset

### Interrupts
- 8 interrupt lines (intr<sub>7..0</sub>), priority-based
- maskable via PSW
- handled through IVT
- context saving: PC, A, PSW

## Documentation

- **docs/UputstvoZaProjekat_2020_2021.pdf** - general project instructions
- **docs/ORT2_Projekat_Zadatak_209.pdf** - specific assignment specification
- **docs/FormularSimulator.doc** - template for execution flow diagrams
- **docs/Formular.pdf** - combined execution flow diagrams (FETCH, ADDR, EXEC, INTR)
- **microcode/Mikroprogram.xlsx** - microprogram and test programs

## Notes

- The processor is implemented and tested in **Logisim**.
- Memory initialization files:
  - RAM files contain test programs and data
  - ROM files contain microprogram control data for FETCH, ADDR, EXEC, and INTR units
- Project was developed as part of coursework and is not intended for production use.
