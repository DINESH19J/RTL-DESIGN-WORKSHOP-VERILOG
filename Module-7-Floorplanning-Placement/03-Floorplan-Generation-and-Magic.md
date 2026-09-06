
---

# `03-Floorplan-Generation-and-Magic.md`

```markdown
# 03 — Floorplan Generation and Magic

## 📌 Introduction

After understanding floorplanning concepts, the next step is to generate and inspect the floorplan using the physical-design flow.

OpenLANE can automate floorplan generation.

The generated layout information can then be inspected using layout tools such as Magic.

---

## ▶️ Running Floorplan

After design preparation, the floorplan stage can be executed using OpenLANE.

A typical command is:

```tcl
run_floorplan
