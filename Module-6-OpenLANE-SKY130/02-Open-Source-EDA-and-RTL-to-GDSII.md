
---

# `02-Open-Source-EDA-and-RTL-to-GDSII.md`

```markdown
# 02 — Open-Source EDA and RTL-to-GDSII Flow

## 📌 Introduction

Electronic Design Automation (EDA) tools are essential for designing modern integrated circuits.

They automate complex tasks that would otherwise require extensive manual effort.

Open-source EDA tools provide accessible solutions for learning, research and practical ASIC development.

This section introduces the major EDA stages and the RTL-to-GDSII flow.

---

## 🔧 What is EDA?

EDA stands for Electronic Design Automation.

EDA consists of software tools used to design, simulate, synthesize and verify electronic circuits.

In ASIC design, EDA tools are used throughout both front-end and back-end implementation.

Important EDA tasks include:

- RTL simulation
- Logic synthesis
- Floorplanning
- Placement
- Clock Tree Synthesis
- Routing
- Timing analysis
- Physical verification

---

## 🧩 Major Open-Source Tools

| Tool | Main Function |
|------|---------------|
| Icarus Verilog | Verilog simulation |
| GTKWave | Waveform visualization |
| Yosys | RTL synthesis |
| OpenROAD | Physical implementation |
| RePlAce | Placement optimization |
| Magic | Layout visualization and verification |
| OpenLANE | Complete ASIC flow |

---

## 🔄 RTL-to-GDSII

RTL-to-GDSII is the process of converting a digital RTL design into physical chip layout data.

The major stages are:

```text
RTL
 ↓
Simulation
 ↓
Synthesis
 ↓
Floorplanning
 ↓
Power Planning
 ↓
Placement
 ↓
CTS
 ↓
Routing
 ↓
Extraction
 ↓
STA
 ↓
Physical Verification
 ↓
GDSII
