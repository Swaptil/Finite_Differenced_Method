# Finite_Differenced_Method

 Heat Diffusion Solver - C++ Program

Author: Swapnil Patil  
ID: S379897  
Department: Aerospace Computational Engineering  

 Overview

This project is a C++ program that solves the 1D unsteady heat conduction equation using several numerical methods. The wall's thickness is 31 cm, with the boundary temperatures set at 149°C, and the initial temperature of the wall is 38°C. The program solves the heat conduction equation over time to determine the temperature distribution through the wall.

 Governing Equation

The governing equation for heat conduction in 1D is:


∂T/∂t = D ∂²T/∂x²


Where:
- `T`: temperature
- `D`: thermal diffusivity of the material
- `t`: time
- `x`: spatial coordinate

 Problem Details:
- Wall thickness: L = 31 cm
- Thermal diffusivity: D = 93 cm²/hr
- Initial temperature: T_in = 38°C
- Boundary temperature: T_sur = 149°C
- Time interval: 0.0 to 0.5 hrs

 Methods Implemented

This program implements the following numerical methods to solve the 1D heat diffusion equation:

 1. DuFort-Frankel Method
   - An explicit method used for stability in high diffusivity cases.
   - The update rule is based on a leapfrog integration in time.

 2. Richardson Method (Central Time, Central Space)
   - An explicit method, second-order accurate in both space and time.
   - It is conditionally stable and requires small time steps.

 3. Laasonen Method (Implicit)
   - A fully implicit method, stable for larger time steps.
   - It solves a tridiagonal system of equations at each time step using the Thomas algorithm.

 4. Crank-Nicolson Method
   - A semi-implicit method, combining the features of both implicit and explicit methods.
   - It provides a balance between stability and accuracy by averaging over time steps.

 5. Analytical Solution
   - The program also computes the analytical solution for comparison. This solution is derived using a series solution involving Fourier sine functions and an exponential decay term based on diffusivity.

 Program Structure

The code follows Object-Oriented Programming (OOP) principles using the `HeatConductionSolver` class. Key components include:

- Variables:  
  - `D`: Diffusivity (93 cm²/hr)
  - `L`: Wall thickness (31 cm)
  - `T_in`: Initial temperature (38°C)
  - `T_sur`: Boundary temperature (149°C)
  - `T_final`: Final time (10 hrs)
  - `h`: Spatial step (0.05 cm)
  - `k`: Time step (0.01 hrs)
  - `mu`: Dimensionless parameter (thermal diffusivity ratio)
  - `u`: Temperature distribution matrix

- Methods:
  - `initializeBoundaryConditions()`: Initializes the boundary temperatures at both ends of the wall.
  - `solveDuFortFrankel()`: Solves the equation using the DuFort-Frankel method.
  - `solveRichardson()`: Solves using the Richardson method.
  - `solveLaasonen()`: Solves using the implicit Laasonen method.
  - `solveCrankNicolson()`: Solves using the Crank-Nicolson method.
  - `solveAnalyticalSolution()`: Computes the analytical solution for comparison.
  - `printSolution()`: Prints the temperature at each grid point for every time step.

 Instructions for Use

 Compilation

This program has been written to be compiled and run in environments supporting C++11 or higher. Follow these steps to compile and run the code:


 HeatConductionSolver heat_conduction_solver.cpp -std=c++11


 Running the Program

After compiling, run the executable to observe the solutions for each method:


HeatConductionSolver


The program will compute and display the temperature distribution for each method at each time step.

 Customization

You can modify the problem parameters such as the initial temperature, boundary temperature, wall thickness, and time step by changing the values in the `main()` function.

For example:


HeatConductionSolver solver(93.0, 31.0, 38.0, 149.0, 10.0, 0.05, 0.01);


Adjusting these parameters will allow you to test different scenarios as part of your analysis.

 Output

The program outputs the temperature distribution for all methods at every time step. You can compare the results visually or numerically to validate the methods against the analytical solution. The temperature values are printed for each spatial location across the time steps.

 Additional Tasks

 Step Size Analysis

To investigate the effect of step size on the accuracy and computation time of the implicit Laasonen method, modify the time step size (`k`) as:

- ∆t = 0.01
- ∆t = 0.025
- ∆t = 0.05
- ∆t = 0.1

 Stability and Accuracy

For the Richardson method, study the accuracy and stability by analyzing how the solution converges with smaller time steps. This is essential for understanding the limitations of the explicit methods used.

 Conclusion

This project provides a comprehensive implementation of numerical methods for solving the 1D heat diffusion equation. The results are compared with the analytical solution to validate the accuracy of each method. The program also allows exploration of the stability and accuracy of explicit vs implicit methods.

