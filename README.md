# PLC-Sorter-Conveyor-Control
Automated multi-lane sorting conveyor system integrating Factory I/O (3D simulation), Allen-Bradley Micro850 PLC ladder logic (CCW), and Ignition Vision HMI.

# Multi-Lane Sorter Conveyor Control System

An automated industrial sorting conveyor application integrating 3D plant simulation, PLC ladder logic execution, and an HMI interface.

## System Overview

* **Simulation:** Factory I/O (3D multi-lane divert conveyor scene with optical height sensors)
* **PLC Controller:** Allen-Bradley Micro850 (Connected Components Workbench / Micro800 Simulator)
* **HMI:** Ignition Vision
* **Communication:** EtherNet/IP (CIP) / OPC-UA
<img width="1601" height="798" alt="3D_Front_View" src="https://github.com/user-attachments/assets/408d9c92-2024-4356-a38a-69eb64f856bf" />

<img width="1566" height="876" alt="Angle_View_1" src="https://github.com/user-attachments/assets/ac41a965-cec8-4781-a793-b81a0045c4f6" />

<img width="784" height="574" alt="HMI" src="https://github.com/user-attachments/assets/dc75a68e-48c7-4d53-8e67-998a47363b9c" />


---

## Architecture & Logic Highlights

1. **Part Classification & Sorting:** Optical sensors identify box height profiles and trigger lane divert mechanisms to sort items sequentially.
2. **First-Scan Stabilization:** Implements `__SYSVA_FIRST_SCAN` alongside an internal `Master_Reset` tag to zero out Count-Up (`CTU`) accumulators on startup, eliminating false rising-edge increments during initial contact scans.
3. **Fail-Safe Sensor Initialization:** Default starting states configured for Emergency Stop pushbuttons and normally closed optical sensors to prevent nuisance tripping during driver communication.
4. **HMI Operator Interface:** Real-time conveyor belt status visualization, live exit counters, Emergency Stop monitoring, and centralized manual/automatic controls.

---

## Repository Contents

* `/CCW` - Connected Components Workbench solution and exported ladder logic.
* `/FactoryIO` - Factory I/O 3D simulation scene file (`.factoryio`).
* `/HMI` - Ignition Vision project archive (`.zip`).

---

## Setup & Running the Project

1. **Micro850 Simulator:** Open the CCW project, build (`F7`), and set the controller to **RUN** mode.
2. **Factory I/O:** Open the scene, go to **File > Drivers**, verify the Micro800 driver is connected, and click **Play**.
3. **Ignition Gateway:** Import the HMI project archive under **System > Projects**, and import the rewquired tags into the `default` tag provider via the Tag Browser.
4. Launch the Vision Client to monitor and operate the sorting line.
