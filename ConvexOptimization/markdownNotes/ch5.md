# Chapter 5: Duality

We consider an optimization problem in the standard form (4.1):

$$
\begin{array}{ll}
\operatorname{minimize} & f_{0}(x) \\
\text { subject to } & f_{i}(x) \leq 0, \quad i=1, \ldots, m \\
& h_{i}(x)=0, \quad i=1, \ldots, p
\end{array}\tag{5.1}
$$

with variable $x \in \mathbf{R}^{n} .$ We assume its domain $\mathcal{D}=\bigcap_{i=0}^{m} \operatorname{dom} f_{i} \cap \bigcap_{i=1}^{p} \operatorname{dom} h_{i}$
is nonempty, and denote the optimal value of (5.1) by $p^{*} .$ We do not assume the problem (5.1) is convex.

The basic idea in Lagrangian duality is to take the constraints in (5.1) into account by augmenting the objective function with a weighted sum of the constraint functions. We define the lagrangian $L: \mathbf{R}^{n} \times \mathbf{R}^{m} \times \mathbf{R}^{p} \rightarrow \mathbf{R}$ associated with the problem (5.1) as
$$
L(x, \lambda, \nu)=f_{0}(x)+\sum_{i=1}^{m} \lambda_{i} f_{i}(x)+\sum_{i=1}^{p} \nu_{i} h_{i}(x)
$$
with $\operatorname{dom} L=\mathcal{D} \times \mathbf{R}^{m} \times \mathbf{R}^{p} .$ We refer to $\lambda_{i}$ as the lagrange multiplier associated with the ith inequality constraint $f_{i}(x) \leq 0 ;$ similarly we refer to $\nu_{i}$ as the Lagrange multiplier associated with the $i$ th equality constraint $h_{i}(x)=0 .$ The vectors $\lambda$ and \nu are called the dual variables or Lagrange multiplier vectors associated with the problem (5.1).


### Lagrange Dual Function

We define the lagrange dual function (or just dual function) $g: \mathbf{R}^{m} \times \mathbf{R}^{p} \rightarrow \mathbf{R}$ as the minimum value of the Lagrangian over $x:$ for $\lambda \in \mathbf{R}^{m}, \nu \in \mathbf{R}^{p}$
$$
g(\lambda, \nu)=\inf _{x \in \mathcal{D}} L(x, \lambda, \nu)=\inf _{x \in \mathcal{D}}\left(f_{0}(x)+\sum_{i=1}^{m} \lambda_{i} f_{i}(x)+\sum_{i=1}^{p} \nu_{i} h_{i}(x)\right)
$$


* The dual function of any problem is convex, even if the objective function is non-convex.
* The dual function yields lower bounds on the optimal value $p^*$ of the problem (5.1) i.e, $g(\lambda, \nu) \geq p^*$
* for e.g:-
* 
    if we rewrite the original problem (5.1) as an unconstrained problem,

    $$\operatorname{minimize}f_0(x) + \sum_{i=1}^m {I_{-}(f_i(x))} + \sum_{i=1}^m {I_{0}(h_i(x))}$$

    where, $I_{-} : \mathbf{R} \rightarrow \mathbf{R}$ is the indicator function for the nonpositive reals,

    $$
    I_{-}(u) = \left \{
    \begin{matrix}
    0 & u \leq 0 \\
    \infty & u > 0, 
    \end{matrix}
    \right \}
    $$

    and $I_0$ is the indicator function of {0}. \\
    Now if we reformulate (5.3) we replace the function $I_{-}(u)$ with the linear function $\lambda_i u_i$ where $\lambda_i \geq 0$ and the function $I_0(u)$ with $\nu_iu_i$

    $$
    \text { minimize } \quad L(x, \lambda, \nu)=f_{0}(x)+\sum_{i=1}^{m} \lambda_{i} f_{i}(x)+\sum_{i=1}^{p} \nu_{i} h_{i}(x)
    $$

    here, as you can see, we use a linear or 'soft' displeasure function in place of $I_{-}$ and $I_0$ which act like an underestimator of the indicator function.

    in practice, we use these types of relaxation alot.

## The Lagrange dual function and conjugate function

To recap, the conjuage $f^*$ of a function $f: \mathbf{R} \rightarrow \mathbf{R}$
 is given by 

$$
f^*(y) = \sup_{x \in \mathbf{dom}f} (y^Tx - f(x)).
$$

The conjugate function and Lagrange dual function are closely related. To see one simple connection, consider the problem
$$
\begin{array}{ll}
\operatorname{minimize} & f(x) \\
\text { subject to } & x=0
\end{array}
$$
(which is not very interesting, and solvable by inspection). This problem has Lagrangian $L(x, \nu)=f(x)+\nu^{T} x,$ and dual function
$$
g(\nu)=\inf _{x}\left(f(x)+\nu^{T} x\right)=-\sup _{x}\left((-\nu)^{T} x-f(x)\right)=-f^{*}(-\nu)
$$

## The Lagrange Dual Problem

For each pair $(\lambda, \nu)$ with $\lambda \succeq 0$, the Lagrange dual function gives us a lower bound on the optimal value $p^{\star}$ of the optimization problem (5.1). Thus we have a lower bound that depends on some parameters $\lambda, \nu .$ A natural question is: What is the best lower bound that can be obtained from the Lagrange dual function? This leads to the optimization problem
$$
\begin{aligned}
\text { maximize }& \quad g(\lambda, \nu)\\
\text{subject to} &\quad \lambda \succeq 0
\end{aligned}\tag{5.16}
$$
This problem is called the lagrange dual problem associated with the problem (5.1). In this context the original problem (5.1) is sometimes called the primal problem. The term dual feasible, to describe a pair $(\lambda, \nu)$ with $\lambda \succeq 0$ and $g(\lambda, \nu)>-\infty$ now makes sense. It means, as the name implies, that $(\lambda, \nu)$ is feasible for the dual problem (5.16). We refer to $\left(\lambda^{\star}, \nu^{\star}\right)$ as dual optimal or optimal Lagrange multipliers
if they are optimal for the problem (5.16) The Lagrange dual problem (5.16) is a convex optimization problem, since the objective to be maximized is concave and the constraint is convex. This is the case whether or not the primal problem (5.1) is convex.

### weak duality
The optimal value of the Lagrange dual problem, which we denote $d^{\star}$, is, by definition, the best lower bound on $p^{*}$ that can be obtained from the Lagrange dual function. In particular, we have the simple but important inequality
$d^{\star} \leq p^{\star}$
(5.23)
which holds even if the original problem is not convex. This property is called weak duality.

The weak duality inequality (5.23) holds when $d^{*}$ and $p^{*}$ are infinite. For example, if the primal problem is unbounded below, so that $p^{*}=-\infty,$ we must have $d^{*}=-\infty,$ i.e., the Lagrange dual problem is infeasible. Conversely, if the dual problem is unbounded above, so that $d^{*}=\infty,$ we must have $p^{\star}=\infty,$ i.e., the primal problem is infeasible.
226
We refer to the difference $p^{*}-d^{*}$ as the optimal duality gap of the original problem, since it gives the gap between the optimal value of the primal problem and the best (i.e., greatest) lower bound on it that can be obtained from the Lagrange dual function. The optimal duality gap is always nonnegative.

The bound (5.23) can sometimes be used to find a lower bound on the optimal value of a problem that is difficult to solve, since the dual problem is always convex, and in many cases can be solved efficiently, to find $d^{*}$. As an example, consider the two-way partitioning problem (5.7) described on page 219. The dual problem
is an SDP, maximize $\quad-\mathbf{1}^{T} \nu$
subject to $\quad W+\operatorname{diag}(\nu) \succeq 0$
with variable $\nu \in \mathbf{R}^{n} .$ This problem can be solved efficiently, even for relatively large values of $n,$ such as $n=1000 .$ Its optimal value is a lower bound on the optimal value of the two-way partitioning problem, and is always at least as good as the lower bound (5.8) based on $\lambda_{\min }(W)$

## Strong Duality and Slater's condition

If the equality
$d^{\star}=p^{\star}$
holds, i.e., the optimal duality gap is zero, then we say that strong duality holds. This means that the best bound that can be obtained from the Lagrange dual function is tight.

Strong duality does not, in general, hold. But if the primal problem (5.1) is convex, i.e., of the form
$$
\begin{array}{ll}
\operatorname{minimize} & f_{0}(x) \\
\text { subject to } & f_{i}(x) \leq 0, \quad i=1, \ldots, m \\
& A x=b
\end{array}
$$
with $f_{0}, \ldots, f_{m}$ convex, we usually (but not always) have strong duality. There are many results that establish conditions on the problem, beyond convexity, under which strong duality holds. These conditions are called construint qualifications. One simple constraint qualification is Slater's condition: There exists an $x \in$ relint $\mathcal{D}$ such that
$$
f_{i}(x)<0, \quad i=1, \ldots, m, \quad A x=b
$$
Such a point is sometimes called strictly feasible, since the inequality constraints hold with strict inequalities. Slater's theorem states that strong duality holds, if Slater's condition holds (and the problem is convex).

Slater's condition can be refined when some of the inequality constraint functions $f_{i}$ are affine. If the first $k$ constraint functions $f_{1}, \ldots, f_{k}$ are affine, then strong duality holds provided the following weaker condition holds: There exists an $x \in$ relint $\mathcal{D}$ with
$$
f_{i}(x) \leq 0, \quad i=1, \ldots, k, \quad f_{i}(x)<0, \quad i=k+1, \ldots, m
$$


## KKT Conditions


<!-- KKT conditions for nonconvex problems
As above, let $x^{*}$ and $\left(\lambda^{*}, \nu^{*}\right)$ be any primal and dual optimal points with zero duality gap. since $x^{*}$ minimizes $L\left(x, \lambda^{*}, \nu^{*}\right)$ over $x,$ it follows that its gradient must vanish at $x^{*},$ i.e.,
$$
\nabla f_{0}\left(x^{*}\right)+\sum_{i=1}^{m} \lambda_{i}^{*} \nabla f_{i}\left(x^{*}\right)+\sum_{i=1}^{p} \nu_{i}^{*} \nabla h_{i}\left(x^{*}\right)=0
$$ -->

for any optimization problem with differentiable objective and constraint functions for which strong duality obtains, any pair of primal and dual optimal points must satisfy the KKT conditions (5.49).


$$
\begin{aligned}
f_{i}\left(x^{*}\right) & \leq 0, \quad i=1, \ldots, m \\
h_{i}\left(x^{*}\right) &=0, \quad i=1, \ldots, p \\
\lambda_{i}^{*} & \geq 0, \quad i=1, \ldots, m \\
\lambda_{i}^{*} f_{i}\left(x^{*}\right) &=0, \quad i=1, \ldots, m \\
\nabla f_{0}\left(x^{*}\right)+\sum_{i=1}^{m} \lambda_{i}^{*} \nabla f_{i}\left(x^{*}\right)+\sum_{i=1}^{p} \nu_{i}^{*} \nabla h_{i}\left(x^{*}\right) &=0
\end{aligned}
$$
which are called the Karush-Kuhn-Tucker (KKT) conditions. 

the 4th condition is known as complementry slackness condition because here, we want either $\lambda_i^*$ to be 0 or $f_i(x^*) = 0$ so, they are complementry to eachother... and here, $\lambda$ is our slack variable.