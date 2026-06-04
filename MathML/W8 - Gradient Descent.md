# W8 - Gradient Descent

## Vanilla GD
**Gradient descent** - The baseline for basically all training algorithms.
On a differentiable function $F: \mathbb{R}^P \mapsto \mathbb{R}$:
1. Input an initial point $w_0$ and the number of steps $T>0$.
2. Choose a step-size sequence for each iteration, $\eta_t>0$
3. For each $t$ from 0 to $T-1$:
       $w_{t+1}=w_t-\eta_t \cdot \nabla F(w_t)$
4. Output $w_T$ (usually)
Vanilla GD is extremely robust even for absurd functions if you initialise well enough.

### Proof of Convergence
Consider doing GD on $F(x) = x^2$ starting from any $x_0$ except 0. Step length is bounded between $(0, 0.5)$. Set $k = 1 - \eta \cdot 2$
This means that with iteration, it will asymptotically in time coverge to the global minima.
It takes $\frac{\log{\frac{|x_0|}{\epsilon}}}{\log{\frac{1}{k}}}$ many steps to converge to within $\epsilon$, i.e. epsilon is the target maximum error allowed.

This speed of convergence cannot be beaten. This is the fastest GD can work: $\log{\frac{1}{\epsilon}}$

Proof is just unrolling $x_{t+1}$:
$x_{t+1} = (1- 2 \eta_t)x_t \implies x_t = x_0 \prod_{t=0}^{t-1}(1-2\eta_i)$
$x_t$ will converge to $x_0$ so long as $\eta$ is between $0, 0.5$.
$x_t=x_0 \cdot (1- 2 \eta_t)^t$
Since k, $(1- 2 \eta_t)$, is a fraction, it will always converge.
$|x_0| \cdot k^t ≤ \epsilon$
Number of iterations can be calculated immediately from initial value, k, and epsilon.

When a function is no longer convex or Lipschitz-smooth, things get harder.