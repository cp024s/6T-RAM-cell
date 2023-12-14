# 6T RAM CELL DESIGN USING SKY 130 PDK

The 6T SRAM (Static Random Access Memory) cell is a fundamental building block of SRAM memory arrays widely used in integrated circuits. It consists of six transistors arranged in a cross-coupled flip-flop configuration. The 6T SRAM cell is known for its stability, simplicity, and fast access times. Here's a brief overview of its structure and operation:

## 1. Construction

1. **Cross-Coupled Inverters:** The heart of the 6T SRAM cell comprises two inverters, typically formed by four transistors (two NMOS and two PMOS). These inverters are connected in a feedback loop, creating a bistable element that can store a binary state (0 or 1).

2. **Access Transistors:** Two additional transistors serve as access transistors. These are used to connect the flip-flop to the bitlines during read and write operations. The bitlines are the pathways through which data is read from or written to the SRAM cell.


## 2. Working 

**2.1 Standby Mode (Idle Circuit):**  
    During standby mode, when the word line is not asserted (word line = 0), the pass transistors N3 and N4 connecting the 6T cell to the bit lines are turned off, preventing cell access. The cross-coupled inverters formed by N1-N2 continuously feed back, maintaining data in the latch as long as they are connected to the power supply.

**2.2 Read Mode (Data Requested):**  
    In read mode, the word line is asserted (word line = 1), enabling both access transistors to connect the cell to the bit lines. The values stored in nodes (node a and b) are transferred to the bit lines. If a logical 1 is stored at node a, the bit line bar discharges through the driver transistor (N1), and the bit line is pulled up through the load transistors (P1) toward VDD, representing a logical 1. The design of the SRAM cell ensures read stability to avoid data disturbance during reading.

**2.3 Write Mode (Updating Contents):**  
    In the write mode, assuming the cell originally stores a 1 and we want to write a 0, the bit line is lowered to 0V, and bit bar is raised to VDD. The cell is selected by raising the word line to VDD. The inverters are typically designed with matched PMOS and NMOS to maintain an inverter threshold at VDD/2. If writing a 0 at node a is desired, N3 operates in saturation. Initially, its source voltage is 1, and the drain terminal of N2 is pulled down by N3 because access transistor N3 is stronger than N1. As a result, N2 turns on, P1 turns off, and a new value is written, forcing the bit line to lower to 0V and bit bar to rise to VDD. For write mode operation, SRAM must have writeability, which is the minimum bit line voltage required to flip the cell's state.
