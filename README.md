# ⚡ IITSoC'23 Electrical Project

## Overview

This project consists of three main components:

1. **Datapath**
2. **Control Unit**
3. **Testbenches**

---

### 1. Datapath

The Datapath executes all the instructions in the instruction set. It is designed at the register-transfer level and includes the following components:

#### 1.1 Input Multiplexer

A 4-to-1 multiplexer selects one of four different inputs to be written into the accumulator:

1. **Immediate Value (`imm_dp`)**: Used for the LDI instruction.
2. **User Input (`input_dp`)**: Used for the IN instruction.
3. **Register File Content**: Used for the LDA instruction.
4. **ALU and Shifter Result**: Used by arithmetic and logical instructions.

#### 1.2 Conditional Flags

Two conditional flags, **zero** and **positive**, are set by comparators:

- **Zero Flag**: Set using an 8-input NOR gate.
- **Positive Flag**: Set by checking the most significant sign bit.

#### 1.3 Accumulator

The accumulator is an 8-bit wide register with `write` and `clear` control signals:

- **Write (`accwr_dp`)**: Writes values into the accumulator.
- **Clear (`rst_dp`)**: Clears the accumulator on reset.

The accumulator output is sent to three destinations:

1. **Output Buffer**: For the OUT instruction.
2. **ALU Operand (A)**: For arithmetic operations.
3. **Register File**: For the STA instruction.

---
