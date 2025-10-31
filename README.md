# SPI_Wrapper 🧩

## UVM Verification Environment for SPI-Wrapper-RAM

---

## 📜 Overview

This repository presents a comprehensive Universal Verification Methodology (UVM) testbench for verifying a system that integrates:
- **SPI Slave**
- **Single-Port RAM**
Via an **SPI Wrapper interface**.

**Main Objective:**  
Demonstrate modular verification reuse, integrating individual UVM environments for component-level verification (SPI Slave and RAM) into a system-level verification environment for the SPI Wrapper.

---

## 🧠 Project Structure and Verification Phases

The verification is divided into three main parts, each focusing on a different design block:

### 1️⃣ Part 1 – SPI Slave Verification
- **DUT:** SPI Slave core (implements Serial Peripheral Interface protocol)
- **UVM Environment:**  
  - Validates SPI protocol compliance
  - Dedicated sequences cover transactions:
    - Write Address
    - Write Data
    - Read Address
    - Read Data

### 2️⃣ Part 2 – Single-Port RAM Verification
- **DUT:** Parameterized Single-Port RAM  
  - Default configuration: `MEM_DEPTH = 256`, `ADDR_SIZE = 8`
- **UVM Environment:**  
  - Ensures correct read/write behavior
  - Checks address range and data coherence via randomized and directed tests

### 3️⃣ Part 3 – SPI Wrapper (System Integration Verification)
- **DUT:** SPI Wrapper (integration layer between SPI Slave and RAM)
- **UVM Environment:**  
  - Top-level verification
  - Reuses SPI Slave and RAM environments as passive agents
  - Enables full system-level verification of data integrity and communication flow

---

## 🎯 Verification Highlights

### Coverage Goals

- **Code Coverage:**  
  - 100% line, toggle, branch, and expression coverage
- **Functional Coverage:**  
  - Coverpoints on interface signals (`rx_data`, `SS_n`, `MOSI`, etc.)
  - Cross-coverage between command types (`din[9:8]`, `MOSI` command bits) and control signals (`rx_valid`, `tx_valid`)
  - Sequential coverage for transaction orderings (e.g., Write → Read)

### Assertions (SystemVerilog Assertions - SVA)

- **Safety Checks:**  
  - Reset behavior (all outputs de-asserted on reset)
- **Liveness Checks:**  
  - Commands must trigger corresponding responses (write → read)
- **Temporal Checks:**  
  - Timing relations between critical signals (`rx_valid`, `tx_valid`, etc.)

### Sequences and Scenarios

- Multiple parameterized and randomized sequences:
  - `reset_sequence`
  - `write_only_sequence`
  - `read_only_sequence`
  - `write_read_sequence` (randomized operation selection)

---

## 👥 Project Team

- **Mohamed Mostafa**
- **Mohamed Rafaat El Sheikh**
- **Youssef Tantawy**

Developed with passion for verification excellence and UVM reusability.



**For questions or contributions, feel free to open an Issue or Pull Request!**
