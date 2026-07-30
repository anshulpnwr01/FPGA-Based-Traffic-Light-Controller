# FPGA-Based Traffic Light Controller

![Badges](https://img.shields.io/badge/HDL-Verilog-blue) ![Badges](https://img.shields.io/badge/Domain-VLSI-orange) ![Badges](https://img.shields.io/badge/Design-RTL-green) ![Badges](https://img.shields.io/badge/Architecture-FSM-red) ![Badges](https://img.shields.io/badge/Verification-Testbench-purple) ![Badges](https://img.shields.io/badge/Waveform-GTKWave-yellow) ![Badges](https://img.shields.io/badge/Status-Complete-brightgreen)

## About
FPGA-Based Traffic Light Controller using Verilog HDL and Finite State Machine (FSM). Features include pedestrian crossing support, emergency vehicle priority, night mode operation, waveform verification, and FPGA-ready implementation.

## Repository Structure
As shown in the repository overview, the project is organized into the following directories:
* `rtl/`: Contains the core Verilog design files (e.g., `traffic_fsm.v`).
* `tb/`: Contains the testbench files for simulation and verification.
* `simulation/` & `waveforms/`: Stores simulation scripts and GTKWave waveform outputs.
* `dashboard/`: Contains the software model for the interactive UI.
* `docs/` & `images/`: Project documentation and reference images.

![GitHub Repository Overview](WhatsApp%20Image%202026-07-28%20at%2011.19.25%20PM.jpeg)

---

## Interactive Controller Dashboard
The project features a software model of the traffic cabinet (operating in a 10 Hz tick domain) to visualize the intersection and interact with the controller logic without requiring physical FPGA hardware immediately.

![Traffic Light Dashboard](WhatsApp%20Image%202026-07-28%20at%2011.19.24%20PM%20(1).jpeg)

### Demand Inputs & Pre-emption
The control logic responds dynamically to several inputs simulating real-world traffic conditions:

![Controller Cabinet Inputs](WhatsApp%20Image%202026-07-28%20at%2011.19.26%20PM.jpeg)

* **`veh_ns` (North-South loop sensor):** Detects waiting vehicles on the main axis.
* **`veh_ew` (East-West loop sensor):** Detects waiting vehicles on the cross-axis.
* **`ped_btn` (Pedestrian Button):** Latches a WALK request for safe crossing.
* **`emergency` (Pre-emption):** Forces an all-red state for standard traffic, holding the priority open for emergency vehicles.
* **`night_mode` (Pre-emption):** Switches the intersection to a low-traffic flashing amber/red state.
* **`rst_n`:** Resets the controller state to its default parameters.

---

## Simulation and Waveform Verification
The RTL design is fully verified using testbenches. The state changes, phase timers, and control signals (`EW_G`, `NS_R`, etc.) can be analyzed using a waveform viewer (such as GTKWave). 

Below are snapshots from the simulation environment tracking the internal registers (`STATE_ID`, `prev_state`) and the corresponding output signals based on the demand inputs:

![Simulation Waveform 1](WhatsApp%20Image%202026-07-28%20at%2011.19.24%20PM.jpeg)

![Simulation Waveform 2](WhatsApp%20Image%202026-07-28%20at%2011.19.25%20PM%20(1).jpeg)

## Getting Started
To simulate this project locally:
1. Clone the repository.
2. Navigate to the `simulation` folder.
3. Run the provided simulation scripts (ensure you have a Verilog simulator and GTKWave installed).
4. Launch the dashboard to interact with the FSM visually.
