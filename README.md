# burgers_1D_main

1. Problem Statement:Burgers'Equation

$$\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} = \nu \frac{\partial^2 u}{\partial x^2}$$
Viscosity Coefficient ($\nu$): $0.01/\pi$.
Initial Condition (IC): $u(x,0) = -\sin(\pi x)$.
Boundary Conditions(BC): $u(-1,t) = u(1,t) = 0$.

2. Technical Highlights

Neural Network Architecture

Structure: A Multi-Layer Perceptron(MLP) with 2 inputs ($x,t$) and 1 output ($u$).
