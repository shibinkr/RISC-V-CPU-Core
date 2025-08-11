# Introduction

This chapter introduces you to basic circuit design in the **Makerchip IDE**, laying the groundwork for understanding core digital logic concepts and demonstrating how to implement them using **TL-Verilog** within the Makerchip environment.

## 1.1 Logical Gate Basics

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


## 1.2 TL-Verilog File Structure in Makerchip

### 1. File Type and Module Requirement
- Supported file types:
  - **Verilog (.v)**
  - **SystemVerilog (.sv)**
  - **TL-Verilog (.tlv)**
- Makerchip **requires** a `top` module with:
  - Inputs: `clk`, `reset`
  - Outputs: `passed`, `failed`
- If you use only Verilog/SystemVerilog:
  - Makerchip’s TLV-specific navigation/debug features won’t work.
  - No diagrams will be generated.

### 2. First Line – Version Declaration

**Example:**
```verilog
\m4_TLV_version 1d: tl-x.org
```
- **Purpose:** Declares TL-Verilog syntax version (`1d` here).
- **`m4_` prefix:** Tells Makerchip to preprocess code with the **M4 macro processor**.
- **`tl-x.org`:** URL for TL-Verilog reference.
- In Makerchip’s **“Nav TLV”** pane:
  - `m4_` prefix is stripped.
  - You see the final expanded TLV code.

### 3. Second Line – Entering SystemVerilog Context

**Example:**
```verilog
\SV
```
- Switches the file to **SystemVerilog mode**.
- **Used for:**
    - Type declarations
    - Module parameters
    - Defining the `top` module interface

- The **`m4_makerchip_module`** macro is used at the end of this section to create `module top(...)`.
- Expanded result is visible in the **“Nav TLV”** pane.

### 4. TL-Verilog Module Body

**Example:**
```verilog
\TLV
```
- Switches to **TL-Verilog context**.

- **Write:**
    - Pipelines
    - Logic
    - TL-specific constructs
- Can switch back to `\SV` at the end to close the module.

### 5. Optional SystemVerilog Helper Modules


Additional modules (test benches, utilities) can be written in `\SV` context after the main module.

### 6. Typical Makerchip TL-Verilog File Layout

```verilog
\m4_TLV_version 1d: tl-x.org    // Required version declaration

\SV
// SystemVerilog: module interface, parameters, ports
m4_makerchip_module             // Macro to generate 'module top(...)'

\TLV
// TL-Verilog: pipeline stages, logic

\SV
// End of module
endmodule

// Optional: SystemVerilog helper modules
```

### 7. Visual Flow of a Typical TL-Verilog File


```text
┌──────────────────────────────┐
│ \SV                          │
│ SystemVerilog context        │
│ - Define module interface    │
│ - Declare parameters & ports │
└───────────────┬──────────────┘
                │
                ▼
┌──────────────────────────────┐
│ \TLV                         │
│ TL-Verilog context           │
│ - Pipelines                  │
│ - Logic                      │
│ - Timing abstraction         │
└───────────────┬──────────────┘
                │
                ▼
┌──────────────────────────────┐
│ \SV                          │
│ SystemVerilog context        │
│ - Close module               │
│ - Optional helper modules    │
└──────────────────────────────┘
```
### Step Summary

- `\SV` – Start in SystemVerilog for module interface & ports.
- `\TLV` – Write TL-Verilog logic and pipelines.
- `\SV` – Close the module, add optional helper modules.


