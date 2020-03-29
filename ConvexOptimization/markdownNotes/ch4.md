
# Chapter4: Convex Optimization problems

In this chapter we will take a look at different type of optimization problems. some of the problem we introduce may not look like a convex optimization problem but with some clever technique like change of variable we can convert them to a solvable (or sometimes tractable) convex optimization problem....

### Anatomy of Convex optimization problem

We use the notation
$$
\begin{array}{cl}
{\operatorname{minimize}} & {f_{0}(x)} \\
{\text { subject to }} & {f_{i}(x) \leq 0, \quad i=1, \ldots, m} \\
{} & {h_{i}(x)=0, \quad i=1, \ldots, p}
\end{array}
$$
to describe the problem of finding an $x$ that minimizes $f_{0}(x)$ among all $x$ that satisfy the conditions $f_{i}(x) \leq 0, i=1, \ldots, m,$ and $h_{i}(x)=0, i=1, \ldots, p .$

* We call $x \in \mathbf{R}^{n}$
the **optimization variable** and the function $f_{0}: \mathbf{R}^{n} \rightarrow \mathbf{R}$ the **objective function or cost function**.
 
* The inequalities $f_{i}(x) \leq 0$ are called **inequality constraints**, and the corresponding functions $f_{i}: \mathbf{R}^{n} \rightarrow \mathbf{R}$ are called the inequality constraint functions.
 
* The equations $h_{i}(x)=0$ are called the **equality constraints**, and the functions $h_{i}: \mathbf{R}^{n} \rightarrow \mathbf{R}$ are the equality constraint functions. If there are no constraints (i.e., $m=p=0$ ) we say the problem ( 4.1) is unconstrained.
 
* The set of points for which the objective and all constraint functions are defined,is called the **domain** of the optimization problem $(4.1) .$
 
* A point $x \in \mathcal{D}$ is **feasible** if it satisfies the constraints $f_{i}(x) \leq 0, i=1, \ldots, m,$ and $h_{i}(x)=0, i=1, \ldots, p$ 
 
* The problem ( 4.1) is said to be **feasible** if there exists at least one feasible point, and **infeasible** otherwise. The set of all feasible points is called the feasible set or the constraint set. 
 
* The optimal value $p^{*}$ of the problem ( 4.1) is a point which minimizes our objective function subjected to the constraints.
We allow $p^{*}$ to take on the extended values $\pm \infty .$ If the problem is infeasible, we have $p^{*}=\infty$ (following the standard convention that the infimum of the empty set 

we also refer to (4.1) as an optimization problem in **standard form**, In the standard form problem we adopt the convention that the right hand side of the inequality and equality constraints are zero. This can always be arranged by subtracting any non zero righthand side: we represent the equality constraint $g_i(x) = \tilde{g}_i(x)$, for example, as $h_i(x) = 0$, where $h_i(x) =g_i(x)−\tilde{g}_i(x)$. In a similar way we express inequalities of the form$f_i(x)≥0$ as−$f_i(x) \leq 0$

with the slight abuse of the notation, we can reformualte our standard convex optimization problem into concave maximization problem, where $f_0$ is concave:
$$
\begin{array}{cl}
{\operatorname{maximize}} & {f_{0}(x)} \\
{\text { subject to }} & {f_{i}(x) \leq 0, \quad i=1, \ldots, m} \\
{} & {h_{i}(x)=0, \quad i=1, \ldots, p}
\end{array}
$$

also, we can readily solve this concave maximization problem by minimzing the covex objective function $-f_0$.

## Equivalent problems
We call 2 problems **equivalent** if from a solution of one, a soluion of the other is readily found, and vice versa. 

### Change of variable

lets suppose we have a function $\phi: \mathbf{R}^n \rightarrow \mathbf{R}^n$ and variable $z=\phi^{-1}(x)$ with image covering the problem domain $\mathcal{D}$. which means $\phi(z) = \phi(\phi^{-1}x) = x$ so, if we modify our standrad form problem w.r.t z we get:


$$
\begin{array}{cl}
{\operatorname{minimize}} & {\tilde{f}_{0}(z)} \\
{\text { subject to }} & {\tilde{f}_{i}(x) \leq 0, \quad i=1, \ldots, m} \\
{} & {\tilde{h}_{i}(x)=0, \quad i=1, \ldots, p}
\end{array}
$$

where, \
$\tilde{f}_i(z) = f_i(\phi(z)),\hspace{10pt} i= 0,....,m\hspace{12pt} \text{and} \hspace{12pt}\tilde{h}_i(z) = h_i(\phi(z)),\hspace{10pt}  i= 1,....,p$


in this scenario we say that the standard form problem (4.1) and the problem (4.4) are related by the *change of variable* or substitution of variable $x= \phi(x)$

### Slack variables

we can convert an inequality constraint into equality constraint by introducing whats called a **slack variable** for example, we can modify our standard form problem (4.1) like this:

$$
\begin{array}{cl}
{\operatorname{minimize}} & {f_{0}(x)} \\
{\text { subject to }} & s_i \geq 0,\\
{} & {f_{i}(x) + s_i = 0, \quad i=1, \ldots, m} \\
{} & {h_{i}(x) = 0, \quad i=1, \ldots, p}
\end{array}
$$

here, by introducing a slack variable $s_i$ we replaces each inequality constraint with an equality constraint at the cost of additional non-negative constraint for the slack variable.

Although, we can also eliminate the equality constraint and retain only inequality constraint but in practice, eliminating them make the problem harder to understand and analyze, or sometimes ruin the the efficiency of an algorithm that solves it.

### Optimizing over some variables

we always have 
$$
\inf_{x,y}f(x,y) = inf_x \tilde{f}(x)
$$

where, $\tilde{f}(x) = inf_y f(x,y)$. which means, we can always minimize a function by first minimizing over some of the variables and then minimizing over the remaining ones.

### Implicit and explicit constraints

As mentioned earlier, we can include any of the constraints *implicitly* in the objective function, by redefining its domain. As an extreme example, the standard form problem can be expressed as the *unconstrained* problem

$$ \operatorname{minimize} F(x),$$

where we define the function F as $f_0$, but with domain restricted to the feasible set:

$\mathbf{dom}F = \{x\in \mathbf{dom}f_0 | f_i(x) \leq 0, i=1,...,m, h_i(x) = 0, i=1,...,p\},$

and $F(x) = f_0(x)$ if it satisfy all the constraint or in this case, if $x \in \mathbf{dom}F$. Equivalently, we can define $F(x)$ to have value $\infty$ for $x$ not feasible. as you can see this problem has the same feasible set, optimal points and optimal value.


## Parameter and oracle problem descriptions

In an oracle model(a.k.a black box model or subroutine model),we do not know $f$ explicitly, but can evaluate $f(x)$ (and usually also some derivatives) at any $x∈\bold{dom}f$. This is referred to as *querying the oracle*, and is usually associated with some cost, such as time. We are also given some prior information about the function, such as convexity and a bound on its values. \
Most of the algorithms we study in part 3 of this book wok with an oracle roblem and can be made more efficient when they are restricted to solve a specific parameter family of problems

## Optimization problem

### Local and global optima

any point which is optimum only in its neighbourhood is said to be locally optimal for example, if we have a point such that by moving to its left or right the $f(x)$ increases then that point is said to be a local minima but if this point gives the smallest value of $f(x)$ among all point then this point is said to be global minimum point.

<div align="center">
<img src="Assets/Img/global-local-optima.png" width=400/>

landscape of a non-convex function
urce: <a href="http://ludovicarnold.altervista.org/teaching/optimization/problem-statement/">Ludovic Arnold</a>
</div>

Although, it is known that any locally optimal point in a convex optimization problem is also globally optimal but for quasiconvex optmization problems it is not true.


// TODO: add minimization over the nonnegative orthant example on pgno. 142


## Quasiconvex optimization


### quasiconvex optimization via convex feasiblity problems

$$
\begin{array}{cl}
\operatorname{find} &x \\
\operatorname{subject}\operatorname{to}& \phi_t(x) \leq 0 \\
{}&f_i(x) \leq 0, \quad i=1,....,m \\
{}&Ax =b,
\tag{4.26}
\end{array}
$$

We assume that the problem is feasible, and startwith an interval $[l,u]$ known to contain the optimal value $p⋆$. We then solve theconvex feasibility problem at its midpoint $t= (l+u)/2$, to determine whether the optimal value is in the lower or upper half of the interval, and update the interval accordingly. This produces a new interval, which also contains the optimal value,but has half the width of the initial interval. This is repeated until the width ofthe interval is small enough:

<img src="Assets/Img/algo41.png">

