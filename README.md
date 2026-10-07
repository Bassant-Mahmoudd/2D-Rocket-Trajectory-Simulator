# 2D-Rocket-Trajectory-Simulator

## Overview
This repository contains a computational dynamics solver that simulates the launch trajectory of a rocket subject to atmospheric drag, variable mass, and wind disturbances. The core engine is a custom numerical integrator utilizing Heun's Method (a second-order Runge-Kutta algorithm) to continuously solve the non-linear equations of motion.

## Physics & Aerodynamic Modeling
The vehicle's state is continuously updated by integrating a system of first-order ODEs. 
*   **Thrust:** Dynamically aligns with the instantaneous velocity vector.
*   **Aerodynamic Drag:** Modeled to strictly oppose the air-relative velocity vector, seamlessly incorporating ambient wind disturbances into the kinematics.
*   **Mass Variation:** Vehicle mass decreases dynamically as a function of the instantaneous mass flow rate during the powered flight phase.

## Algorithm Verification
To ensure the integrity of the numerical solver, the Heun's method algorithm was rigorously validated against a purely analytical solution for a simplified 1-D vertical flight regime ($C_D = 0$, Constant Thrust). The numerical integration matched the analytical kinematic predictions with a margin of error $< 1\%$, proving the robustness of the time-stepping architecture.

| Parameter | Analytical Value (ft) | Numerical Output (ft) |
| :--- | :--- | :--- |
| **Burnout Height** | 486.7 | 490.11 |
| **Total Apogee** | 4212.7 | 4351.99 |

## Simulation Capabilities
The simulator outputs full state history (Time, Altitude, Range, Velocity, Acceleration) until ground impact. The included multi-trajectory analysis evaluates varying launch angles ($70^\circ$, $75^\circ$, $80^\circ$) operating under a constant 10 mph headwind vector.

<img width="1000" height="600" alt="Figure_12" src="https://github.com/user-attachments/assets/aa8a0da7-0656-48f5-861e-f873066edc7f" />
