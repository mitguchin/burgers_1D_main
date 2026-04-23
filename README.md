# burgers_1D_main

1. Problem Statement:Burgers'Equation

$$\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} = \nu \frac{\partial^2 u}{\partial x^2}$$

1) Viscosity Coefficient ($\nu$): $0.01/\pi$.
2) Initial Condition (IC): $u(x,0) = -\sin(\pi x)$.
3) Boundary Conditions(BC): $u(-1,t) = u(1,t) = 0$.

2. Technical Highlights

Neural Network Architecture

1) Structure: A Multi-Layer Perceptron(MLP) with 2 inputs ($x,t$) and 1 output ($u$).
2) Depth: 5 hidden layers with 20-30 neurons each.
3) Activation: Tanh(Hyperbolic Tangent) was choosen to ensure smooth higher-order derivatives,which is critical for calculating the Laplacian
($\frac{\partial^2 u} {\partial x^2}$) in the PDE loss.

# Physics-Informed Training(Autograd)
Using PyTorch's Automatic Differentiation(Autograd), the physical residuals are directly optimized:

1) PDE Loss: Minimizes the residual of the Burgers' equation across the entire computational domain.
2) Data Loss: Minimizes the prediction error at the initial and boundary points.
* Total Loss: $Loss_{Total} = Loss_{Data} + Loss_{PDE}$.

