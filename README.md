# 🖥️ RISC-V Reference SoC Tapeout Program — VSD  
### Week 0 • Kick-Off — Digital VLSI SoC Design & Toolchain Setup

<div align="center">

[![RISC-V](https://img.shields.io/badge/RISC--V-SoC-blue?style=for-the-badge&logo=riscv)](https://riscv.org)
[![VSD Program](https://img.shields.io/badge/VSD%20Program-Open%20Silicon-orange?style=for-the-badge)](https://www.vlsisystemdesign.com/)
[![Week 0](https://img.shields.io/badge/Week%200-Completed-brightgreen?style=for-the-badge)](https://github.com/Nideshkanna/week0-getting-started)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Introduction
Welcome to the starting point of the RISC-V SoC tapeout adventure!  
In this first milestone we:

- Summarized **“Getting Started with Digital VLSI SoC Design”**  
- Installed and verified an open-source EDA toolchain (Yosys, Icarus Verilog, GTKWave, etc.)  
- Published our Week 0 progress on GitHub.

---

## 🚀 Beginning the Digital VLSI SoC Flow
The digital VLSI journey spans from abstract C models to silicon hardware.  
A golden rule binds every step:

> **Outputs must remain equivalent across all phases → O0 = O1 = O2 = O3 = O4 ✅**

---

### 📝 Design Philosophy
> **Golden Verification Principle**  
> The design’s behavior should remain identical as you move between levels of abstraction.

- A C-language testbench serves as the *golden reference*  
- Guarantees correctness from specification → RTL → SoC assembly → final die.

---

### 📊 Processor Compilation Pipeline

| Stage | Purpose | Key Artifact |
|-------|---------|--------------|
| **O0** | C Application | High-level code |
| **O1** | Chip Specification | Executable C model |
| **O2** | RTL Blueprint | Verilog description |
| **O3** | SoC Integration | Processor + IPs |
| **O4** | Final Silicon | Fabricated device |

---

### 🔄 Digital VLSI Design Stages
1. **Chip Modelling** — define behavior in C  
2. **RTL Authoring** — convert model → Verilog, divide into core & peripherals  
3. **Logic Synthesis** — map RTL into a gate-level netlist  
4. **Physical Design (RTL→GDSII)** — floorplan, place, route, export GDSII  
5. **Tape-Out** — run DRC/LVS, ship to foundry  
6. **Tape-In** — fabricate, dice, and package

---

## 🛠️ Lessons Learned
- Abstraction is vital: C model → GDSII  
- Verification is king: one **C testbench** validates every level  
- Organised phases streamline SoC development

---

## 🧰 Task 2 — Tool Installation

> **Platform:** Ubuntu 22.04 (6 GB RAM, 4 vCPUs, 70 GB disk)

### ▶️ Yosys
```bash
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git \
graphviz xdot pkg-config python3 libboost-system-dev \
libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make
sudo make install
```
### Check
```bash
yosys --version
```
### ▶️ Icarus Verilog
```bash
sudo apt-get update
sudo apt-get install iverilog
iverilog -V
```
### ▶️ GTKwave
```bash
sudo apt-get update
sudo apt-get install gtkwave
gtkwave --version
```
### ▶️ NgSpice Installation
```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release && cd release
../configure --with-x --with-readline=yes --disable-debug
make
sudo make install
```

### Check 
```bash
ngspice --version
```

### ▶️ Magic
```bash
sudo apt-get install m4 tcsh csh libx11-dev \
tcl-dev tk-dev libcairo2-dev mesa-common-dev libglu1-mesa-dev libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
magic -d XR
```

### ▶️ OpenLane ( Docker )
```bash
sudo apt-get update && sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o \
/usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
docker run hello-world
```

### Build OpenLane
```bash
cd ~
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test
```

## 🗃️ Task 3 : Github Repo Creation
- [Week 0 Repo]{https://github.com/Techwithram/Week-0-of-RISC-V-SoC-Program)
- [Main Repo - Overview ](https://github.com/Techwithram/RISC-V-SOC-Tapeout-Program)
- Week 1 : Coming Soon

## ⏫ Wrap Up:
| Tool           | Purpose         | Status |
| -------------- | --------------- | ------ |
| Yosys          | RTL synthesis   | ✔️     |
| Icarus Verilog | Simulation      | ✔️     |
| GTKWave        | Waveform viewer | ✔️     |
| Ngspice        | SPICE analysis  | ✔️     |
| Magic          | Layout + DRC    | ✔️     |
| OpenLANE       | RTL→GDSII flow  | ✔️     |


Maintainer : [Tatikonda Ramakrishna](https://github.com/Techwithram)
