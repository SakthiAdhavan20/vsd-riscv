# Task 4 – Functional Simulation of RISC-V

By making use of **RISC-V Core: Verilog Netlist and Testbench**, perform an experiment of **Functional Simulation** and observe the waveforms.

**NOTE:** Since the designing of RISC-V Architecture and writing its testbench is **not** part of this Research Internship, we will use the Verilog Code and Testbench of RISC-V that has already been designed.  
The reference GitHub repository is: **iiitb_rv32i**

---

## Steps to perform functional simulation of RISC-V

1) **Create a new directory with your name**
```bash
mkdir <your_name>

    Create two files using the touch command

touch netlist.v netlist_tb.v

    Copy the code from the reference GitHub repo and paste it into your netlist.v and netlist_tb.v files.

    Run and simulate the Verilog code

iverilog -o netlist netlist.v netlist_tb.v
./netlist

    View the simulation waveform in GTKWave

gtkwave netlist.vcd

    GTKWave will open and display the waveform window.

Important note on encodings

All the instructions in the provided Verilog are hard-coded.
Hard-coded means that instead of following the standard RISC-V bit patterns, the designer directly assigned 32-bit values.
Therefore, the 32-bit instructions generated in Task-2 will not match these hard-coded words.
Instructions – Standard vs Hardcoded (used in this core)
Operation	Standard RISC-V ISA (ref)	Hardcoded ISA (used)
ADD r6, r1, r2	32'h00110333	32'h02208300
SUB r7, r1, r2	32'h402083b3	32'h02209380
AND r8, r1, r3	32'h0030f433	32'h0230a400
OR r9, r2, r5	32'h005164b3	32'h02513480
XOR r10, r1, r4	32'h0040c533	32'h0240c500
SLT r11, r2, r4	32'h0045a0b3	32'h02415580
ADDI r12, r4, 5	—	32'h00520600
SW r3, r1, 2	32'h0030a123	32'h00209181
LW r13, r1, 2	32'h0020a683	32'h00208681
BEQ r0, r0, 15	32'h00000f63	32'h00f00002
ADD r14, r2, r2	—	32'h00210700

    Below, each instruction is shown in the standard RISC-V field layout (opcode/rd/funct3/rs1/rs2/funct7) so the intent is clear, while the Machine Code line shows the hardcoded 32-bit word actually used in this core (from netlist_tb.v)

## RISC-V Instruction Breakdown (based on netlist_tb.v)

### 1. Instruction: add r6, r1, r2
**RISC-V Instruction 1**

- **Opcode:** 0110011  
- **rd (r6 = x6):** 00110  
- **funct3:** 000  
- **rs1 (r1 = x1):** 00001  
- **rs2 (r2 = x2):** 00010  
- **funct7:** 0000000  

**Machine Code:** `02208300`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0000000  | 00010  | 00001  | 000    | 00110  | 0110011 |

---

### 2. Instruction: sub r7, r1, r2
**RISC-V Instruction 2**

- **Opcode:** 0110011  
- **rd (r7 = x7):** 00111  
- **funct3:** 000  
- **rs1 (r1 = x1):** 00001  
- **rs2 (r2 = x2):** 00010  
- **funct7:** 0100000  

**Machine Code:** `02209380`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0100000  | 00010  | 00001  | 000    | 00111  | 0110011 |

---

### 3. Instruction: and r8, r1, r3
**RISC-V Instruction 3**

- **Opcode:** 0110011  
- **rd (r8 = x8):** 01000  
- **funct3:** 111  
- **rs1 (r1 = x1):** 00001  
- **rs2 (r3 = x3):** 00011  
- **funct7:** 0000000  

**Machine Code:** `0230a400`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0000000  | 00011  | 00001  | 111    | 01000  | 0110011 |

---

### 4. Instruction: or r9, r2, r5
**RISC-V Instruction 4**

- **Opcode:** 0110011  
- **rd (r9 = x9):** 01001  
- **funct3:** 110  
- **rs1 (r2 = x2):** 00010  
- **rs2 (r5 = x5):** 00101  
- **funct7:** 0000000  

**Machine Code:** `02513480`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0000000  | 00101  | 00010  | 110    | 01001  | 0110011 |

---

### 5. Instruction: xor r10, r1, r4
**RISC-V Instruction 5**

- **Opcode:** 0110011  
- **rd (r10 = x10):** 01010  
- **funct3:** 100  
- **rs1 (r1 = x1):** 00001  
- **rs2 (r4 = x4):** 00100  
- **funct7:** 0000000  

**Machine Code:** `0240c500`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0000000  | 00100  | 00001  | 100    | 01010  | 0110011 |

---

### 6. Instruction: slt r11, r2, r4
**RISC-V Instruction 6**

- **Opcode:** 0110011  
- **rd (r11 = x11):** 01011  
- **funct3:** 010  
- **rs1 (r2 = x2):** 00010  
- **rs2 (r4 = x4):** 00100  
- **funct7:** 0000000  

**Machine Code:** `02415580`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0000000  | 00100  | 00010  | 010    | 01011  | 0110011 |

---

### 7. Instruction: addi r12, r4, 5
**RISC-V Instruction 7**

- **Opcode:** 0010011  
- **rd (r12 = x12):** 01100  
- **funct3:** 000  
- **rs1 (r4 = x4):** 00100  
- **Immediate:** 000000000101  

**Machine Code:** `00520600`  
**Type:** I-type  

**Bitwise Layout:**
| Field   | imm[11:0]    | rs1    | funct3 | rd     | opcode  |
|---------|--------------|--------|--------|--------|---------|
| Binary  | 000000000101 | 00100  | 000    | 01100  | 0010011 |

---

### 8. Instruction: sw r3, r1, 2
**RISC-V Instruction 8**

- **Opcode:** 0100011  
- **funct3:** 010  
- **rs1 (r1 = x1):** 00001  
- **rs2 (r3 = x3):** 00011  
- **Immediate:** 000000000010  

**Machine Code:** `00209181`  
**Type:** S-type  

**Bitwise Layout:**
| Field   | imm[11:5] | rs2    | rs1    | funct3 | imm[4:0] | opcode  |
|---------|-----------|--------|--------|--------|----------|---------|
| Binary  | 0000000   | 00011  | 00001  | 010    | 00010    | 0100011 |

---

### 9. Instruction: lw r13, r1, 2
**RISC-V Instruction 9**

- **Opcode:** 0000011  
- **rd (r13 = x13):** 01101  
- **funct3:** 010  
- **rs1 (r1 = x1):** 00001  
- **Immediate:** 000000000010  

**Machine Code:** `00208681`  
**Type:** I-type  

**Bitwise Layout:**
| Field   | imm[11:0]    | rs1    | funct3 | rd     | opcode  |
|---------|--------------|--------|--------|--------|---------|
| Binary  | 000000000010 | 00001  | 010    | 01101  | 0000011 |

---

### 10. Instruction: beq r0, r0, 15
**RISC-V Instruction 10**

- **Opcode:** 1100011  
- **funct3:** 000  
- **rs1 (r0 = x0):** 00000  
- **rs2 (r0 = x0):** 00000  
- **Immediate:** 000000011110  

**Machine Code:** `00f00002`  
**Type:** B-type  

**Bitwise Layout:**
| Field   | imm[12|10:5] | rs2    | rs1    | funct3 | imm[4:1|11] | opcode  |
|---------|--------------|--------|--------|--------|-----------|---------|
| Binary  | 0 000000      | 00000  | 00000  | 000    | 1111 0    | 1100011 |

---

### 11. Instruction: add r14, r2, r2
**RISC-V Instruction 11**

- **Opcode:** 0110011  
- **rd (r14 = x14):** 01110  
- **funct3:** 000  
- **rs1 (r2 = x2):** 00010  
- **rs2 (r2 = x2):** 00010  
- **funct7:** 0000000  

**Machine Code:** `00210700`  
**Type:** R-type  

**Bitwise Layout:**
| Field   | funct7   | rs2    | rs1    | funct3 | rd     | opcode  |
|---------|----------|--------|--------|--------|--------|---------|
| Binary  | 0000000  | 00010  | 00010  | 000    | 01110  | 0110011 |

