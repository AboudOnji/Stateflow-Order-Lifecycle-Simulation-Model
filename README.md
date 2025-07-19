# Stateflow Order Lifecycle Simulation Model

BARSEKH-ONJI Aboud (D.Sc.)

Universidad Anáhuac México Sur - Facultad de Ingeniería

ORCID: https://orcid.org/0009-0004-5440-8092

Email: aboud.barsekh@anahuac.mx


License
This project is distributed under the MIT License. See the LICENSE file for more details.
# Overview
This repository contains a MATLAB Simulink and Stateflow model that simulates the complete lifecycle of a purchase order. The project was developed as an educational example for a master's degree course in logistics process simulation. Its main objective is to demonstrate how the Stateflow tool can be used to model complex business logic, reactive systems, and state-based processes in a structured, hierarchical, and scalable manner.

Model Evolution
The model was built incrementally in three phases, each adding a new layer of complexity and realism. This approach allows for the progressive study of different Stateflow features.

Phase 1: Basic Model (The "Happy Path")
Objective: To establish the ideal process flow without exceptions.

States: Inactive -> Received -> Payment_Verified -> Inventory_Assigned -> Order_Shipped -> Order_Delivered.

Stateflow Concepts Used:

Creation of basic states.

Transitions conditioned by boolean inputs.

Use of enumerated data types (IntEnumType) to improve readability.

Entry actions (entry) to update the output state.

Phase 2: Handling Exceptions and Decision Logic
Objective: To introduce alternative paths to manage common process failures.

New States: Payment_Failed, Out_of_Stock.

Stateflow Concepts Used:

Junction Connectors: To implement if-then-else decision logic graphically.

Modeling of exception flows that return the system to a stable state.

Use of temporal operators (after) for automatic transitions.

Phase 3: Hierarchy and Parallel Processes
Objective: To structure the model to handle concurrent processes and global interrupt logic.

New States: Canceled, Return_Requested, Package_Received_Return, Refund_Processed.

Stateflow Concepts Used:

Superstates (Hierarchy): Grouping the main logic into an Active_Order state to simplify the diagram and allow for high-level transitions.

Parallel States (Orthogonality): Simultaneous modeling of the main order process and an independent return subprocess.

Interrupt Transitions: A cancellation request can interrupt any active substate within Active_Order, demonstrating the power of hierarchy.

Repository Files
modelo_orden.slx: The main Simulink model file containing the Stateflow Chart.

OrdenStatus.m: The MATLAB script that defines the OrdenStatus enumeration class. It is essential for the model to work correctly.

README.md: This file.

How to Use the Model
Ensure you have MATLAB, Simulink, and Stateflow installed.

Clone or download this repository to your local machine.

Open MATLAB and navigate to the directory where you saved the files.

Make sure that both modelo_orden.slx and OrdenStatus.m are in the same folder or on the MATLAB path.

Open the modelo_orden.slx file.

Run the simulation (by pressing the "Run" button). It is recommended to set the simulation time to infinite (inf) to be able to interact with the model.

During the simulation, you can force transitions by manually changing the values of the Constant blocks that serve as inputs to the Stateflow Chart (e.g., changing the value of nueva_orden to 1 to start a process).

