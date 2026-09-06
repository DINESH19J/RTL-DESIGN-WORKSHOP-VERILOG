
---

# `02-Preplaced-Cells-Power-and-Pins.md`

```markdown
# 02 — Pre-Placed Cells, Power Planning and Pin Placement

## 📌 Introduction

Physical design includes several important considerations before standard-cell placement.

Pre-placed cells, power distribution, I/O pin locations and placement blockages must be considered carefully.

These factors influence wire length, congestion, timing and routability.

---

## 🧩 Pre-Placed Cells

Some blocks must be placed at fixed locations before standard-cell placement.

These are called pre-placed cells or pre-placed blocks.

Examples can include:

- Memory macros
- Analog blocks
- IP blocks
- Large functional macros

Their positions are generally fixed during standard-cell placement.

---

## 📍 Why Pre-Placement is Important

Pre-placed macros influence the available space for standard cells.

Poor macro placement can create:

- Routing congestion
- Long connections
- Narrow routing channels
- Timing problems

Therefore, macro locations should be selected carefully.

---

## ⚡ Decoupling Capacitors

Decoupling capacitors help stabilize the local power supply.

When a circuit switches rapidly, it can cause temporary variations in supply voltage.

A decoupling capacitor can provide local charge during such transient events.

Conceptually:

```text
VDD
 |
 +---- Decoupling Capacitor
 |
GND
