# sample README FILE.not completed Task3


# Task 3 – RISC-V Instruction Type and 32-bit Encoding

This task focuses on identifying and decoding 15 unique RISC-V instructions used in a compiled C program. The goal is to classify each instruction by type (R, I, S, B, U, J) and extract the 32-bit binary encoding using the instruction format specification.

---

## 📘 Instruction Type Reference

The six main instruction types in RISC-V are:

| Type | Format Fields                                  | Used For                        |
|------|------------------------------------------------|----------------------------------|
| R    | `opcode | rd | funct3 | rs1 | rs2 | funct7`    | Register-to-register operations |
| I    | `opcode | rd | funct3 | rs1 | imm[11:0]`       | Immediate, load, etc.           |
| S    | `opcode | imm[4:0] | funct3 | rs1 | rs2 | imm[11:5]` | Store instructions         |
| B    | `opcode | imm[11], imm[4:1], funct3, rs1, rs2, imm[10:5], imm[12]` | Branch |
| U    | `opcode | rd | imm[31:12]`                     | Upper immediate instructions     |
| J    | `opcode | rd | imm[20|10:1|11|19:12]`          | Jumps                            |

---

## 🔍 Sample Code Used

The program analyzed is `odd_no.c`, compiled with `riscv64-unknown-elf-gcc` using both `-O1` and `-Ofast`.

Disassembly obtained via:

```bash
riscv64-unknown-elf-objdump -d odd_no.o > objdump_output.txt
```

---

## 📄 15 Unique Instructions and Their 32-bit Encodings

| #  | Assembly Instruction | Instruction Type | 32-bit Hex | 32-bit Binary | Fields Decoded |
|----|----------------------|------------------|------------|----------------|----------------|
| 1  | `addi sp, sp, -32`   | I                | `0xfe010113` | `11111110000000010000000100010011` | opcode: 0010011, funct3: 000, ... |
| 2  | `sd ra, 24(sp)`      | S                | `0x00113c23` | `00000000000100010011110000100011` | opcode: 0100011, funct3: 011, ... |
| 3  | `sd s0, 16(sp)`      | S                | ...        | ...            | ...            |
| .. | ...                  | ...              | ...        | ...            | ...            |
| 15 | `ret`                | I (alias for `jalr`) | `0x00008067` | `00000000000000000000000001100111` | opcode: 1100111 |

> ⚠️ All values must be taken directly from your `odd_no.o` binary. Use your own instruction addresses and encodings. You may use an online RISC-V disassembler or decode manually using the ISA spec.

---

## 🖼️ (Optional) Screenshots

Include any reference images here if desired:

```
screenshots/objdump_extract.png
screenshots/encoding_notes.png
```

Example:
![Objdump Output](screenshots/objdump_extract.png)

---

## 📚 Observations

- Most of the load/store instructions fall into **S-type**
- Control flow instructions like `beq`, `bne` are **B-type**
- Arithmetic instructions like `addi`, `addiw`, `andi` are **I-type**
- Understanding how bits are split into fields helps in pipeline design and decoding logic

---

## ✅ Conclusion

This task helped deepen understanding of how RISC-V assembly instructions are encoded in 32-bit binary format and how instruction types impact control logic in a RISC-V processor.


