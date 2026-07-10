This folder contains screenshots captured during different stages of the **RTL-to-GDSII implementation of a Synchronous Memory Block using Cadence Innovus on a 90nm technology node**.

The screenshots provide a visual representation of the **complete backend Physical Design flow**, including **floorplanning, power planning, placement, clock tree synthesis, routing, physical verification, and final GDSII generation**.
# Screenshots

The following screenshots highlight the key stages of the RTL-to-GDSII implementation flow.

## 1. Floorplan + Power Planning
Core area definition along with VDD and VSS power rings and stripes.

![Floorplan](03_floorplan_global.png.png)

![Power Plan](05_power_plan_global.png.png)

---

## 2. Placement - Global View
Standard cells placed across the core with optimized utilization and zero routing overflow.

![Placement Global](07_placement_global.png.png)

---

## 3. Placement - Zoomed View
Zoomed view showing standard cell instances and placement quality.

![Placement Zoomed](08_placement_zoomed.png.png)

---

## 4. Congestion Analysis
Routing congestion map showing available routing resources and overflow information.

![Congestion Map](09_congestion_map.png.png)

---

## 5. Clock Tree Synthesis (CTS)
Balanced clock tree generated using CCOpt for minimum skew and optimized latency.

![Clock Tree](12_cts_clock_tree.png.png)

---

## 6. Post-CTS Timing Results
Timing summary after setup and hold optimization.

![Post CTS Timing](15_postcts_timing_report.png.png)

---

## 7. Routed Layout - Global View
Complete routed layout showing metal interconnections across the entire design.

![Routing Global](18_routing_global.png.png)

---

## 8. Routed Layout - Zoomed View
Detailed routing view showing metal layers and via connections.

![Routing Zoomed](19_routing_zoomed.png.png)

---

## 9. Physical Verification
Verification reports confirming zero DRC violations, zero connectivity violations, and zero PG short violations.

![Verification](26_verification_summary.png.png)

---

## 10. Final Layout
Final layout after successful timing closure and physical verification.

![Final Layout](28_final_layout_global.png.png)

---

## 11. Final GDSII Layout
Final GDSII stream file generated after completing the RTL-to-GDSII implementation flow.

![GDSII](30_final_gdsii_view.png.png)
