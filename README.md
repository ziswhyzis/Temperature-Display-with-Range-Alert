# 🌡️ Temperature Display with Range Alert

Welcome to the repository for my Digital Logic Design course project! This project focuses on designing a hardware-level temperature monitoring and warning system strictly using foundational logic gates.

## 📋 Project Overview

The objective was to design a combinational logic circuit that processes a 4-bit binary input representing a temperature reading (from $0^\circ$C to $15^\circ$C) and provides two specific outputs:
1.  **Hexadecimal Display:** The current temperature is displayed in Hex format (`0`-`F`) on a 7-segment display.
2.  **Range Alert:** A separate "Warning" LED activates 🚨 if the temperature falls **outside** the safe operating range of $5^\circ$C to $12^\circ$C (inclusive).

**Allowed Components:** `AND`, `OR`, `NOT`, `NAND`, `NOR`, `XOR`, `X-NOR` basic gates only.

### 💡 Sample Input-Output
* **Input:** `1111` ($15^\circ$C) ➡️ **Output:** Warning = `1` (ON), Display = `F`
* **Input:** `0111` ($7^\circ$C)  ➡️ **Output:** Warning = `0` (OFF), Display = `7`

---

## ⚙️ Design & Optimization Strategy

To achieve this using *only* basic gates, the design process followed a rigorous Boolean simplification and optimization pipeline:

1.  **Truth Table Generation:** Mapped all 16 possible 4-bit inputs (0000 to 1111) to their corresponding 7-segment outputs (A through G) and the Warning LED state.
2.  **Karnaugh Map (K-map) Simplification:** Derived optimized Sum-of-Products (SOP) expressions for all 8 outputs to minimize the logic footprint.
3.  **🚀 Architectural Optimization (The Common Gate Bus):**
    Because we were restricted to basic gates, implementing each boolean expression independently would lead to massive redundancy and wiring chaos.
    * **The Solution:** By analyzing the K-map equations, we identified recurring product terms (e.g., $A'B$, $CD$, $A'C'D'$).
    * We designed a **"Common Gate Bus"** consisting of 9 shared `AND` gate configurations. 
    * Instead of rebuilding these terms for every segment, the shared `AND` bus calculates them once. The specific `OR` / `XOR` gates for each segment then simply tap into this centralized bus. This drastically reduced the total gate count and resulted in a clean, professional circuit layout.

---

## 💻 Virtual Simulation

You can interact with the live virtual simulation of the optimized circuit on CircuitVerse! Toggle the 4-bit inputs to see the 7-segment display and Warning LED react in real-time.

🔗 **[Run the Simulation on CircuitVerse](https://circuitverse.org/simulator/embed/260-project-a4f231cb-ac64-4c75-9501-5ff4ad8094b7)**

---

## 🛠️ Tools Used
* **Logic Simplification:** Karnaugh Maps (K-maps)
* **Simulation & Design:** CircuitVerse
* **Core Logic:** Combinational Digital Logic Design

