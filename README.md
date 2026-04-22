
# 2×2 🧊 Systolic Array for Matrix–Matrix Multiplication
<img width="2816" height="1536" alt="Gemini_Generated_Image_9on7ds9on7ds9on7" src="https://github.com/user-attachments/assets/604e7e2c-69b1-4f07-ad89-2ac3f7c8ff39" />

A fully transistor-level, static CMOS implementation of a 2×2 Systolic Array for matrix multiplication, designed and verified in Cadence Virtuoso.

### Overview

SystolicMM is a ground-up, transistor-level implementation of a 2×2 Systolic Array for performing matrix–matrix multiplication. The entire design was built using static CMOS methodology inside Cadence Virtuoso, starting from individual NMOS/PMOS transistors and composing them into logic gates, adders, a 4-bit array multiplier, registers, and finally four interconnected Processing Elements (PEs).

The array accepts two 4-bit input matrices and produces 12-bit output values representing the four elements of the result matrix, all verified via transient simulation.

<img width="530" height="145" alt="Screenshot 2026-04-22 at 15 09 10" src="https://github.com/user-attachments/assets/3312c2b5-1c1c-42ca-9dee-dbd009999898" />

This project explores the design and implementation of a **2x2 Systolic Array**, a specialized hardware architecture optimized for high-throughput matrix operations. 

By utilizing parallel Processing Elements (PEs) and a pipelined data flow, this design overcomes the "von Neumann bottleneck," making it ideal for accelerating **Deep Learning** workloads and **Digital Signal Processing (DSP)** tasks.  

### Objectives
* Implement a scalable 2x2 grid of Processing Elements.
* Design high-speed 4-bit multipliers and 11-bit accumulators.
* Optimize power and stability using Static CMOS logic.
* Validate performance through transient analysis of complex matrix products.

### Architecture
* **Grid Size**: 2x2 (4 Processing Elements).
* **Data Flow**: 
    * Inputs ($A$) propagate horizontally.
    * Weights ($B$) propagate vertically.
    * Partial sums are accumulated locally within each PE.
* **Timing**: Interleaved data entry to ensure synchronized MAC operations.

### Hardware Specifications
* **Logic Style**: Static CMOS (4-pin transistors with body biasing).
* **Transistor Sizing**: $W = 1.5\mu m$, $L = 600nm$.
* **Clocking**: $1MHz$ frequency ($10\mu s$ period) with $500fs$ transition times.
* **Registers**: Negative-edge triggered D Flip-Flops for stable data latching.

### Component Breakdown

The system is built hierarchically from the transistor level up:

✅ **MAC Units**: 4-bit array multiplier + cascaded full adders.

✅ **Storage**: 4-bit input/weight registers and 12-bit output registers.

✅ **Arithmetic**: 11-bit precision to prevent overflow during accumulation.

✅ **Primitives**: Custom-designed NAND, OR, and Inverter gates.

### Design Details
| Parameter | Value |
| :--- | :--- |
| Technology | Cadence Virtuoso (Static CMOS) |
| Precision | 4-bit Input / 12-bit Output |
| Clock Pulse | $5\mu s$ (50% Duty Cycle) |
| Latency | Pipelined output delivery |
| Methodology | Bottom-Up VLSI Design |

### 📊 Results
The array was verified using the matrix product $(12, 11) \times (9, 15)$:

- **Test Case**: $A_{11}=12$, $B_{11}=9$
- **Expected Output**: $108$
- **Measured Output**: `01101100` (Binary 108)
- **Signal Integrity**: Waveform analysis confirmed clean switching and stable hold times at $1MHz$.

### put pictures here

### Learned Engineering Principles
* **Parallelism vs. Serialism**: Drastic reduction in clock cycles compared to standard CPUs.
* **Structural Pipelining**: Efficient use of registers to prevent data collisions.
* **Transistor Sizing**: Balancing $W/L$ ratios to meet specific timing constraints.
* **Fan-out Management**: Ensuring signal strength across cascaded adder stages.

### Future Work
Scaling: Expansion to an $8 \times 8$ or $16 \times 16$ array.
Low Power: Implementation of clock gating to reduce dynamic power consumption.Advanced Logic: Exploring Transmission Gate Logic for more compact multiplexing.Integration: Interfacing with an FPGA for real-world hardware validation.

### 👥 Authors
Denzel Bullen
Isabella Opoku-Ware
