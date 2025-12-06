# Genetic Algorithm and PSO Optimization for Race Car Frame Design

This repository contains Python implementations of Genetic Algorithm (GA) and Particle Swarm Optimization (PSO) applied to the structural optimization of a race car frame. The study focuses on minimizing the total structural weight while ensuring that safety and displacement constraints are satisfied. A finite element model (FEM) is constructed using Python to evaluate each candidate design. The full methodology and analysis are documented in the accompanying report.
<img width="747" height="807" alt="image" src="https://github.com/user-attachments/assets/68a3e3e6-84e7-4d21-b547-6f3185e6d9fc" />

## Overview

The structure under investigation is a simplified Formula 1–inspired chassis composed of 69 beam elements and 30 nodes. Each beam element can be assigned one of several cross-sectional profiles and material types. External forces are applied to the left side of the frame, and the right side is fully constrained. The optimization objective is to minimize weight while satisfying the following conditions:

• The minimum factor of safety must not fall below 3.  
• The maximum nodal displacement must not exceed 0.6 mm.

Both GA and PSO are used to search the discrete design space of beam sections and materials.

## Finite Element Model

The FEM implementation is written in Python using the PyNite library. The model constructs nodes, beams, material properties, and boundary conditions. It evaluates structural responses, including:

• Total weight  
• Nodal deflections  
• Factor of Safety (FOS)

These results are returned for use in fitness evaluation within the optimization algorithms.

## Genetic Algorithm Optimization

The GA optimization uses an integer-encoded chromosome representing section IDs and material IDs for all members. The fitness function combines normalized weight and penalty terms for constraint violations. Two sets of GA parameters were tested: one with default settings and one with a higher elite ratio.

The GA results demonstrate that incorporating elitism improves convergence and yields lighter structures while still maintaining the required safety and displacement limits.

## GA With Constraints

A refined version of the GA explicitly incorporates constraint handling. Structural weight, maximum displacement, and minimum FOS are normalized, and penalty terms are added when constraints are violated. This ensures that the optimization process naturally favors feasible designs. Both tested GA configurations successfully produce designs that satisfy all constraints.
<img width="693" height="367" alt="image" src="https://github.com/user-attachments/assets/58e55843-1af7-4959-b503-1fec21303157" />

## Particle Swarm Optimization

A binary-encoded PSO method is also implemented. The design variables are encoded into bit strings and decoded during fitness evaluation. Two PSO parameter sets were tested, each producing feasible solutions that satisfy all displacement and safety constraints.

Compared to the GA results, PSO achieves lower structural weights and higher safety margins. Although PSO exhibits more fluctuation during convergence, it ultimately finds better solutions and does so with fewer evaluations.
<img width="712" height="368" alt="image" src="https://github.com/user-attachments/assets/547db284-2408-4eaa-9949-9c83429240d9" />

## Comparative Analysis

• PSO outperforms GA in weight minimization while maintaining feasibility.  
• Both GA and PSO satisfy the factor of safety and displacement requirements.  
• GA offers smoother convergence, whereas PSO converges faster but with more oscillation.  
• PSO-optimized designs achieve higher safety margins and better material distribution.

## Conclusion

This project demonstrates the application of population-based optimization methods to a finite element structural design problem. GA and PSO are both effective for discrete optimization of a complex truss structure, with PSO providing the best overall results. These methods show strong potential for use in engineering design, especially when constraints, discrete variables, and nonlinear behavior are involved.
