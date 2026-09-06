
---

# `03-OpenLANE-and-SKY130-PDK.md`

```markdown
# 03 — OpenLANE and SKY130 PDK

## 📌 Introduction

OpenLANE is an open-source digital ASIC implementation flow.

It combines several open-source EDA tools to automate major stages of ASIC physical implementation.

The SKY130 PDK provides technology-specific information required to design chips using a 130 nm process.

This section explains OpenLANE, SKY130, PDK contents and standard-cell libraries.

---

## 🏗️ OpenLANE

OpenLANE provides an automated RTL-to-GDSII implementation flow.

It integrates tools for synthesis, floorplanning, placement, clock tree synthesis, routing and verification.

A simplified OpenLANE flow is:

```text
Design Preparation
       ↓
Synthesis
       ↓
Floorplan
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
Timing Analysis
       ↓
Physical Verification
