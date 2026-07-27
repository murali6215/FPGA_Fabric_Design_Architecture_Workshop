# DAY 5 - RISCV Core on Custom SOFA Fabric

The RVMYTH RISC-V core was integrated with the custom SOFA FPGA fabric and executed through the complete OpenFPGA and VTR flow. The implementation generated various timing, utilization, routing, and simulation reports which were analyzed to verify the correctness of the design and FPGA mapping process.

---

# SOFA RVMYTH Utilization Report

The utilization report shows the FPGA resource usage of the RVMYTH core after synthesis and mapping onto the SOFA FPGA architecture.

The design consumes LUTs, latches, CLBs, routing resources, and logic elements. This report helps in understanding the hardware cost of implementing the processor core on the FPGA fabric.

## Circuit Statistics

<img width="330" height="182" alt="WhatsApp Image 2026-07-19 at 3 13 35 PM" src="https://github.com/user-attachments/assets/9a07c834-feff-4357-841a-f9269b5e061a" />

## Timing Graph

<img width="540" height="505" alt="WhatsApp Image 2026-07-19 at 3 16 23 PM" src="https://github.com/user-attachments/assets/42a7e6c2-0dfb-470e-bfd9-ea553b64f51c" />


*Detailed FPGA primitive block usage and logic element statistics for the RVMYTH implementation.*

---

# Constraints File

An SDC (Synopsys Design Constraints) file was created to define the clock timing constraints for the design.

## Constraint File Used

```tcl
create_clock -period 200 clk
set_input_delay -clock clk -max 0 [get_ports {*}]
set_output_delay -clock clk -max 0 [get_ports {*}]
```

The constraint file defines:

- Clock period
- Input delay constraints
- Output delay constraints

These constraints are used by the timing analysis engine during placement and routing.

---

# Timing Analysis

Timing analysis was performed after placement and routing to verify whether the design satisfies setup and hold timing constraints.

The setup timing report shows that the data arrival time is within the required timing limits and timing slack is positive.

<img width="1000" height="491" alt="WhatsApp Image 2026-07-19 at 3 56 54 PM" src="https://github.com/user-attachments/assets/07f652b7-5a27-4795-8ce2-0bb5d497c9ab" />


*Setup timing analysis report showing positive timing slack for the RVMYTH core.*

---

# Hold Timing Analysis

Hold timing analysis verifies that the data remains stable for the required duration after the clock edge.

<img width="942" height="578" alt="WhatsApp Image 2026-07-19 at 3 59 02 PM" src="https://github.com/user-attachments/assets/5f942aa4-136c-4651-b4e9-5b761438ec98" />


*Hold timing analysis report showing successful hold timing closure.*

---

# Post Implementation Simulation

Post implementation simulation was performed after synthesis, placement, and routing of the RVMYTH core.

The generated waveform confirms the correct execution of the processor logic after FPGA implementation. The simulation validates that the synthesized and routed netlist behaves correctly under the given clock and reset conditions.

The waveform also demonstrates proper output transitions and stable processor execution after implementation.


<img width="1268" height="572" alt="WhatsApp Image 2026-07-19 at 8 41 49 PM" src="https://github.com/user-attachments/assets/053c0cf1-a6f2-4adf-a22b-cb4df705af47" />


*Post implementation simulation waveform of the RVMYTH core on SOFA FPGA fabric.*

---

# Observations

- The RVMYTH processor was successfully mapped onto the custom SOFA FPGA fabric.
- FPGA resource utilization increased significantly compared to smaller counter-based designs.
- Timing constraints were successfully met with positive setup and hold slack values.
- The OpenFPGA and VTR flow successfully generated all required reports and simulation outputs.
- Post implementation simulation verified the correctness of the synthesized FPGA netlist.

---

# Conclusion

The RVMYTH RISC-V core was successfully implemented on the custom SOFA FPGA architecture using the OpenFPGA and VTR framework. The generated utilization reports, timing analysis, and simulation waveforms confirm that the processor operates correctly on the FPGA fabric while satisfying all timing constraints.

This experiment demonstrated the complete FPGA implementation flow starting from RTL design to post implementation verification using an open-source FPGA toolchain.
