
---

# `05-Synthesis-and-Synthesis-Results.md`

```markdown
# 05 — Synthesis and Synthesis Result Analysis

## 📌 Introduction

Synthesis converts RTL into a gate-level netlist using cells available in the selected technology library.

It is one of the most important stages between RTL design and physical implementation.

This section covers synthesis, logic optimization, technology mapping and synthesis result analysis.

---

## 🔄 Synthesis Flow

The simplified synthesis process is:

```text
RTL
 ↓
Elaboration
 ↓
Logic Optimization
 ↓
Technology Mapping
 ↓
Gate-Level Netlist
