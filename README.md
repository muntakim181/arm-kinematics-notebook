# 6-DOF Robotic Kinematics

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)

A complete, ground-up mathematical framework and interactive visualization suite for 6-Degree-of-Freedom (6-DOF) robotic manipulators. This repository bridges the gap between theoretical kinematics and real-world robot control, transitioning from classical geometry to professional numerical solvers.

This repository serves as both a robust mathematical foundation for custom hardware control and an interactive educational masterclass for robotics engineers.

## Table of Contents
- [Overview](#overview)
- [The Curriculum (Notebooks)](#the-curriculum-notebooks)
- [Core Engineering Features](#core-engineering-features)
- [Hardware Architecture Assumptions](#hardware-architecture-assumptions)
- [Installation & Setup](#installation--setup)
- [Author](#author)

---

## Overview
Standard kinematics libraries (like Peter Corke's Robotics Toolbox) are incredibly useful, but they often obscure the underlying math. When a robot hits a singularity and teleports or crashes, engineers need to understand *why* the matrix collapsed. 

This project exposes the entire control loop using interactive Jupyter Notebooks. Using `numpy`, `matplotlib`, and `ipywidgets`, you can physically drag sliders and watch the math break down, adapt, and solve in real-time.  

Also For interactive GUI WebApp visit [Here](https://arm-kinematics-webapp.vercel.app/)

---

## The Curriculum (Notebooks)

The notebooks in this repository are designed to be run sequentially, taking you from basic geometry to state-of-the-art path planning.

1. **Forward Kinematics:** Building the $4 \times 4$ Homogeneous Transformation Matrices and chaining the Denavit-Hartenberg (DH) parameters.
2. **Analytical Inverse Kinematics:** Deriving exact algebraic solutions for position (Wrist Center) and orientation using Kinematic Decoupling.
3. **The Gimbal Lock Trap:** Visualizing the mathematical failure of Euler angles at $\pm 90^\circ$ pitch.
4. **The Geometric Jacobian:** Building the velocity mapping matrix using vector cross-products instead of heavy partial derivatives.
5. **Numerical Inverse Kinematics:** Writing a robust control loop using the Pseudo-Inverse ($J^+$) and tracking end-effector error.
6. **Singularities & Damped Least Squares (DLS):** Injecting a damping factor ($\lambda$) to safely navigate mathematical breakdowns without violently commanding infinite joint velocities.
7. **Redundancy & Null Space:** Using the Null Space Projector $(I - J^+ J)$ to control internal arm motion (obstacle avoidance) while maintaining a strict end-effector pose.
8. **Dual Quaternions:** Proving the superiority of Quaternion SLERP over Euler angle interpolation for smooth, predictable tool paths.

---

## Core Engineering Features
* **Interactive Visualizations:** Every complex algorithm is paired with an interactive 3D Matplotlib plot with UI sliders.
* **Zero-Offset Kinematic Logic:** The mathematical models are strictly designed with zero joint offsets, ensuring all base configurations zero out cleanly for seamless slider and hardware control.
* **Algorithm Progression:** Clearly shows *why* the industry moved from Analytical math $\rightarrow$ Euler Jacobians $\rightarrow$ Dual Quaternions.

## Hardware Architecture Assumptions
The analytical derivations in this repository intentionally diverge from standard textbooks. Instead of a traditional differential spherical wrist, the math is tailored for a **custom single-motor wrist architecture** with a separated tool axis. 

This makes the repository highly applicable for custom-machined or 3D-printed robotic arms utilizing standard servos and stepper motors. The control logic is optimized for downstream integration with ESP32 microcontrollers, SocketCAN interfaces, and ROS 2.

---

## Installation & Setup

To run these interactive notebooks locally, clone the repository and install the required Python packages.

```bash

## Create a Project Folder
Navigate to the directory where you want your project and create a new folder:

mkdir my-project
cd my-project
```
```bash
# Clone the repository
git clone https://github.com/muntakim181/arm-kinematics-notebook.git
cd arm-kinematics-notebook.git
```
## Create the Virtual Environment
Run the standard Python module `venv`. It is recommended to name the environment folder `.venv` so that it stays hidden in your workspace:
```bash
python -m venv .venv
```

### macOS / Linux
```bash
source .venv/bin/activate
```

### Windows (Command Prompt)
```cmd
.venv\Scripts\activate.bat
```

## Install the Dependencies
Run the installation command using the `-r` (requirement) flag:
```bash
pip install -r requirements.txt
```

### Or For Conda Users
```bash
# Create a virtual environment (optional but recommended)
$ conda create --name <env> --file requirements.txt
conda activate <env> 
```

# Launch Jupyter Lab
```bash
jupyter lab
```

Author
Muntakim Ali Rashfi

Robotics Enthusiast & Data Science Student

Focused on control systems, physics simulations, Reinforcement Learning and AI integration for advanced manipulators.
