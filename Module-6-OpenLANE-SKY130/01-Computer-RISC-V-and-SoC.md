
---

# `01-Computer-RISC-V-and-SoC.md`

```markdown
# 01 — Computer, RISC-V and SoC Fundamentals

## 📌 Introduction

Understanding computer architecture is the first step towards understanding digital ASIC design.

A computer executes instructions using digital hardware implemented with logic gates and transistors.

Software applications are converted into machine instructions that can be understood by a processor.

The processor follows an Instruction Set Architecture (ISA) to execute these instructions.

RISC-V is an open Instruction Set Architecture based on the RISC philosophy.

This section explains the relationship between software, instructions, processors and hardware.

---

## 💻 How Do We Talk to Computers?

Computers ultimately process binary information represented using 0s and 1s.

A programmer writes instructions using a high-level programming language.

A compiler converts the program into lower-level machine instructions.

The processor fetches, decodes and executes these instructions.

The hardware performs the required operations using digital logic.

The simplified path is:

```text
Application
    ↓
Programming Language
    ↓
Compiler
    ↓
Machine Instructions
    ↓
Processor
    ↓
Digital Logic
    ↓
Transistors
