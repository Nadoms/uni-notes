# W7 - Background Mathematics
## Function Classes
Some notation:
- $\mapsto$ means maps to
- | means for every
- $\forall$ means for all
- $\epsilon$ means in

A NN architecture with unassigned weights is a function class. Any architecture is a class.

Models are functions of input data, parameterised by weights.
![c864ad0e49dca1d3d94ae25dfc201d73.png](./c864ad0e49dca1d3d94ae25dfc201d73.png)
Losses are functions of the weights.
![ba899541efb2622501adb23275a4dd33.png](./ba899541efb2622501adb23275a4dd33.png)

### Euclidean Norm
**2-Norm** - Given a vector, its 2-norm is the euclidean distance from the origin.
$||v||_2 = \sqrt{v^2_1+v^2_2+...+v^2_p}$

### Lipschitzness
**L-Lipschitz** - A function F, $\mathbb{R}^p \rightarrow \mathbb{R}$, where for any two sets of inputs $x, y$:
![256377d808cd636e82cca61998b315f6.png](./256377d808cd636e82cca61998b315f6.png)
This means a function is linearly upper-bounded. The gap between the outputs is always less than the gap between the inputs (multiplied by L).

$F(x) = x$ is 1-Lipschitz.

### Convexity
**Convexity** - If a function's graph between any two points always lies below or on some chord joining the points $(x, F(x)),(y, F(y))$.
![b7b076722ffcef789abd779dbb72a96c.png](./b7b076722ffcef789abd779dbb72a96c.png)
Which basically says this:
![49b14f42e9e1aab54098347c90a043c5.png](./49b14f42e9e1aab54098347c90a043c5.png)

A differentiable function is convex if:
![2718b1fd4dacaadbea7717487f954f05.png](./2718b1fd4dacaadbea7717487f954f05.png)
Basically its differential at prior point x is lower than at point y. Its curvature is $\ge 0$.

**Differentiable** - When a function does not have any hard edges, and its differential will output real numbers.

### Smoothness
**$\beta$-Lipschitz smoothness** - When a differentiable function satisfies:
![25cea46ee4b8258528baf876c483e0f5.png](./25cea46ee4b8258528baf876c483e0f5.png)
So basically its differential is Lipschitz smooth.
$F(x) = x^2$ is 2-smooth.

### Convergence
A sequence of points convergences at a point if as the limit reaches infinity, the 2-norm between the last point and the convergent point is 0.

### Supremums and Infimums
A supremum is the least upper bound given some bounds.
An infimum is the greatest lower bound given some bounds.
$I = [0, 1) \rightarrow \text{sup } I = 1$

### Spectral Norms
**2, 2-norm** dont get it  eigen blah 