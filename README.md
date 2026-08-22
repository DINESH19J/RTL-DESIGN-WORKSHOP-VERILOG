# RTL Design & Synthesis Workshop (Verilog)

An end-to-end repository documenting design methodologies, logic synthesis, timing analysis, and netlist verification for digital IC design using standard EDA flows.

---

## 📌 Overview
This repository contains RTL Verilog code, testbenches, liberty timing specs, and synthesis results across a multi-week structured workflow.

* **HDL Language:** Verilog HDL
* **Design Domains:** Combinational & Sequential RTL, Gate-Level Synthesis, Timing Analysis
* **Tools Used:** Icarus Verilog / Yosys / Cadence / Synopsys EDA Tools (Specify your tools)

---

## 📂 Repository Structure

```text
├── DC_WORKSHOP/          # Design Compiler / Synthesis scripts
├── Week 1/               # Introduction to Liberty files & RTL Simulation
│   ├── read the liberty files.PNG
│   ├── design and test bench.PNG
│   └── README.md
├── Week 2/               # Synthesis, Timing Constraints & Optimization
│   └── README.md
├── lib/                  # Standard Cell Liberty (.lib) files
├── my_lib/               # Custom user target libraries
└── verilog_files/        # Raw Verilog design modules & testbenches
