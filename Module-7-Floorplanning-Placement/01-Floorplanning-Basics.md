
---

# `01-Floorplanning-Basics.md`

```markdown
# 01 — Floorplanning Basics

## 📌 Introduction

Floorplanning is one of the first major stages of physical design.

It determines the physical dimensions and initial organization of the chip.

A good floorplan improves placement, routing, timing and power distribution.

A poor floorplan can create congestion, long interconnects and timing problems.

---

## 🏗️ What is Floorplanning?

Floorplanning determines:

- Die dimensions
- Core dimensions
- Aspect ratio
- Utilization
- Macro locations
- I/O pin locations
- Placement regions

The floorplan provides the physical foundation for the remaining design stages.

---

## 📐 Utilization Factor

Utilization factor indicates how much of the available core area is occupied by cells.

It can be expressed as:

```text
Utilization =
Area occupied by cells / Total available core area
