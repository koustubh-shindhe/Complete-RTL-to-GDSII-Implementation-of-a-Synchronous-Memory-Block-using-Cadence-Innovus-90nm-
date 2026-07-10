## Project Overview
I worked on this project during the ASIC Physical Design training program at Nitte Meenakshi Institute of Technology (NMIT), Bengaluru. The objective of this project was to understand and implement the complete Physical Design flow of a Synchronous Memory Block using Cadence Innovus on a 90nm technology node.

Through this project, I gained hands-on experience in every stage of the backend design flow, starting from importing the synthesized netlist and ending with the final GDSII generation. It helped me understand how timing, power planning, placement, routing, and physical verification are handled in an actual ASIC implementation flow.

One of the main goals of this project was to close timing without any setup or hold violations and to make sure the design was physically clean. After completing the flow, I was able to achieve zero DRC violations, zero connectivity violations, and zero power-grid shorts at the worst-case corner (SS, 0.9V, 125°C).

## Backend Flow 

- Design Setup and Import
- Floorplanning
- Power Planning
- Standard Cell Placement
- Clock Tree Synthesis (CTS)
- Post-CTS Optimization
- Routing
- Physical Verification
- GDSII Stream-Out

## Design Information

## Design Specifications

| Parameter | Value |
|-----------|--------|
| Design Name | memory |
| Design Type | Synchronous Memory Block |
| Technology Node | 90nm |
| Supply Voltage | 0.9V |
| PVT Corner | SS, 0.9V, 125°C |
| Implementation Tool | Cadence Innovus 21.15 |
| Synthesis Tool | Cadence Genus |
| Analysis Mode | MMMC |
| Metal Layers Used | M1-M6 |
| Setup View | func_ss |
| Hold View | func_ff |


# Physical Design Flow
```text
Synthesized Netlist
        │
        ▼
1. Design Setup & Import
        │
        ▼
2. Floorplanning
        │
        ▼
3. Power Planning
        │
        ▼
4. Placement
        │
        ▼
5. Clock Tree Synthesis (CTS)
        │
        ▼
6. Post-CTS Optimization
        ▼
7. Routing
        │
        ▼
8. Physical Verification
        │
        ▼
9. GDSII Stream-Out

```

# Stage-by-Stage Implementation

## 1. Design Setup and Import

The physical design flow started by importing the synthesized netlist generated from Cadence Genus into Innovus. Along with the netlist, all the required technology and timing files were loaded to set up the design environment.

### Inputs Used
- Synthesized netlist (`memory.v`)
- Technology LEF and standard cell LEF
- Liberty timing libraries (LVT cells)
- SDC constraints
- MMMC setup files (`func_ss` and `func_ff`)

### Design Environment

| Property | Value |
|----------|--------|
| Operating Condition | PVT_0P9V_125C |
| Voltage | 0.900 V |
| Temperature | 125°C |
| Analysis Mode | Worst Case |
| Max Transition | 0.280 ns |

---

## 2. Floorplanning

The die boundary and core area were defined before placement. Standard cell rows were created and I/O pins were distributed around the edges of the die.

### Activities Performed
- Core and die area definition
- Standard cell row creation
- I/O pin placement
- Utilization planning

**Outcome:** A clean floorplan with sufficient routing resources and minimal congestion.

---

## 3. Power Planning

A power delivery network was implemented to provide reliable VDD and VSS distribution throughout the design.

### Structures Created
- Core power rings
- Internal power stripes
- Power connectivity checks

**Result:** Power planning completed successfully without warnings or errors.

---

## 4. Placement

Standard cell placement was performed using the Cadence GigaPlace engine with timing-driven optimization enabled.

### Placement Summary

| Metric | Value |
|--------|--------|
| Cell Density | 53.253% |
| Routing Overflow | 0.00% |
| Total Paths | 290 |

### Timing Summary

| Analysis Mode | WNS (ns) | TNS (ns) | Violating Paths |
|--------------|-----------|-----------|----------------|
| all | 0.804 | 0.000 | 0 |
| reg2reg | 2.259 | 0.000 | 0 |

---

## 5. Clock Tree Synthesis (CTS)

Clock Tree Synthesis was performed using the CCOpt engine to distribute the clock signal with minimum skew and balanced latency.

### CTS Results

| Metric | Value |
|--------|--------|
| Clock Skew | 0.015 ns |
| Maximum Latency | 0.179 ns |
| Minimum Latency | 0.164 ns |
| Clock Domain | mclk |

The generated clock tree used multiple clock buffers to achieve balanced clock distribution across all sequential elements.

---

## 6. Post-CTS Optimization

Additional optimization passes were executed after CTS to improve timing and eliminate hold violations.

### Hold Fix Summary

| Metric | Before | After |
|---------|---------|-------|
| Hold Violations | 3 | 0 |
| Hold WNS | -0.000 ns | 0.000 ns |

### Timing Summary

| Analysis Mode | WNS (ns) | TNS (ns) | Violating Paths |
|--------------|-----------|-----------|----------------|
| Setup | 1.407 | 0.000 | 0 |
| Hold | 0.000 | 0.000 | 0 |

---

## 7. Routing

Detailed routing was completed using NanoRoute. All nets were successfully connected across the available metal layers.

### Routing Summary

| Metric | Value |
|--------|--------|
| Nets Routed | 2664 |
| Horizontal Overflow | 0.00% |
| Vertical Overflow | 0.00% |
| Open Nets | 0 |
| Metal Layers | M1-M6 |

### Post-Route Timing

| Analysis Mode | WNS (ns) | TNS (ns) | Violating Paths |
|--------------|-----------|-----------|----------------|
| Setup | 0.927 | 0.000 | 0 |
| Hold | 0.000 | 0.000 | 0 |

---

## 8. Physical Verification

After routing, signoff verification checks were performed.

### Verification Results

| Check | Result |
|--------|---------|
| DRC | 0 Violations |
| PG Short | 0 Violations |
| Connectivity | 0 Violations |

The final database was completely clean and ready for stream-out.

---

## 9. GDSII Generation

After achieving timing closure and passing all verification checks, the final layout was exported as a GDSII file.

| Parameter | Value |
|-----------|--------|
| Output File | final.gds |
| Design Name | memory |
| Die Size | 83.6 µm × 82.08 µm |
| Database Units | 2000 |
