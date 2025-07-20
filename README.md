# VSDSquadron Research Internship 2025 – Sakthi Adhavan M

Welcome to my internship submission repository for the **VSDSquadron Research Internship 2025**, organized by [VSD - VLSI System Design](https://www.vlsisystemdesign.com/), under the mentorship of **Kunal Ghosh**.

This internship focuses on open-source SoC design, RISC-V processor architecture, Verilog simulation, and hands-on toolchain installation.

---

## 🧑‍💻 Profile

- **Name:** Sakthi Adhavan M
- **College:** Madras Institute of Technology  
- **GitHub:** [github.com/SakthiAdhavan20](https://github.com/SakthiAdhavan20)  
- **LinkedIn:** [www.linkedin.com/in/sakthi-adhavan](https://www.linkedin.com/in/sakthi-adhavan)  
- **Email:** sakthiadhavan.mit@gmail.com  

---

## 📁 Tasks Overview

| Task | Description | Status |
|------|-------------|--------|
| 🔧 [Task 1](#task-1--tool-installation-click-to-expand) | Tool Installation (Ubuntu, Toolchain, GTKWave, etc.) | ✅ Completed |
| 🔍 Task 2 | RISC-V Instruction Type and Format | ⏳ In Progress |
| ⚙️ Task 3 | Compile C code with GCC and RISC-V Toolchain | ⏳ In Progress |
| 🐞 Task 4 | Spike Simulation and Debugging | ⏳ In Progress |
| 🔁 Task 5 | Functional Simulation of RISC-V Netlist | ⏳ In Progress |
| 📦 Task 6 | Build and Upload to VSDSquadron Mini | ⏳ In Progress |

---

## ✅ Completed Tasks

<details>
<summary><strong>Task 1 – Tool Installation (Click to Expand)</strong></summary>

<br>

## Task 1 – Tool Installation

The goal of Task 1 is to install all essential tools required for the VSD Internship 2025.

---

### 1. Install Ubuntu 20.04 LTS on VirtualBox

Ubuntu is the OS used throughout the internship. We install it inside Oracle VirtualBox.

> 📸 Screenshot:  
![Ubuntu Installed](Task%201/ubuntu_installed.png)

---

### 2. Install RISC-V GNU Toolchain

The RISC-V GNU toolchain helps compile C/C++ to RISC-V assembly.

```bash
git clone https://github.com/riscv/riscv-gnu-toolchain

sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip \
libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf \
libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake \
libglib2.0-dev libslirp-dev

cd riscv-gnu-toolchain
./configure --prefix=$HOME/riscv
make -j$(nproc)
```

Add to PATH:

```bash
echo 'export PATH="$HOME/riscv/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

> 📸 Screenshot:  
![RISC-V Toolchain Installed](Task%201/riscv_toolchain.png)

---

### 3. Install GTKWave

GTKWave is a waveform viewer used to analyze `.vcd` simulation output.

```bash
sudo apt install gtkwave
```

> 📸 Screenshot:  
![GTKWave Installed](Task%201/gtkwave.png)

---

### 4. Install Yosys

Yosys performs synthesis of Verilog RTL.

```bash
sudo apt install yosys
yosys -V
```

> 📸 Screenshot:  
![Yosys Installed](Task%201/yosys.png)

---

### 5. Install Icarus Verilog

Used for simulating Verilog HDL designs and generating `.vcd` outputs.

```bash
sudo apt install iverilog
```

```bash
iverilog testbench.v design.v
./a.out
```

> 📸 Screenshot:  
![Icarus Verilog Installed](Task%201/iverilog.png)

---

### 6. Install xdot

xdot helps visualize `.dot` netlists (e.g. from Yosys).

```bash
sudo apt install xdot
```

> 📸 Screenshot:  
![xdot Installed](Task%201/xdot.png)

---

### ✅ Conclusion

All tools were successfully installed and verified on Ubuntu 20.04 VM.  
Ready to begin RTL simulation, synthesis, and RISC-V experiments.

</details>

---

## 📌 Note

All tools used are **open-source**.  
Tasks are implemented and documented manually on **Ubuntu 20.04 in VirtualBox**.  
This repo will be continuously updated.

---

## 📷 Screenshots

All tool screenshots are inside the `Task 1/` folder and embedded above.

---

## 📣 Acknowledgement

Thanks to [Kunal Ghosh](https://www.linkedin.com/in/kunalg101/) and VSD for enabling students to explore the world of VLSI and RISC-V.

---
