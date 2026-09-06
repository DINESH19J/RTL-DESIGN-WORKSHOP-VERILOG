# Module 1 — Inception of Open-Source EDA, OpenLANE and SKY130 PDK

## 📌 Overview

This module introduces the fundamentals of open-source digital ASIC design.

It begins with computer architecture, RISC-V and the transition from software applications to hardware.

The module then introduces System-on-Chip (SoC) concepts and Electronic Design Automation (EDA).

It explains the major stages involved in an RTL-to-GDSII digital ASIC design flow.

Open-source EDA tools such as Yosys, OpenROAD, Magic and OpenLANE are introduced.

The module also covers the OpenLANE ASIC implementation flow in detail.

The SKY130 Process Design Kit (PDK) is introduced as the technology platform used for implementation.

The practical work focuses on the `picorv32a` design using the SKY130A PDK.

---

## 🎯 Learning Objectives

- Understand how software instructions are executed by computer hardware.
- Understand the role of Instruction Set Architecture (ISA).
- Learn the basic concepts of RISC-V.
- Understand software-to-hardware conversion.
- Understand System-on-Chip architecture.
- Understand Electronic Design Automation.
- Learn the major stages of digital ASIC design.
- Understand the RTL-to-GDSII flow.
- Understand the purpose of OpenLANE.
- Understand the role of the SKY130 PDK.
- Understand standard-cell libraries.
- Understand the OpenLANE directory structure.
- Understand the design preparation stage.
- Understand RTL synthesis and technology mapping.
- Analyze synthesis results before physical design.

---

## 🔄 RTL-to-GDSII Flow

```text
Specification
     ↓
Architecture
     ↓
RTL Design
     ↓
RTL Simulation
     ↓
Logic Synthesis
     ↓
Gate-Level Netlist
     ↓
Floorplanning
     ↓
Power Planning
     ↓
Placement
     ↓
Clock Tree Synthesis
     ↓
Routing
     ↓
Parasitic Extraction
     ↓
Static Timing Analysis
     ↓
Physical Verification
     ↓
GDSII
