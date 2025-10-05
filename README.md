# RISC-V-SoC-TAPEOUT-VSD_WEEK2
# Introduction to BabySoC &amp; Functional Modelling

# 🧩 BabySoC Functional Modelling Project

### 🎯 Objective
To build a solid understanding of **System-on-Chip (SoC)** fundamentals and practice **functional modelling** of the **BabySoC** using simulation tools **Icarus Verilog** and **GTKWave**.

---

## 🧠 1. Introduction to SoC

A **System-on-Chip (SoC)** is an **integrated circuit** that combines multiple hardware components (IPs) — both **digital and analog** — into a single silicon chip.

### Key Characteristics
- Includes CPU, memory, input/output interfaces, timers, and storage units.  
- Integration reduces interconnect distance → **lower area and power consumption**.  
- Can be **microprocessor-based** or **microcontroller-based**, depending on the system.

---

## ⚙️ 2. SoC Structure

An SoC can be divided into two main parts:

### **1️⃣ Functional Units (System Components)**
These perform the core processing and operations:
- **Processor Cores:** Execute instructions and manage computation.
- **Memory:** Stores data and instructions (RAM, ROM, cache).
- **Interfaces:** Handle communication with peripherals (USB, display, wireless).
- **DSPs / GPUs / Accelerators:** Perform specialized tasks like signal processing or AI.

### **2️⃣ Communication Subsystem (Chip Interconnect)**
Connects all functional units for efficient data transfer:
- **Intermodule Communication:** Enables data flow between modules.
- **Bus-Based Communication:** Uses shared high-speed lines for data transfer.
- **Network-on-Chip (NoC):** Modern packet-switched interconnect for scalability and concurrency — like a “mini-internet” inside the chip.

---

## 👶 3. Introduction to BabySoC

### **Main Components**
1. **RVMYTH Microprocessor (Digital)**  
   - A simple **RISC-V-based CPU** that executes instructions and handles digital control logic.

2. **Phase-Locked Loop (PLL) (Mixed-Signal)**  
   - Generates a **stable, high-frequency clock** signal to synchronize all digital components.

3. **Digital-to-Analog Converter (DAC) (Analog)**  
   - Converts **10-bit digital output** from RVMYTH into analog signals (e.g., audio, voltage waveform).

### **Why BabySoC?**
- Simplified architecture for **educational understanding**.  
- Open-source **RISC-V architecture** — ideal for academic and hobbyist learning.  
- Integrates only three essential IP cores → **clearer focus on functional flow**.

---

## 🧩 4. Functional Modelling

Functional modelling connects **high-level design concepts** to detailed **RTL implementation**.  
It validates **system logic and dataflow** before fabrication or synthesis.

### **Steps in Functional Modelling**

#### 🔹 Step 1: Specification & Partitioning
- Define **system requirements** (functions, interfaces, performance).
- Divide into **functional blocks (IP cores)**.
- Define **dataflow and control interaction** among them.

#### 🔹 Step 2: High-Level Coding
- **Algorithm Translation:** Write logic in high-level language (C/C++ or untimed HDL).
- **Behavioral Modelling:** Model each block’s behavior (focus on correctness, ignore timing).
- Develop a **Golden Reference Model** for later RTL comparison.

#### 🔹 Step 3: Simulation & Debugging
- **Stimuli Generation:** Prepare test vectors for inputs.
- **Simulation:** Run behavioral simulation in **Icarus Verilog (iverilog)**.
- **Waveform Analysis:** Visualize signal behavior in **GTKWave**.
- **Debugging:** Detect and correct algorithmic/logical errors early.

---

## 🧰 5. Tools Used

| Tool | Purpose |
|------|----------|
| **Icarus Verilog (iverilog)** | Compiling and simulating Verilog HDL files |
| **vvp** | Running compiled simulation output |
| **GTKWave** | Viewing signal waveforms for verification |

---

## 🧪 6. Simulation Workflow

### **Step 1: Compile Verilog Files**
```bash
$ iverilog -o output.vvp top_module.v submodule1.v submodule2.v testbench.v

