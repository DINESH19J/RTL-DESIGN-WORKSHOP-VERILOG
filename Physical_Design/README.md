# OpenROAD Physical Design and Static Timing Analysis (STA)

## Project Overview

This project documents the physical design and post-route Static Timing Analysis (STA) of a digital circuit using **OpenROAD and the SkyWater SKY130 HD platform**.

The OpenROAD flow was used to examine the design at different physical implementation stages, including floorplanning, placement, clock-tree synthesis, routing, and post-route timing analysis.

The screenshots included in this repository provide visual evidence of the implementation stages and timing reports.

## Objectives

- Understand the physical design flow using OpenROAD.
- Examine the floorplan and standard-cell placement.
- Observe clock-tree synthesis (CTS).
- Inspect the routed layout and metal interconnections.
- Analyze setup and hold timing.
- Examine worst negative slack (WNS) and total negative slack (TNS).
- Review reported power, area, and utilization.
- Understand the importance of timing closure in digital circuit implementation.

## Tools and Technology

| Component | Description |
|---|---|
| Physical Design Tool | OpenROAD |
| Technology Platform | SkyWater SKY130 HD |
| Timing Analysis | Static Timing Analysis (STA) |
| Design Flow | Floorplan, Placement, CTS, Routing, Post-Route STA |
| Timing Reports | Setup and Hold Analysis |
| Documentation | GitHub README and screenshots |

---

# 1. OpenROAD Physical Design Flow

The physical design flow consists of several stages. Each stage prepares the circuit for the next step of implementation.

The stages documented in this repository are:

1. Floorplanning
2. Placement
3. Clock-Tree Synthesis (CTS)
4. Routing
5. Post-Route Static Timing Analysis

---

# 2. Floorplanning

<img width="1522" height="782" alt="WhatsApp Image 2026-10-15 at 6 27 42 PM" src="https://github.com/user-attachments/assets/91de55f5-b02c-4faa-ac91-0c96e30d35d4" />

### Description

Floorplanning is the initial physical design stage in which the die area, core area, and basic placement region are established.

The screenshot shows the OpenROAD floorplan view with the design region and visible physical layers.

### Purpose

- Establish the physical boundaries of the design.
- Define the core area available for standard cells.
- Prepare the design for placement and routing.
- Provide the foundation for subsequent physical implementation stages.

### Observation

The OpenROAD GUI displays the floorplan database and the associated design layout.

---

# 3. Standard-Cell Placement

<img width="1502" height="786" alt="image" src="https://github.com/user-attachments/assets/6e03d395-4100-49b9-b377-f8e2d01a96f8" />

### Description

Placement determines the physical locations of standard cells inside the floorplan.

During this stage, the implementation tool arranges the cells while considering design constraints and physical implementation requirements.

### Purpose

- Position standard cells within the core.
- Improve placement quality.
- Estimate interconnect parasitics.
- Prepare the design for clock-tree synthesis and routing.

### Observation

The screenshot shows the design after the placement stage, identified as `3_place` in the OpenROAD flow.

The placement result provides the physical arrangement used by later implementation stages.

---

# 4. Clock-Tree Synthesis (CTS)

<img width="1510" height="788" alt="image" src="https://github.com/user-attachments/assets/a2d544d0-b4fb-4bb7-984c-c845de0af29d" />

### Description

Clock-Tree Synthesis creates the clock distribution network required to deliver clock signals to sequential elements such as registers and flip-flops.

The clock network must be designed to control clock delay and skew.

### Purpose

- Distribute the clock signal throughout the design.
- Insert clock buffers where required.
- Reduce clock skew.
- Prepare the design for detailed routing and timing analysis.

### Observation

The screenshot shows the design at the CTS stage, identified as `4_cts`.

The OpenROAD console also displays commands related to parasitic estimation and timing-report updates.

---

# 5. Routing

<img width="1510" height="784" alt="image" src="https://github.com/user-attachments/assets/d5cd6a30-1b87-4639-995c-686f2adc102f" />

### Description

Routing establishes the physical electrical connections between standard cells using the available metal layers and vias.

The routed layout contains interconnections across multiple metal layers.

### Purpose

- Connect the placed standard cells.
- Implement signal interconnections.
- Use metal layers and vias to establish connectivity.
- Account for physical interconnect effects during timing analysis.

### Observation

The screenshot shows a zoomed-in view of the routed design.

Different colors represent different physical routing layers in the OpenROAD GUI.

Routing is important because interconnect resistance and capacitance can affect circuit delay.

---

# 6. Post-Route Static Timing Analysis

Static Timing Analysis evaluates whether signals can propagate through the circuit within the timing requirements defined by the design constraints.

The following sections examine the timing paths shown in the supplied terminal screenshots.

---

## 6.1 Setup Timing Analysis: Register-to-Register Path

<img width="514" height="570" alt="image" src="https://github.com/user-attachments/assets/1b822df1-81fb-4f8d-aa13-668e7d37807a" />

### Description

This screenshot shows a maximum-delay timing path between sequential elements.

The path belongs to the `core_clock` timing group and includes clock-to-Q delay, combinational logic delay, and setup-time requirements.

### Reported Result

- Path type: Maximum delay
- Reported slack: Approximately `-1.45`
- Status: `VIOLATED`

### Interpretation

Setup timing checks whether data reaches the destination register before its required capture time.

Negative setup slack indicates that the reported path does not meet its setup timing requirement under the constraints used for this run.

### Conclusion

The displayed register-to-register path has a setup timing violation that requires further investigation.

---

## 6.2 Setup Timing Analysis: Register-to-Output Path

<img width="492" height="488" alt="image" src="https://github.com/user-attachments/assets/0b32203b-b740-40c8-bde3-76c5716a58b4" />

### Description

This screenshot shows a maximum-delay path from a register to the output port `resp_msg[3]`.

The path is associated with the `vclk_core_clock` timing group.

### Reported Result

- Path type: Maximum delay
- Reported slack: Approximately `-1.76`
- Status: `VIOLATED`

### Interpretation

Register-to-output timing analysis checks whether a signal reaches an output within the timing requirement defined by the relevant constraints.

The negative slack indicates that the reported path misses its required timing.

### Possible Areas for Investigation

- Output-delay constraints.
- Logic depth along the critical path.
- Cell delays.
- Interconnect delays.
- Clock relationships and timing constraints.

### Conclusion

The displayed register-to-output path has a setup timing violation.

---

## 6.3 Hold Timing Analysis

<img width="542" height="458" alt="image" src="https://github.com/user-attachments/assets/b720d09b-918e-45e1-bcb9-303aa603d2f4" />

### Description

Hold timing analysis verifies that data does not arrive too early at the destination register following the active clock edge.

This check is important for ensuring reliable sequential operation.

### Reported Result

- Path type: Minimum delay
- Reported slack: Approximately `+0.48`
- Status: `MET`

### Interpretation

Positive hold slack indicates that the displayed path meets its hold timing requirement.

### Conclusion

The hold check shown in this screenshot passes.

This result applies to the reported check and does not mean that all timing paths have passed.

---

## 6.4 Output Timing Check

<img width="492" height="488" alt="image" src="https://github.com/user-attachments/assets/17e31349-c3cf-4743-b022-2006fdb1bc41" />

### Description

This screenshot shows a minimum-delay timing path from a register to the output port `resp_val`.

### Reported Result

- Path type: Minimum delay
- Reported slack: Approximately `+1.06`
- Status: `MET`

### Interpretation

The displayed path meets the timing requirement under the constraints used in this run.

### Conclusion

The output timing check shown in this screenshot passes.

However, the positive slack in this minimum-delay path does not resolve the setup violations identified in the maximum-delay paths.

---

# 7. Post-Route STA Summary

<img width="594" height="617" alt="image" src="https://github.com/user-attachments/assets/070251da-7fd2-4517-989a-58db21c45b08" />

### Description

The post-route STA summary consolidates several important implementation metrics, including setup slack, hold slack, power, and design area.

The following values are transcribed from the supplied screenshot.

## 7.1 Timing Results

| Metric | Reported Value | Interpretation |
|---|---:|---|
| Worst Setup Slack | -1.762 | Setup timing violation |
| Worst Hold Slack | +0.479 | Positive worst hold slack |
| WNS (Setup) | -1.762 | Worst setup slack is negative |
| TNS (Setup) | -69.502 | Aggregate setup timing deficit |

### Timing Interpretation

**Worst Negative Slack (WNS)** represents the most negative setup slack reported for the analyzed design.

**Total Negative Slack (TNS)** represents the aggregate negative setup slack reported by the timing analysis.

The negative WNS and TNS indicate that setup timing closure has not been achieved in this run.

The positive worst hold slack indicates that the reported worst hold check has positive slack.

---

## 7.2 Power Results

The screenshot reports the following power values.

| Power Category | Reported Power |
|---|---:|
| Sequential | 1.75e-03 W |
| Combinational | 4.87e-03 W |
| Clock | 7.15e-04 W |
| Total | 7.34e-03 W |

### Interpretation

The reported total power is approximately **7.34 mW**.

The table separates the reported power into sequential, combinational, and clock-related components.

These values are the estimates displayed by the tool and should be interpreted according to the activity assumptions and analysis settings used in the run.

---

## 7.3 Area and Utilization

| Metric | Reported Value |
|---|---:|
| Design Area | 5029 µm² |
| Utilization | 84% |

### Interpretation

The screenshot reports a design area of approximately 5029 square micrometers and utilization of 84%.

These are the values displayed in the supplied report and refer to the implementation stage shown.

---

# 8. Overall Observations

The screenshots demonstrate the major physical implementation stages of the OpenROAD flow.

The following observations can be made from the supplied results:

1. The floorplanning stage establishes the physical design region.
2. Placement arranges standard cells within the available core area.
3. CTS prepares the clock distribution network for sequential elements.
4. Routing establishes the physical interconnections.
5. Post-route STA evaluates the timing behavior of the implemented design.
6. The displayed register-to-register setup path has negative slack.
7. The displayed register-to-output setup path also has negative slack.
8. The displayed hold timing checks have positive slack.
9. The summary reports negative setup WNS and TNS.
10. The report provides power, area, and utilization estimates for the implementation.

---

# 9. Conclusion

The physical design flow was examined using OpenROAD with the SkyWater SKY130 HD platform.

The repository documents floorplanning, standard-cell placement, clock-tree synthesis, routing, and post-route static timing analysis.

The timing screenshots show both setup and hold analysis. Although the displayed hold checks pass, the negative worst setup slack and total negative setup slack indicate that the design has not achieved setup timing closure in this run.

Further analysis of critical paths, timing constraints, cell delays, and interconnect parasitics would be required before claiming that the design meets all timing requirements.

The results provide a practical demonstration of how physical implementation and static timing analysis are used to evaluate a digital circuit.

---

# 10. Repository Structure

```text
openroad-sta-report/
│
├── README.md
│
└── images/
    ├── 01_floorplan.png
    ├── 02_placement.png
    ├── 03_clock_tree_synthesis_cts.png
    ├── 04_routing.png
    ├── 05_setup_timing_internal_path.png
    ├── 06_setup_timing_output_path.png
    ├── 07_hold_timing.png
    ├── 08_output_timing_check.png
    └── 09_post_route_sta_summary.png
```

---

## Notes

- This documentation is based on the screenshots supplied for this run.
- Timing units and constraints should be verified against the actual timing reports and SDC files before using the values for sign-off.
- These screenshots alone do not demonstrate that STA has been completed for every process, voltage, and temperature corner.
- The reported setup violations should be investigated before declaring timing closure.
