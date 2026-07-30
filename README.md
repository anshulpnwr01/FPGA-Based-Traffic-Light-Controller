# FPGA-Based Traffic Light Controller

## Overview
This repository contains the comprehensive documentation for an **FPGA-Based Traffic Light Controller**.[cite: 2] The core control logic is implemented using a Finite State Machine (FSM) written in Verilog HDL.[cite: 2] 

![GitHub Repository Overview](WhatsApp%20Image%202026-07-28%20at%2011.19.25%20PM.jpeg)

To view the complete design diagrams, code snippets, and system architecture, please refer to the uploaded document: **fpga traffic light controller with priority system_2.pdf**.

## Project Description
The project simulates a real-world intersection traffic management system, complete with a software model of a controller cabinet dashboard.[cite: 2] The system is built to be hardware-deployable (FPGA-ready) and supports waveform verification to ensure accurate logic behavior before deployment.[cite: 2]

![Traffic Light Dashboard](WhatsApp%20Image%202026-07-28%20at%2011.19.24%20PM%20(1).jpeg)

### 1. Finite State Machine (FSM) Architecture
The traffic controller relies on a synchronous, clock-driven FSM (`clk` signal) to safely manage intersection traffic.[cite: 2] 
* **State Tracking:** The system uses a 4-bit register for the current state (`STATE [3:0]`) and keeps track of the preceding state using a `prev_state [3:0]` register.[cite: 2]
* **Phase Timing:** A dedicated phase timer ensures each state runs for the appropriate duration before transitioning.[cite: 2]
* **Example State:** `S_NS_G` represents the state where North-South signals are Green, and East-West signals are Red.[cite: 2]

### 2. Standard Demand Inputs
The intersection handles traffic demand dynamically rather than relying on a static, unchanging timer. The controller dashboard accepts the following inputs:[cite: 2]

![Controller Cabinet Inputs](WhatsApp%20Image%202026-07-28%20at%2011.19.26%20PM.jpeg)

* **`veh_ns` (Toggle):** Simulates vehicle presence detection for the North-South lanes.[cite: 2]
* **`veh_ew` (Toggle):** Simulates vehicle presence detection for the East-West lanes.[cite: 2]
* **`ped_btn` (Push Button):** Allows pedestrians to request a WALK signal to cross the intersection safely.[cite: 2]

### 3. Priority & Pre-emption System
To handle special circumstances, the controller features robust pre-emption logic that overrides normal state progression:[cite: 2]
* **Emergency Mode (`emergency`):** A toggle switch that interrupts standard traffic flows to grant immediate right-of-way to emergency vehicles.[cite: 2]
* **Night Mode (`night_mode`):** A toggle switch for low-traffic hours that alters standard signal behavior (e.g., flashing yellow for main roads, flashing red for side roads).[cite: 2]

### 4. Simulation & Control Features
The provided dashboard acts as a software model of the physical traffic cabinet, featuring:[cite: 2]
* **Simulation Speed Control:** An adjustable slider (e.g., up to 5x) to fast-forward state transitions and test the system efficiently.[cite: 2]
* **System Reset:** An active-low reset button (`rst_n`) to immediately reset the controller to its default starting state.[cite: 2]

Below are snapshots from the simulation environment tracking the internal registers and logic outputs based on the demand inputs:

![Simulation Waveform 1](WhatsApp%20Image%202026-07-28%20at%2011.19.24%20PM.jpeg)
![Simulation Waveform 2](WhatsApp%20Image%202026-07-28%20at%2011.19.25%20PM%20(1).jpeg)

