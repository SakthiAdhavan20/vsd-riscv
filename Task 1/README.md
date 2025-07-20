# Task 1 – Tool Installation

The goal of Task 1 is to install all essential tools required for the VSD Internship 2025.

---

## 1. Install Ubuntu 20.04 LTS on VirtualBox

Ubuntu is the operating system we’ll use throughout this internship. We install it using Oracle VirtualBox so it runs inside your existing computer, without replacing your original OS.

Oracle VirtualBox is a free and open-source hypervisor for x86 virtualization. It allows us to create a virtual machine (VM) where we install Ubuntu 20.04 as a guest OS.

> 📸 Screenshot:  
![Ubuntu Installed](ubuntu_installed.png)

---

## 2. Install RISC-V GNU Toolchain

The RISC-V GNU toolchain is a set of open-source programming tools (compiler, assembler, linker, etc.) for developing software for RISC-V-based processors. This toolchain helps convert C/C++ programs into RISC-V assembly so it can run on a RISC-V simulator or core.

### 🔧 Commands Used:

```bash
# Clone the official RISC-V GNU Toolchain repository
git clone https://github.com/riscv/riscv-gnu-toolchain

# Install required dependencies for building the toolchain
sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip \
libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf \
libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake \
libglib2.0-dev libslirp-dev

# Move into the toolchain folder
cd riscv-gnu-toolchain

# Configure the build to install toolchain binaries in $HOME/riscv
./configure --prefix=$HOME/riscv

# Build the toolchain using all available processor cores
make -j$(nproc)
```

✅ After installation, you must add the toolchain to your system PATH so that commands like `riscv64-unknown-elf-gcc` work from anywhere:

```bash
echo 'export PATH="$HOME/riscv/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

> 📸 Screenshot:  
![RISC-V GNU Toolchain Installed](riscv_toolchain.png)

---

## 3. Install GTKWave

GTKWave is a waveform viewer that lets you view signal transitions over time from simulation files (like `.vcd`). It is crucial for debugging digital designs and understanding signal behavior in Verilog simulations.

```bash
sudo apt install gtkwave
```

Once installed, you can open it with `gtkwave` in the terminal.

> 📸 Screenshot:  
![GTKWave Installed](gtkwave.png)

---

## 4. Install Yosys

Yosys is an open-source framework for RTL synthesis. It translates Verilog RTL code into a lower-level netlist format. It’s commonly used with open-source ASIC/FPGA flows.

```bash
sudo apt install yosys
```

You can verify it with:
```bash
yosys -V
```

> 📸 Screenshot:  
![Yosys Installed](yosys.png)

---

## 5. Install Icarus Verilog

Icarus Verilog is a simulator that compiles Verilog source files into executable simulation models. It’s used for testing Verilog code and generating `.vcd` files for GTKWave.

```bash
sudo apt install iverilog
```

You can compile and run simulations using:
```bash
iverilog testbench.v design.v
./a.out
```

> 📸 Screenshot:  
![Icarus Verilog Installed](iverilog.png)

---

## 6. Install xdot

`xdot` is a tool to visualize `.dot` files (graph descriptions), especially useful when analyzing synthesized RTL netlists from Yosys.

```bash
sudo apt install xdot
```

You can use this to view RTL-level connections (wires, gates) in a graphical form.

> 📸 Screenshot:  
![xdot Installed](xdot.png)

---

## ✅ All tools successfully installed and verified.

You are now ready to start simulation, synthesis, and RISC-V development using these tools.


