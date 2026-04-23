# burgers_1D_main


1. Problem Statement:Burgers'Equation

$$\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} = \nu \frac{\partial^2 u}{\partial x^2}$$

- Viscosity Coefficient ($\nu$): $0.01/\pi$
- Initial Condition (IC): $u(x,0) = -\sin(\pi x)$
- Boundary Conditions(BC): $u(-1,t) = u(1,t) = 0$


2. Technical Highlights

Neural Network Architecture

- Structure: A Multi-Layer Perceptron(MLP) with 2 inputs ($x,t$) and 1 output ($u$)
-  Depth: 5 hidden layers with 20~30 neurons each.
- ctivation: Tanh(Hyperbolic Tangent) was choosen to ensure smooth higher-order derivatives,which is critical for calculating the Laplacian
($\frac{\partial^2 u} {\partial x^2}$) in the PDE loss.

* Physics-Informed Training(Autograd)

Using PyTorch's Automatic Differentiation(Autograd), the physical residuals are directly optimized:

- PDE Loss: Minimizes the residual of the Burgers' equation across the entire computational domain.
- Data Loss: Minimizes the prediction error at the initial and boundary points.
- Total Loss: $Loss_{Total} = Loss_{Data} + Loss_{PDE}$

# Two-stage Optimization Strategy
: A Hybrid optimization approach was implemented to balance speed and precision:


1. Adam Optimizer:
Used in initial phase to navigate the loss landscape quickly and reach the global minimum vicinity.


2. L-BFGS Optimizer:
A second-order optimizer that utilizes curvature information to achieve high-precision convergence in the final stages of traning.


3. Result & Visulization
The trained model successfully captures shock wave formation, a hallmark of the Burgers' equation where the wave steepens over time.

* Heatmap (u distribution): Visualizes the velocity field $u$ across space ($x$) and time($t$), showing the non-linear advection process.
* Line plots: Cross-sections at specific time steps confirm the sharpening of the wave profile into a shock.


4. Implementation Details
* Framework: PyTorch(with CUDA support for GPU acceleration).
* Key Libraries: NumPy for data handling, Matplotlib/Seaborn for high-fidelity scientific visualization, and TQDM for progress tracking.
* Precision: High-resolution grids($h = 0.01, k=0.01$) were used for final inference to validate the model's continuity.



