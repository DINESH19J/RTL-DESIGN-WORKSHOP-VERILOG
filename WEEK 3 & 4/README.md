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



### OpenLANE ASIC Design Flow

OpenLANE provides an automated open-source ASIC implementation flow.

The design passes through synthesis, floorplanning, placement, clock tree synthesis, routing, extraction, timing analysis, and physical verification.

The flow uses the **SKY130 Process Design Kit (PDK)** to provide technology-specific information such as standard cells, design rules, transistor models, and physical layers.

---

# 5. RTL Synthesis

![RTL Synthesis](images/5%20synthesis%20succes.PNG)

### RTL Synthesis and Successful Synthesis

RTL synthesis converts the hardware description into a gate-level netlist.

During this stage, design constraints such as clock period, input delay, output delay, and load conditions are applied.

The synthesis process maps the RTL logic onto available standard cells from the SKY130 library.

The terminal output shown above confirms that the synthesis process was completed successfully.

---

# 6. Synthesis Statistics

![Synthesis Statistics](images/6%20ff%20ratio.png)

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

![Flip-Flop Analysis](images/6%20ff%20ratio.png)

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

![Placement Analysis](images/7.placement%20visual.PNG)

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

![Placement Visualization](images/8%20placement.PNG)

### Standard Cell Placement Visualization

This image provides a visual representation of the placed standard cells.

The cells are arranged in rows within the core area of the chip. Proper placement is important because the physical location of the cells directly affects routing complexity, interconnect length, timing, and chip area.

The placement result provides the foundation for the subsequent routing stage.

---

# 10. Magic VLSI Layout Inspection

![Magic VLSI Layout](images/9%20magic%20layout.PNG)

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

![CMOS Inverter Layout](images/10%20layout%20inverter.PNG)

### CMOS Inverter Physical Layout

The CMOS inverter is a fundamental digital logic circuit consisting of a PMOS transistor and an NMOS transistor.

The PMOS transistor is connected toward the positive supply, while the NMOS transistor is connected toward ground.

The physical layout represents these transistor structures using semiconductor layers such as diffusion, polysilicon, contacts, and metal interconnections.

This layout demonstrates how a basic CMOS logic gate is physically implemented in the SKY130 technology.

---

# 12. Layout Layer Inspection

![Layout Layer Inspection](images/11%20layout%20layer%20inspection.PNG)

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

![SPICE Testbench](images/12%20transient%20analysis%20testbench.PNG)

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

![Extracted Netlist](images/extracted%20netlist%20standard%20inverter.PNG)

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

![NGSPICE Simulation](images/ngspice%20transient%20spice%20simulation.PNG)

### NGSPICE Post-Layout Simulation

NGSPICE is used to simulate the extracted circuit.

Unlike a purely schematic-level simulation, post-layout simulation uses the circuit information obtained from the physical implementation.

This allows the electrical behavior of the implemented circuit to be evaluated while considering the effects introduced by the physical layout and parasitic elements.

---

# 16. Transient Simulation Waveform

![Transient Simulation Waveform](images/Capture.PNG)

### Transient Analysis and Waveform Verification

Transient analysis is performed by applying a time-varying pulse signal to the CMOS inverter.

The input switches between logic LOW and HIGH, while the output responds inversely.

The waveform demonstrates the expected inverter behavior:

- Input LOW → Output HIGH
- Input HIGH → Output LOW

The repeated switching confirms the functional behavior of the CMOS inverter during transient simulation.

---

# 17. Final Physical Layout

![Final Physical Layout](images/15%20layout.PNG)

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
