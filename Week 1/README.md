# Week 1 – Introduction to Liberty Files & RTL Simulation

This week focuses on understanding standard cell **Liberty (.lib) files** and getting hands-on with **RTL design and testbench simulation** using Verilog.

---

## 📑 Table of Contents

- [Overview](#overview)
- [1. Reading Liberty Files](#1-reading-liberty-files)
- [2. RTL Design and Testbench](#2-rtl-design-and-testbench)
- [Key Takeaways](#key-takeaways)

---

## Overview

Before synthesizing any RTL design into hardware, it's essential to understand the standard cell libraries that map logical gates to real, physical cells with defined timing, power, and area characteristics. This week covers:

- Understanding the structure and contents of a `.lib` (Liberty) file
- Writing a simple RTL design in Verilog
- Creating a testbench to verify the design's functionality through simulation

---

## 1. Reading Liberty Files

[#1-reading-liberty-files](#1-reading-liberty-files)

A **Liberty file (.lib)** is a standard format used by EDA tools to describe the electrical and timing characteristics of a standard cell library — the collection of logic gates (AND, OR, NAND, flip-flops, etc.) that RTL code gets mapped to during synthesis.

A `.lib` file typically defines:

- **Cell definitions** – logic function, pin names, and directions (input/output)
- **Timing parameters** – propagation delay, setup/hold times for each cell
- **Power information** – leakage power, dynamic power per cell
- **PVT corners** – Process, Voltage, and Temperature variations the cell was characterized under (e.g. `slow`, `typical`, `fast` corners)
- **Cell drive strengths** – multiple versions of the same gate (e.g. `AND2_X1`, `AND2_X2`) with different sizes for different speed/power trade-offs

Reading and understanding these files is the first step before synthesis, since the synthesis tool picks the best-matching cells from this library based on your design's timing constraints.

![Reading the liberty files](./read%20the%20liberty%20files.PNG)

---

## 2. RTL Design and Testbench

[#2-rtl-design-and-testbench](#2-rtl-design-and-testbench)

With the library concepts in place, the next step is writing an RTL design in Verilog and verifying it using a testbench.

**RTL Design**
The RTL (Register Transfer Level) code describes the intended hardware behavior at a functional level using Verilog constructs (`always` blocks, `assign` statements, etc.), without worrying about the underlying gate implementation.

**Testbench**
A testbench is a separate Verilog file that:
- Instantiates the design module (Device Under Test / DUT)
- Applies a set of input stimuli over time
- Observes and checks the output response

**Simulation Flow**
1. Write the RTL design (`design.v`)
2. Write the testbench (`tb_design.v`)
3. Compile both using a simulator (e.g. `iverilog design.v tb_design.v -o output`)
4. Run the simulation (`./output` or `vvp output`)
5. View the generated waveform in **GTKWave** to verify correctness

This flow confirms the RTL design behaves as expected *before* it's ever synthesized into gates.

![Design and testbench](./design%20and%20test%20bench.PNG)

---

## Key Takeaways

- Liberty files bridge the gap between abstract RTL logic and real, physical standard cells
- Understanding `.lib` structure (timing, power, PVT corners) is essential before synthesis
- RTL design + testbench + simulation is the standard verification flow to catch functional bugs early
- Waveform analysis in GTKWave is used to visually confirm expected behavior against the testbench stimuli
