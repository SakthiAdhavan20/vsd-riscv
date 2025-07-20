# Task 1 – Tool Installation

The goal of Task 1 is to install all essential tools required for the VSD Internship 2024.

---

## 1. Install Ubuntu 20.04 LTS on VirtualBox

Ubuntu 20.04 was installed using Oracle VirtualBox.

> 📸 Screenshot:  
![Ubuntu Installed](ubuntu_installed.png)

---

## 2. Install RISC-V GNU Toolchain

### 🔧 Commands Used:

```bash
git clone https://github.com/riscv/riscv-gnu-toolchain
sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip \
libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf \
libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev
cd riscv-gnu-toolchain
./configure --prefix=$HOME/riscv
make -j$(nproc)
```

> 📸 Screenshot:  
![RISC-V GNU Toolchain Installed](riscv_toolchain.png)

---

## 3. Install GTKWave

```bash
sudo apt install gtkwave
```

> 📸 Screenshot:  
![GTKWave Installed](gtkwave.png)

---

## 4. Install Yosys

```bash
sudo apt install yosys
```

> 📸 Screenshot:  
![Yosys Installed](yosys.png)

---

## 5. Install Icarus Verilog

```bash
sudo apt install iverilog
```

> 📸 Screenshot:  
![Icarus Verilog Installed](iverilog.png)

---

## 6. Install xdot

```bash
sudo apt install xdot
```

> 📸 Screenshot:  
![xdot Installed](xdot.png)

---

## ✅ All tools successfully installed and verified.

