# 🔬 RTL-to-GDSII ASIC Design Flow Using OpenLANE and SKY130

## 📌 Project Overview

This project demonstrates a complete open-source ASIC design flow, starting from RTL design and progressing through synthesis, placement, physical layout, layout inspection, SPICE netlist extraction, and post-layout simulation.

The implementation uses the **OpenLANE ASIC flow**, **SKY130 PDK**, **Magic VLSI**, and **NGSPICE** to demonstrate the transition from a digital design description to its physical implementation and electrical verification.

The project also includes the design and analysis of a **CMOS inverter**, allowing the physical layout to be extracted into a SPICE netlist and verified through transient simulation.

---

# 📑 Contents

1. [Introduction](#1-introduction)
2. [ASIC Design Methodology](#2-asic-design-methodology)
3. [RTL-to-GDSII Design Flow](#3-rtl-to-gdsii-design-flow)
4. [OpenLANE and SKY130 PDK](#4-openlane-and-sky130-pdk)
5. [RTL Synthesis](#5-rtl-synthesis)
6. [Synthesis Statistics](#6-synthesis-statistics)
7. [Flip-Flop and Standard Cell Analysis](#7-flip-flop-and-standard-cell-analysis)
8. [Placement and Physical Design](#8-placement-and-physical-design)
9. [Placement Visualization](#9-placement-visualization)
10. [Magic VLSI Layout Inspection](#10-magic-vlsi-layout-inspection)
11. [CMOS Inverter Layout](#11-cmos-inverter-layout)
12. [Layout Layer Inspection](#12-layout-layer-inspection)
13. [SPICE Testbench](#13-spice-testbench)
14. [Extracted SPICE Netlist](#14-extracted-spice-netlist)
15. [Post-Layout SPICE Simulation](#15-post-layout-spice-simulation)
16. [Transient Simulation Waveform](#16-transient-simulation-waveform)
17. [Final Physical Layout](#17-final-physical-layout)
18. [Results and Observations](#18-results-and-observations)
19. [Conclusion](#19-conclusion)
20. [References](#20-references)

---

# 1. Introduction

Very Large Scale Integration (VLSI) design involves transforming a high-level hardware description into a physical integrated circuit.

The ASIC design process consists of several stages including:

- RTL design
- Logic synthesis
- Floorplanning
- Placement
- Clock tree synthesis
- Routing
- Physical verification
- Layout extraction
- Circuit simulation
- GDSII generation

This project demonstrates these stages using open-source tools and the SKY130 technology process.

---

# 2. ASIC Design Methodology

The ASIC design methodology provides a structured path from a functional hardware description to a manufacturable chip layout.

The design begins with an RTL description that defines the required digital functionality. The RTL is synthesized into standard cells and then physically implemented through placement and routing.

The final physical design is converted into GDSII format, which contains the geometric information required for semiconductor fabrication.

---

# 3. RTL-to-GDSII Design Flow

<img width="842" height="476" alt="3" src="https://github.com/user-attachments/assets/bee0ebea-8b40-4ac3-8f21-93d52bcf5ef9" />

### Simplified RTL-to-GDSII Flow

The RTL-to-GDSII flow represents the complete transformation of an RTL design into a physical chip layout.

The major stages include:

1. RTL design
2. Logic synthesis
3. Floorplanning
4. Power planning
5. Placement
6. Clock Tree Synthesis
7. Routing
8. Parasitic extraction
9. Static timing analysis
10. Physical verification
11. GDSII generation

The GDSII file represents the final physical geometry of the integrated circuit.

---

# 4. OpenLANE and SKY130 PDK

<img width="1295" height="650" alt="4" src="https://github.com/user-attachments/assets/c1503fc9-8338-4b55-8958-cff2fc4fdecb" />

### OpenLANE ASIC Design Flow

OpenLANE provides an automated open-source ASIC implementation flow.

The design passes through synthesis, floorplanning, placement, clock tree synthesis, routing, extraction, timing analysis, and physical verification.

The flow uses the **SKY130 Process Design Kit (PDK)** to provide technology-specific information such as standard cells, design rules, transistor models, and physical layers.

---

# 5. RTL Synthesis

<img width="1350" height="728" alt="5 synthesis succes" src="https://github.com/user-attachments/assets/3acd2ff3-b6a7-411b-9c8c-7302c6fb8cf5" />

### RTL Synthesis and Successful Synthesis

RTL synthesis converts the hardware description into a gate-level netlist.

During this stage, design constraints such as clock period, input delay, output delay, and load conditions are applied.

The synthesis process maps the RTL logic onto available standard cells from the SKY130 library.

The terminal output shown above confirms that the synthesis process was completed successfully.

---

# 6. Synthesis Statistics

<img width="1217" height="645" alt="6 ff ratio" src="https://github.com/user-attachments/assets/edaa0a8b-6124-4eed-8a0a-3e6289e566b5" />

### Standard Cell Statistics

The synthesis results provide information about the cells used in the generated gate-level design.

The design contains approximately **14,786 cells**, including:

- Inverters
- Buffers
- Logic gates
- Multiplexers
- Flip-flops
- Other standard cells

These statistics provide an overview of the complexity of the synthesized design.

---

# 7. Flip-Flop and Standard Cell Analysis

<img width="1217" height="645" alt="6 ff ratio" src="https://github.com/user-attachments/assets/0cfb6cc7-2bb2-46c7-b6ca-bfc29b6b53d3" />

### Flip-Flop Ratio Analysis

The synthesis statistics show approximately **1,613 D-type flip-flops** in the design.

The flip-flop ratio is calculated as:

\[
\text{Flip-Flop Ratio}
=
\frac{\text{Number of Flip-Flops}}
{\text{Total Number of Cells}}
\times 100
\]

Using the synthesis results:

\[
\text{Flip-Flop Ratio}
\approx 10.84\%
\]

This value represents the proportion of sequential storage elements within the synthesized design.

---

# 8. Placement and Physical Design

<img width="1146" height="607" alt="7 placement visual" src="https://github.com/user-attachments/assets/83cfec38-5988-4403-b238-9d96185344c5" />

### Placement Analysis and Optimization

After synthesis, the standard cells are physically positioned inside the chip core.

The placement stage considers several physical parameters including:

- Cell utilization
- Wirelength
- Displacement
- Routing congestion
- Timing requirements

The placement process attempts to arrange the cells efficiently while satisfying the physical design constraints.

---

# 9. Placement Visualization

<img width="807" height="608" alt="8 placement" src="https://github.com/user-attachments/assets/e6d57f97-dbe1-4263-b4a4-1cfae37f1615" />

### Standard Cell Placement Visualization

This image provides a visual representation of the placed standard cells.

The cells are arranged in rows within the core area of the chip. Proper placement is important because the physical location of the cells directly affects routing complexity, interconnect length, timing, and chip area.

The placement result provides the foundation for the subsequent routing stage.

---

# 10. Magic VLSI Layout Inspection

<img width="838" height="394" alt="9 magic layout" src="https://github.com/user-attachments/assets/ab5e2e02-d5c4-49f4-89af-76eb0242a2e4" />

### Layout Visualization Using Magic VLSI

Magic VLSI is used to view and inspect the physical layout generated during the ASIC implementation process.

Different colors represent different physical layers such as:

- Diffusion
- Polysilicon
- Metal
- Contacts
- Well regions

Magic allows the physical geometry and connectivity of the design to be inspected at the layout level.

---

# 11. CMOS Inverter Layout

<img width="838" height="406" alt="10 layout inverter" src="https://github.com/user-attachments/assets/497d80b9-ba87-4c8f-b0b8-ff8451098261" />

### CMOS Inverter Physical Layout

The CMOS inverter is a fundamental digital logic circuit consisting of a PMOS transistor and an NMOS transistor.

The PMOS transistor is connected toward the positive supply, while the NMOS transistor is connected toward ground.

The physical layout represents these transistor structures using semiconductor layers such as diffusion, polysilicon, contacts, and metal interconnections.

This layout demonstrates how a basic CMOS logic gate is physically implemented in the SKY130 technology.

---

# 12. Layout Layer Inspection

<img width="689" height="387" alt="11 layout layer inspection" src="https://github.com/user-attachments/assets/928d808d-aa80-449d-885b-a4e2b1a2b964" />

### Layer-Level Layout Inspection

The physical layout is inspected layer by layer using Magic VLSI.

Layer inspection allows the individual structures of the CMOS circuit to be examined, including:

- Diffusion regions
- Polysilicon gates
- Metal interconnections
- Contacts
- Power connections

This step helps verify the physical connectivity and geometry of the layout.

---

# 13. SPICE Testbench

<img width="838" height="479" alt="12 transient analysis testbench" src="https://github.com/user-attachments/assets/ee81b65d-ce0c-41cb-86e6-bd6723b51b0d" />

### SPICE Testbench for CMOS Inverter

A SPICE testbench is created to evaluate the electrical behavior of the CMOS inverter.

The testbench contains:

- PMOS and NMOS transistor models
- Supply voltage
- Input pulse signal
- Output node
- Simulation parameters
- Transient analysis command

The SKY130 transistor models are used to provide technology-specific device behavior.

The input pulse allows the inverter's switching response to be analyzed.

---

# 14. Extracted SPICE Netlist

<img width="830" height="326" alt="extracted netlist standard inverter" src="https://github.com/user-attachments/assets/fc38da94-cb0b-41ce-a6ef-b92dbaf2eabc" />

### Layout-Extracted SPICE Netlist

The physical layout can be converted into an electrical representation using layout extraction.

The extracted SPICE netlist represents the transistor-level connectivity obtained from the physical layout.

The extracted model can include:

- PMOS device
- NMOS device
- Device terminals
- Interconnections
- Parasitic components

This enables the physical layout to be electrically simulated and verified.

---

# 15. Post-Layout SPICE Simulation

<img width="830" height="326" alt="extracted netlist standard inverter" src="https://github.com/user-attachments/assets/c55953df-02d9-46a1-bf0e-b3fdb306358c" />

### NGSPICE Post-Layout Simulation

NGSPICE is used to simulate the extracted circuit.

Unlike a purely schematic-level simulation, post-layout simulation uses the circuit information obtained from the physical implementation.

This allows the electrical behavior of the implemented circuit to be evaluated while considering the effects introduced by the physical layout and parasitic elements.

---

# 16. Transient Simulation Waveform

<img width="832" height="432" alt="ngspice transient spice simulation" src="https://github.com/user-attachments/assets/1d8b0cfe-a131-42eb-969f-617dafa2aa8e" />

### Transient Analysis and Waveform Verification

Transient analysis is performed by applying a time-varying pulse signal to the CMOS inverter.

The input switches between logic LOW and HIGH, while the output responds inversely.

The waveform demonstrates the expected inverter behavior:

- Input LOW → Output HIGH
- Input HIGH → Output LOW

The repeated switching confirms the functional behavior of the CMOS inverter during transient simulation.

---

# 17. Final Physical Layout

<img width="831" height="497" alt="15 layout" src="https://github.com/user-attachments/assets/38c8b0fe-b353-49ad-8ccf-405159347157" />

### Final Layout Result

The final physical layout represents the implemented design after the physical design stages.

The layout contains the required standard cells, interconnections, power structures, and technology-specific layers.

The completed physical design can be subjected to physical verification before generating the final GDSII representation.

---

# 18. Results and Observations

The project successfully demonstrates the transition from RTL design to physical ASIC implementation.

### Key observations

- RTL was successfully synthesized.
- Standard-cell statistics were obtained from the synthesized design.
- Flip-flop utilization was analyzed.
- Standard cells were physically placed.
- The physical layout was generated and inspected using Magic VLSI.
- A CMOS inverter layout was created and examined at the layer level.
- The physical layout was extracted into a SPICE netlist.
- NGSPICE was used for post-layout transient simulation.
- The inverter produced the expected complementary output response.

---

# 19. Conclusion

This project demonstrates a complete open-source ASIC design and verification workflow using **OpenLANE, SKY130, Magic VLSI, and NGSPICE**.

The work covers the complete path from RTL synthesis to physical implementation and post-layout electrical simulation.

The CMOS inverter example further demonstrates the relationship between transistor-level circuit design, physical layout, layout extraction, and SPICE simulation.

Overall, the project provides practical exposure to the major stages involved in modern ASIC physical design and open-source VLSI implementation.

---

# 20. References

- OpenLANE ASIC Design Flow
- SKY130 Open-Source PDK
- Magic VLSI Layout Tool
- NGSPICE Circuit Simulator
- Yosys RTL Synthesis
- OpenROAD Physical Design Tools

---

## 🛠️ Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| **OpenLANE** | Automated RTL-to-GDSII ASIC flow |
| **SKY130 PDK** | Semiconductor technology and standard-cell library |
| **Yosys** | RTL synthesis |
| **OpenROAD** | Physical design implementation |
| **Magic VLSI** | Layout visualization and inspection |
| **NGSPICE** | Circuit and post-layout simulation |
| **GDSII** | Final physical layout representation |

---

## 📂 Project Structure

```text
ASIC-Design-Project/
│
├── README.md
│
├── images/
│   ├── 2.PNG
│   ├── 3.PNG
│   ├── 4.PNG
│   ├── 5 synthesis succes.PNG
│   ├── 6 ff ratio.png
│   ├── 7.placement visual.PNG
│   ├── 8 placement.PNG
│   ├── 9 magic layout.PNG
│   ├── 10 layout inverter.PNG
│   ├── 11 layout layer inspection.PNG
│   ├── 12 transient analysis testbench.PNG
│   ├── extracted netlist standard inverter.PNG
│   ├── ngspice transient spice simulation.PNG
│   ├── 15 layout.PNG
│   └── Capture.PNG
│
├── rtl/
│
├── synthesis/
│
├── placement/
│
├── layout/
│
├── spice/
│
└── results/
