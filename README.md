🧩 SPI Wrapper UVM Verification Environment
📜 Overview

This repository presents a comprehensive UVM (Universal Verification Methodology) testbench designed to verify a system integrating an SPI Slave and a Single-Port RAM through an SPI Wrapper interface.

The primary goal of this project is to demonstrate modular verification reuse, where component-level UVM environments (for SPI Slave and RAM) are integrated into a system-level environment to validate the SPI Wrapper functionality.

🧠 Project Structure & Verification Phases

The verification is divided into three main parts, each targeting a specific design block:

🔹 Part 1 – SPI Slave Verification

DUT: SPI Slave core implementing the SPI protocol.

Objective: Verify SPI protocol compliance.

Key Features:

Directed and randomized sequences for various SPI transactions:

Write Address

Write Data

Read Address

Read Data

🔹 Part 2 – Single-Port RAM Verification

DUT: Parameterized Single-Port RAM

MEM_DEPTH = 256, ADDR_SIZE = 8

Objective: Validate memory behavior and integrity.

Key Features:

Randomized and directed tests

Address range checking

Read/Write data coherence

🔹 Part 3 – SPI Wrapper (System Integration Verification)

DUT: SPI Wrapper (integration layer between SPI Slave and RAM).

Objective: Verify end-to-end data flow and integration behavior.

Key Features:

Reuse of SPI Slave and RAM UVM environments as passive agents

Full system-level verification of communication and data integrity

🎯 Verification Highlights
✅ Coverage Goals

To ensure comprehensive verification, the following targets were achieved:

Code Coverage:

100% line, toggle, branch, and expression coverage.

Functional Coverage:

Coverpoints on interface signals (rx_data, SS_n, MOSI, etc.)

Cross-coverage between command types (din[9:8], MOSI bits) and control signals (rx_valid, tx_valid)

Sequential coverage for transaction orderings such as:

Write Address → Write Data → Read Address → Read Data

🧩 Assertions (SVA)

SystemVerilog Assertions were implemented to ensure protocol and timing correctness:

Safety Checks: Validate reset behavior (outputs de-assert after reset).

Liveness Checks: Ensure that each command triggers a valid response.

Temporal Checks: Verify timing relations between key handshake signals (rx_valid, tx_valid, etc.).

🔁 Sequences & Scenarios

A diverse set of sequences ensures both directed and randomized verification:

Sequence Name	Description
reset_sequence	Validates correct system reset behavior.
write_only_sequence	Tests write transactions exclusively.
read_only_sequence	Tests read transactions exclusively.
write_read_sequence	Randomized mix of read and write operations with probabilistic selection.
👥 Project Team
Name	Role
Mohamed Mostafa Mohamed	UVM Testbench Developer
Rafaat El Sheikh	Design & Verification Engineer
Youssef Tantawy	Verification Engineer
💡 Key Takeaway

This project showcases verification reusability and modularity through a layered UVM architecture, ensuring scalable and maintainable test environments for complex system-level verification.

🛠️ Tools & Technologies

Language: SystemVerilog

Methodology: UVM (IEEE 1800.2)

Simulator: Mentor QuestaSim / Synopsys VCS

Version Control: Git & GitHub
