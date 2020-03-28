

## 1.4.1 Local Optimization
A large fractions of the research on general nonlinear programming has focused on methods for lcoal optimiation, which as a consequence are well developed. because its fast and can handle large-scale problems and are widely applicable the only requireedment is that the objective function should be differentiable.

they are really sensitive to initial optimization. which makes local optimization more like an art
In contrast, there is a little art involved in solving a least-squres problem or a linear program.

## 1.4.2 Global Optimization

The objecive function is a utility function, i.e, one for which smaller values are worse than larger values, and the constraints represent prior knowledge about the possible parameter values.

## Role of convex optimization in nonconvex optimiation

we can combine convex optimization with a local optimization method by first soving the approximate problem which obtain the exact solution , then we can use this optimal point as a starting point for our local optimization method.


### Bounds for global optmization

IN relaxation, each nonconvex constraint is repaced with a looser, but convex, constraint. In lagrangian relaxation, the Lagrangin dual problem is solved. this problem is convex and provides a lower bound on the optimal value of the nonconvex problem<!--  -->.