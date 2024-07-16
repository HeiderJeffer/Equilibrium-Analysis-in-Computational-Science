<body>
<img src = "https://github-vistors-counter.onrender.com/github?username=https://github.com/HeiderJeffer/MSc.-ETH-Zurich-and-USI-Equilibrium-Analysis-in-Computational-Science" alt = "Visitors-Counter"/>
</body>

#### Equilibrium Analysis in Computational Science
#### Speaker: Heider Jeffer
#### instructor: Mehdi Jazayeri 
#### Assistant: Dr. Sasa Nesic
#### Topic: Computational Science - Equilibrium Analysis

### Introduction to Equilibrium
The equilibrium of a system is a state where the system experiences no net change. Equilibrium analysis in computational science is crucial for understanding the behavior of systems under various conditions. Here, we will discuss the different types of equilibrium, their stability, and examples of how they are analyzed in various models.

### Types of Equilibrium
1. **Stable Equilibrium**: A system is in stable equilibrium if, after being slightly displaced, it returns to its original equilibrium position.
2. **Unstable Equilibrium**: A system is in unstable equilibrium if, after being slightly displaced, it does not return to its original equilibrium position and does not remain in the displaced position.
3. **Neutral Equilibrium**: A system is in neutral equilibrium if, after being slightly displaced, it remains in the new position without returning to the original or moving further away.
4. **Metastable Equilibrium**: The system returns towards equilibrium as long as disturbances are not too large. The equilibrium is not globally stable; once the system crosses an unstable point, it may not return to the stable state.
5. **Metastable Equilibrium with Multiple Stable States**: The system returns to one of several possible equilibrium states depending on the nature of the disturbance. The system is globally stable with multiple local equilibria.

### Stability
Stability refers to the ability of a system to maintain its equilibrium state. For a system to be considered stable, small perturbations should not lead to significant deviations from the equilibrium.

### Mechanisms and Examples
#### Stable and Unstable Equilibria
- **Stable Equilibrium**: If a body is displaced slightly, it returns to its equilibrium position. An example is a marble at the bottom of a bowl.
- **Unstable Equilibrium**: If a body is displaced slightly, it moves away from its equilibrium position. An example is a marble balanced on the top of an inverted bowl.
- **Neutral Equilibrium**: If a body is displaced slightly, it remains in the new position. An example is a marble on a flat surface.

### Attractors and Their Types
In dynamic systems, attractors represent the states towards which a system tends to evolve. There are several types of attractors:
1. **Stable Equilibrium (Steady State)**: The system returns to this state after small disturbances.
2. **Limit Cycle**: The system oscillates in a closed trajectory.
3. **Chaos**: The system exhibits complex, non-repeating patterns.

#### Example: Chaotic Attractor (Lorenz Attractor)
The Lorenz attractor is a classic example of chaos in a system. It demonstrates how small changes in initial conditions can lead to vastly different outcomes.

### Example Systems and Analysis
#### Chemical Plant Model
A chemical plant processes a substance through two reactors in a cascade. The reactors are modeled as reservoirs, and the variation of mass over time is proportional to the net inflow. The system is represented by state variables \(x_1\) and \(x_2\), with equations governing the mass flow:

\[
\begin{align*}
\dot{x}_1 &= -ax_1 + u \\
\dot{x}_2 &= -ax_2 + ax_1 \\
z &= ax_2 + d
\end{align*}
\]

The equilibrium point is found by setting the derivatives to zero and solving for \(x_1\) and \(x_2\). For stability, the eigenvalues of the system matrix are calculated. If all eigenvalues have negative real parts, the system is stable.

### Logistic Model Example
To find equilibria in the logistic model, we solve the equation \( \frac{dN}{dt} = rN \left(1 - \frac{N}{K}\right) = 0 \). The equilibria are \( N = 0 \) and \( N = K \).

- **N = 0**: Unstable equilibrium.
- **N = K**: Stable equilibrium.

### Stability of Models with Several Variables
In multi-variable models, stability analysis involves:
1. Finding equilibrium points.
2. Linearizing the model around these points.
3. Calculating the Jacobian matrix and its eigenvalues.
4. If all eigenvalues have negative real parts, the equilibrium is stable; otherwise, it is unstable.

#### Predator-Prey Model
In a predator-prey model, the equilibrium densities of prey (\(H^*\)) and predators (\(P^*\)) are found by solving the system of equations. The Jacobian matrix at the equilibrium is used to determine stability.

### Stability in Discrete-Time Models
A discrete-time model is stable if the absolute value of the slope of the system's response is less than one. This condition ensures that the system's deviations from equilibrium diminish over time.

### Example

These examples demonstrate how to find equilibrium points and analyze stability for different models in computational science using Python. Each example includes solving equations for equilibrium points and performing stability analysis using methods such as eigenvalues of Jacobian matrices or discrete-time stability criteria.

### Example 1: Logistic Model Equilibrium Analysis

```python
import sympy as sp

# Define symbols and variables
N = sp.symbols('N')
r, K = sp.symbols('r K', positive=True)

# Define the logistic model equation
dN_dt = r * N * (1 - N / K)

# Find equilibrium points by solving dN/dt = 0
equilibria = sp.solve(dN_dt, N)
print("Equilibrium points for Logistic Model:")
for eq in equilibria:
    print(f"N = {eq}")

# Stability analysis
for eq in equilibria:
    jacobian_matrix = sp.Matrix([[sp.diff(dN_dt, N)]])
    stability_condition = jacobian_matrix.subs(N, eq)
    if stability_condition < 0:
        print(f"N = {eq} is stable.")
    else:
        print(f"N = {eq} is unstable.")
```

### Example 2: Chemical Plant Model Equilibrium Analysis

```python
import numpy as np
from scipy.linalg import eig

# Define parameters
a = 0.5  # Example value
u, d = 1, 1  # Example inputs

# Define the system matrix and equilibrium point
A = np.array([[-a, 0],
              [a, -a]])
b = np.array([[u],
              [d]])
x_eq = np.linalg.solve(A, b)

print("Equilibrium point (x1, x2):", x_eq)

# Stability analysis using eigenvalues
eigenvalues, _ = eig(A)
print("Eigenvalues:", eigenvalues)
if np.all(np.real(eigenvalues) < 0):
    print("The system is stable.")
else:
    print("The system is unstable.")
```

### Example 3: Predator-Prey Model Equilibrium Analysis

```python
from sympy import symbols, Matrix
from sympy.solvers import solve

# Define symbols and variables
H, P = symbols('H P')
a, b, c, d = 0.5, 0.5, 0.5, 0.5  # Example parameters

# Define predator-prey model equations
dH_dt = a * H - b * H * P
dP_dt = -c * P + d * H * P

# Find equilibrium points by solving dH/dt = 0 and dP/dt = 0
equilibria = solve((dH_dt, dP_dt), (H, P))
print("Equilibrium points for Predator-Prey Model:")
for eq in equilibria:
    print(f"H = {eq[0]}, P = {eq[1]}")

# Stability analysis
for eq in equilibria:
    jacobian_matrix = Matrix([[dH_dt.diff(H), dH_dt.diff(P)],
                              [dP_dt.diff(H), dP_dt.diff(P)]])
    stability_condition = jacobian_matrix.subs({H: eq[0], P: eq[1]}).eigenvals()
    if all([eig.real < 0 for eig in stability_condition]):
        print(f"H = {eq[0]}, P = {eq[1]} is stable.")
    else:
        print(f"H = {eq[0]}, P = {eq[1]} is unstable.")
```



### Conclusion
Understanding equilibrium and stability in computational science is essential for predicting system behavior. Through various models and examples, we have seen how equilibrium analysis helps in designing and controlling systems in fields ranging from chemical processing to ecological modeling.
