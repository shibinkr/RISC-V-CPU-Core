# Introduction

This chapter introduces you to basic circuit design in the **Makerchip IDE**, laying the groundwork for understanding core digital logic concepts and demonstrating how to implement them using **TL-Verilog** within the Makerchip environment.

## Logical Gate Basics

- In digital circuits, wires settle at one of two voltage levels:
  - High voltage (VDD)
  - Low voltage (VSS or ground)
- These voltages represent boolean values:
  - High voltage = 1, true, on, asserted
  - Low voltage = 0, false, off, deasserted
- This binary representation provides a clear and simple way to represent data.
- It forms the basis for building more complex logic functions.
- This abstraction ensures predictable behavior in digital circuit design.


| A | B | NOT A | A AND B | A OR B | A NAND B | A NOR B | A XOR B | A XNOR B |
|---|---|-------|---------|--------|----------|---------|---------|----------|
| 0 | 0 |   1   |    0    |   0    |    1     |    1    |    0    |    1     |
| 0 | 1 |   1   |    0    |   1    |    1     |    0    |    1    |    0     |
| 1 | 0 |   0   |    0    |   1    |    1     |    0    |    1    |    0     |
| 1 | 1 |   0   |    1    |   1    |    0     |    0    |    0    |    1     |

