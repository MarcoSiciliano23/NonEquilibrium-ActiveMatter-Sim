# ActiveLangevin2D-WCA

Object-Oriented C++ simulator for the study of **Brownian Dynamics (Overdamped Langevin)** of a two-dimensional active and passive matter system. Particles interact via a repulsive excluded-volume potential (Weeks-Chandler-Andersen) and are confined in a box with Periodic Boundary Conditions (PBC).

This project aims to explore the transition between fluid and viscoelastic regimes (via microrheology) and to investigate the emergence of collective phenomena and the maximization of entropy dissipation under the effect of external driving forces.

## Physics of the Model

### 1. Overdamped Langevin Dynamics
The time evolution of the particles is governed by the balance between viscous friction, interparticle forces, external active forces, and thermal noise. Inertia is negligible. Numerical integration is performed using the **Euler-Maruyama** scheme.

### 2. Steric Interaction (WCA Potential)
To model steric hindrance without attractive tails, a Lennard-Jones potential truncated and shifted at its absolute minimum is used (r_cut = 1.12246 sigma).

## Architecture and Structure
The code is written in C++ and uses the **Armadillo** library for efficient and vectorized management of spatial coordinates.
* **particle.cpp / particle.h**: Manages individual particles, tracking both *wrapped* coordinates (for forces) and *unwrapped* coordinates (for studying absolute spatial diffusion and Mean Squared Displacement).
* **system.cpp / system.h**: The physical "engine". It handles the integration loop, O(N^2) interactions, and thermodynamic sampling via Data Blocking.

### Computed Observables
* **Passive System:** Potential Energy, Pressure (Virial), Radial Distribution Function g(r), Mean Squared Displacement (MSD).
* **Active System:** Dissipated Power.

## Requirements and Compilation

The project requires a standard C++ compiler and the Armadillo library installed on the system.

```bash
# Compilation via Makefile
make clean
make

# Execution
./simulator.exe
