# Equilibrium Analysis in Computational Science

## Speaker: Heider Jeffer
## instructor: Mehdi Jazayeri 
### Topic: Computational Science - Equilibrium Analysis

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

### Conclusion
Understanding equilibrium and stability in computational science is essential for predicting system behavior. Through various models and examples, we have seen how equilibrium analysis helps in designing and controlling systems in fields ranging from chemical processing to ecological modeling.
