
---

# `04-Library-Binding-and-Placement.md`

```markdown
# 04 — Library Binding and Placement

## 📌 Introduction

After floorplanning and power planning, standard cells must be assigned physical locations.

Placement determines where the cells from the synthesized netlist are positioned inside the core.

Library information is essential because the physical and timing properties of cells must be known.

---

## 📚 Need for Libraries

A digital ASIC design uses many standard cells.

The implementation tools need information about each cell's:

- Logical function
- Physical dimensions
- Pin locations
- Timing characteristics
- Capacitance
- Power characteristics

This information is provided through technology libraries.

---

## 🔗 Library Binding

Library binding connects logical cells in the design with technology-specific physical cells.

For example:

```text
Logical Inverter
       ↓
sky130_fd_sc_hd__inv_2
