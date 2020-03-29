# Convex Function

## Basic properties and examples

<div align="center">
    <img src="Assets/Img/fig31.png" width="400">
</div>

A function $f: \mathbf{R}^n \rightarrow \mathbf{R}$ is *convex* if **dom** $f$ is a convex set and if for all $x$, $y \in \mathbf{dom}f$, and $\theta$ with $0 \leq \theta \leq 1$, we have

$$
\color{blue}{f(\theta_x + (1-\theta)y)}  \color{black}\hspace{2pt}{\leq}\hspace{2pt} \color{red}{\theta f(x) + (1-\theta)f(y)}
$$

this inequality is known as **jensen's inequality**.

this inequality means that the line segment bbetween (x, f(x)) and (y, f(y)), which is the *chord* from $x$ to $y$, lies above the graph of $f$.

### Extended-value extensions

we can also embed the domain of our problem inside our convex function like this:

$$
\bar{f}(x)=\left\{\begin{array}{ll}
{f(x)} & {x \in \operatorname{dom} f} \\
{\infty} & {x \notin \operatorname{dom} f}
\end{array}\right.
$$

this essentially say that if a point violates the domain then set it to infinity which will make this problem essentially infeasable for these points.

we will say more about these kinds of techniques, later in the next chapter.

### First-order conditions

apart from jensen's inequality, we can check wether a function is convex or not using its gradient information ( if the function is differnetiable that is..). one such techinique which uses first-order derivative is (which can be though of as a *global underestimator* of the function $f$) as follows:

$$ f(y) \geq f(x) + \nabla f(x)^T(y-x)$$

this inequaltiy shows that from local information about a convex funtion we can derive global information. this property exmplains some of th remarkable properties of convex functions for example, this inequlatiy shows that if $\nabla f(x) =0$, then for all $y \in \mathbf{dom}f$, $x$ is a global minimizer of the function $f$ 

we can also check for concavity by using 

$$ f(y) \leq f(x) + \nabla f(x)^T(y-x)$$

and ofcourse, by using strict $>$ or $<$ we can check for strict convexity or strict concavity of a function.

### second-order conditions

we can also use the second-order derivative to check wether a function is convex or not although this can be hard to compute for higher-dimensions.

$$ 0 \preceq  \nabla^2 f(x)$$


the book gives alot of examples of functions that are convex or not, but as some professors have mentioned earlier, the best way to consume that is to practice the exercise, prove that a function is convex using the above conditions and develop the intution along the way. so we will skip the examples for now, but if you want them you can check pgno. 71 to 75.


### Epigraph and Hypograph

<img src="Assets/Img/fig35.png">

The graph of a function $f: \mathbf{R}^{n} \rightarrow \mathbf{R}$ is defined as
$$
\{(x, f(x)) | x \in \operatorname{dom} f\}
$$
which is a subset of $\mathbf{R}^{n+1} .$ The epigmaph of a function $f: \mathbf{R}^{n} \rightarrow \mathbf{R}$ is defined as
$$
\text { epi } f=\{(x, t) | x \in \operatorname{dom} f, f(x) \leq t\}
$$
which is a subset of $\mathbf{R}^{n+1} .$ (Epi' means 'above' so epigraph means 'above the graph'.) The definition is illustrated in figure $3.5 .$

The link between convex sets and convex functions is via the epigraph: $A$ function is convex if and only if its epigraph is a convex set. A function is concave if and only if its **hypograph**, defined as
$$
\text { hypo } f=\{(x, t) |  t \leq f(x)\}
$$
is a convex set.

<div align="center">
<img src="Assets/Img/epi_hypo_scienceDIrect.jpg"/>

source: <a href="https://www.sciencedirect.com/science/article/pii/S0167947310004123">sciencedirect.com</a>
</div>

## Operations that preserve convexity

In this section we will look at some operations which when gets appled to a convex function doesn't make it non-convex i.e, we will look at operations that preserve the convexity of a given function

### Nonnegative weighted sums

Evidently if $f$ is a convex function and $\alpha \geq 0,$ then the function $\alpha f$ is convex. If $f_{1}$ and $f_{2}$ are both convex functions, then so is their sum $f_{1}+f_{2} .$ Combining nonnegative scaling and addition, we see that the set of convex functions is itself a convex cone: a nonnegative weighted sum of convex functions,
$$
f=w_{1} f_{1}+\cdots+w_{m} f_{m}
$$
is convex. Similarly, a nonnegative weighted sum of concave functions is concave. A nonnegative, nonzero weighted sum of strictly convex (concave) functions is strictly convex (concave).

### Composition with an affine mapping

Suppose $f: \mathbf{R}^{n} \rightarrow \mathbf{R}, A \in \mathbf{R}^{n \times m},$ and $b \in \mathbf{R}^{n} .$ Define $g: \mathbf{R}^{m} \rightarrow \mathbf{R}$ by
$$
g(x)=f(A x+b)
$$
with $\operatorname{dom} g=\{x | A x+b \in \operatorname{dom} f\} .$ Then if $f$ is convex, so is $g ;$ if $f$ is concave, so is $g$

### Pointwise maximum and minimum

If $f_{1}$ and $f_{2}$ are convex functions then their pointwise maximum $f,$ defined by
$$
f(x)=\max \left\{f_{1}(x), f_{2}(x)\right\}
$$
with $\operatorname{dom} f=\operatorname{dom} f_{1} \cap \operatorname{dom} f_{2},$ is also convex.

<div align="center">

<img src="Assets/Img/pointwisemax_semanticScholar.png"/>

source: <a href="https://www.semanticscholar.org/paper/Optimal-Algorithms-in-Multiview-Geometry-Hartley-Kahl/6be7007180120ad42e3b88a879806618ad418930">semanticscholar.org</a>

</div>

## Composition 

In this section we examine conditions on $h: \mathbf{R}^{k} \rightarrow \mathbf{R}$ and $g: \mathbf{R}^{n} \rightarrow \mathbf{R}^{k}$ that guarantee convexity or concavity of their composition $f=h \circ g: \mathbf{R}^{n} \rightarrow \mathbf{R},$ defined by
$$
f(x)=h(g(x)), \quad \operatorname{dom} f=\{x \in \operatorname{dom} g | g(x) \in \operatorname{dom} h\}
$$

in order to verify that f is convex, we just use second order condition i.e, check if $f'' \geq 0$ for $h: \mathbf{R} \rightarrow \mathbf{R}$ and $g: \mathbf{R}^n \rightarrow \mathbf{R}$. we get:

$$
f^{\prime \prime}(x)=h^{\prime \prime}(g(x)) g^{\prime}(x)^{2}+h^{\prime}(g(x)) g^{\prime \prime}(x)
$$
Now suppose, for example, that $\left.g \text { is convex (so } g^{\prime \prime} \geq 0\right)$ and $h$ is convex and nondecreasing (so $\left.h^{\prime \prime} \geq 0 \text { and } h^{\prime} \geq 0\right) .$ It follows from ( 3.9) that $f^{\prime \prime} \geq 0,$ i.e., $f$ is convex. In a similar way, the expression ( 3.9) gives the results:
$f$ is convex if $h$ is convex and nondecreasing, and $g$ is convex,
$f$ is convex if $h$ is convex and nonincreasing, and $g$ is concave,
( 3.10)
$f$ is concave if $h$ is concave and nondecreasing, and $g$ is concave,
$f$ is concave if $h$ is concave and nonincreasing, and $g$ is convex.

we can also extend this idea for vectors as well i.e,
$$
f^{\prime \prime}(x)=g^{\prime}(x)^{T} \nabla^{2} h(g(x)) g^{\prime}(x)+\nabla h(g(x))^{T} g^{\prime \prime}(x)
$$


### Minimization

If $f$ is convex in $(x,y)$, and $C$ is a convex nonempty set, then the function

$$ g(x) = \inf_{y \in C} f(x,y)$$

is convex in $x$.

### Perspective of a function

If $f: \mathbf{R}^{n} \rightarrow \mathbf{R},$ then the perspective of $f$ is the function $g: \mathbf{R}^{n+1} \rightarrow \mathbf{R}$ defined by
$$
g(x, t)=t f(x / t)
$$
with domain
$$
\operatorname{dom} g=\{(x, t) | x / t \in \operatorname{dom} f, t>0\}
$$
The perspective operation preserves convexity: If $f$ is a convex function, then so is its perspective function $g .$ Similarly, if $f$ is concave, then so is $g .$


## The Conjugate Function

The conjugate function $f^{*}(y)$ is the maximum gap between the linear function $y x$ and $f(x),$ as shown by the dashed line in the figure. If $f$ is differentiable, this occurs at a point $x$ where $f^{\prime}(x)=y$ i.e,

$$
f^{*}(y)=\sup _{x \in \operatorname{dom} f}\left(y^{T} x-f(x)\right)
$$

<img src="Assets/Img/fig38.png">

example:

Find the conjugate function of $log(1/x)$

### Basic Properties

* Fenchel's inequality
  * From the definition of conjugate function, we immediately obtain the inequality
    $$
    f(x)+f^{*}(y) \geq x^{T} y
    $$
    for all $x, y .$ This is called Fenchel's inequality (or Young's inequality when $f$ is differentiable).

    For example with $f(x)=(1 / 2) x^{T} Q x,$ where $Q \in \mathbf{S}_{++}^{n},$ we obtain the inequality
    $$
    x^{T} y \leq(1 / 2) x^{T} Q x+(1 / 2) y^{T} Q^{-1} y
    $$
* Conjugate of the conjugate is a original function which holds if $f$ is a convex and $\mathbf{epi} f$ is a closed set.
* the conjugate of a differentiable function $f$ is also called the **Legendre transform** of $f$ (or Fenchel conjugate).
* the conjugate of the sum of *independent* convex functions is the sum of the conjugates.('Independent' means they are functions of different variables.)
* Suppose $A \in \mathbf{R}^{n \times n}$ is nonsingular and $b \in \mathbf{R}^{n} .$ Then the conjugate of $g(x)=$ $f(A x+b)$ is
    $$
    g^{*}(y)=f^{*}\left(A^{-T} y\right)-b^{T} A^{-T} y
    $$
    with $\operatorname{dom} g^{*}=A^{T} \mathrm{dom} f^{*}$

## Quasiconvex function

A function $f: \mathbf{R}^{n} \rightarrow \mathbf{R}$ is called quasiconvex (or unimodal) if its domain and all its sublevel sets
$$
S_{\alpha}=\{x \in \operatorname{dom} f | f(x) \leq \alpha\}
$$
for $\alpha \in \mathbf{R},$ are convex. A function is quasiconcave if $-f$ is quasiconvex, $i . e .,$ every superlevel set $\{x | f(x) \geq \alpha\}$ is convex. A function that is both quasiconvex and quasiconcave is called quasilinear. If a function $f$ is quasilinear, then its domain, and every level set $\{x | f(x)=\alpha\}$ is convex.

<img src="Assets/Img/fig39.png">

we can check if a function is quasi-convex or not by using a variation on jensen's inequality that characterizes quasiconvexity: \
A function $f$ is quasiconvex if and only if the $\mathbf{dom} f$is convex and for any $x, y \in \mathbf{dom}f$ and $0 \leq \theta \leq 1,$

$$ f(\theta x + (1-\theta)y) \leq \max\{ f(x), f(y)\}$$

similarly, we can also check for quasiconvexity and quasi-linear function:
$$ f(\theta x + (1-\theta)y) \geq \max\{ f(x), f(y)\}$$

quasi-linear:
$$ f(\theta x + (1-\theta)y) = \max\{ f(x), f(y)\}$$

### Quasiconvex functions on R

* $f$ is nondecreeasing
* $f$ is nonincreasing
* there is a point $c \in \mathbf{dom}f$ such that for $t\leq c$ (and $t \in \mathbf{dom}f$), $f$ is nonincreasing, and for $t \geq c$ (and $t \in \mathbf{dom}f$), $f$ is nondecreasing.

## Differentiable quasiconvex functions
just like in convex function, we can also use the derivative information to check wether a function is quasi-convex or not:

First-order condition

Second-order condition

## Operations that preserve quasiconvexity

write.

## Log-concave and log-convex functions

A function $f: \mathbf{R}^n \rightarrow \mathbf{R}$ is logrithmically concave or log-concave if $f(x) > 0$ for all $x \in \mathbf{dom}f$ and $\log f$ is concave. It is said to be logrithmically convex concave. 

we can express log-concavity more formally : a function $f: \mathbf{R}^n \rightarrow \mathbf{R}$, with convex domain and $f(x) > 0, \forall x \in \mathbf{dom} f$ , is log-concave iff $\forall x,y \in \mathbf{dom}f$ and $0 \leq \theta \leq 1$, we have

$$ f(\theta x + (1-\theta)y)) \geq f(x)^\theta f(y)^{1-\theta}$$

which suggest that, we can also check for log concavity of a function without logarithms using the above inequaltiy.

### Properties

## Convexity with respect to generalized inequalities


untill now, we are just using the function which return a result in $\mathbf{R}$. but in this section we consider generalizations of the notions of monotonicity and convexity w.r.t generalized inequlatiies.

..... paste

show that the generalized inequality w.r.t $S_{+}$ matrix is convex.:-


