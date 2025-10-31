# flow-over-a-box-using-FDM
A 2D CFD simulation of laminar flow past over square obstacle using FDM in python.
OBJECTIVE: To simulate 2D incompressible flow around a square box using the Finite Difference Method (FDM) and analyze:
1. Solve the 2D incompressible Navier–Stokes equations using FDM.
2. Apply appropriate boundary conditions for inlet, outlet, walls, and obstacle.
3. Visualize flow using streamlines and vorticity contours.
4. Compute drag and lift coefficients and study their variation with time.
5. Analyze flow behavior for multiple Reynolds numbers.
Methodology:
• Structured grid generation for a 2D domain.
   A 2D channel of size Lx × Ly is discretized into a structured grid.
    Grid spacing: dx = Lx/(nx-1), dy = Ly/(ny-1).
• Explicit time stepping for momentum equations.
    Continuity: ∂u/∂x + ∂v/∂y = 0
     Momentum (u-direction): ∂u/∂t + u∂u/∂x + v∂u/∂y = -(1/ρ)∂p/∂x + ν∇²u
   Momentum (v-direction): ∂v/∂t + u∂v/∂x + v∂v/∂y = -(1/ρ)∂p/∂y + ν∇²v
• Pressure Poisson Equation solved using Gauss–Seidel iteration.
       ∇2p=b(x,y)
• No-slip condition on walls and obstacle.
    • Inlet: u = U_in, v = 0
    • Outlet: Zero-gradient
    • Walls: No-slip (u = 0, v = 0)
    • Obstacle: No-slip
• Force calculation based on pressure difference method.
    CD​=2(p_front​−p_back​)/ρU^2
    CL​=2(p_top​−p_bottom​)​/ρU^2
               
Governing Equations:
The 2D incompressible Navier–Stokes equations in Cartesian form:
![OIP](https://github.com/user-attachments/assets/0ec4ba43-aa3e-4756-b588-728ee93fbd3d)


NUMERICAL SETUP:
| Parameter           | Symbol                   | Value       |
| ------------------- | ------------------------ | ----------- |
| Domain size         | (L_x * L_y)              | 2.0 × 1.0 m |
| Grid resolution     | (n_x * n_y)              | 225 × 100   |
| Time step           | Δt                       | 0.001 s     |
| Kinematic viscosity | ν                        | 0.01 m²/s   |
| Inlet velocity      | Uₐ                       | 0.5 m/s     |
| Pressure solver     | Iterative Gauss–Seidel   |             |
| Scheme              | Explicit FDM (2nd order) |             |
 Numerical Scheme:
Discretization: Finite Difference Method (FDM)  
Pressure Correction: Iterative Poisson solver  
Boundary Conditions:
  - Inlet: uniform velocity  
  - Outlet: zero-gradient  
  - Walls: no-slip (u = v = 0)  
  - Box surface: no-slip  
  Time Marching: Explicit scheme  
  Pressure Solver:Gauss–Seidel iteration  

Obstacle:
A square box centered in the domain from x = 0.8–1.0 and y = 0.4–0.6, modeled as a no-slip
boundary.

These are recorded at every time step to track vortex shedding and force oscillations.
Simulated Reynolds Numbers:
| Re| Likely Flow Regime                                       |
| ------ | -------------------------------------------------------- |
| 55     | Laminar, steady, symmetric wake                          |
| 85     | Transitional, periodic vortex shedding                   |
| 250    | Unsteady, strong oscillations                            |
| 1000   | Fully unsteady, large wake, quasi-turbulent              |
| 1797   | Strong unsteady, large amplitude oscillations in Cl & Cd |


