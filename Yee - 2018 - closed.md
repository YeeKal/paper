## A Probabilistic Roadmap Approach for Systems with Closed

- 1999

1. break the chain loops
2. randomized gradient descent to generate samples
3. tangent space sample to connect neighbor points

## A Kinematics-Based Probabilistic Roadmap Method for Closed Kinematic Chains

- 2001

1. node generation
    - randomly generate $\theta_a$
    - forward kinematics to compute end-frame configuration $g_{la}$
    - inverse kinematics to solve $\theta_p$
    - $\theta=(\theta_a,\theta_p)$,is retained if it is collision-free
2. node connection
    - 

## Randomized path planning for linkages with closed kinematic chains

- 2001

**random samples**

0. kinematic error
$$e(q)=\sum_{k\in B}||J_k(q)-J^{'}_k(q)||^2$$
1. random q in $C_{free}$
2. compare and select q with smaller error(gradient descend)

**connect points: incremental motions**

- on the surface
- step is small enough
- compare tangent space sample and random samples

1. tangent space: SVD on the matrix of the partial derivatives to find the orthonormal basis
2. recursive derivative
$$\begin{bmatrix} X_n \\ Y_n\\1 \end{bmatrix}=\begin{bmatrix} cos(q_n) & -sin(q_n) & l_{n-1}\\ sin(q_n) &  cos(q_n) 0 \\0& 0& 1 \end{bmatrix}\begin{bmatrix} X_{n-1} \\ Y_{n-1}\\1  \end{bmatrix}$$
$$\begin{aligned}
\frac{\partial{X_n}}{\partial{q_i}}&=\begin{cases}cos(q_n)\frac{\partial{X_{n-1}}}{\partial{q_i}}-sin(q_n)\frac{\partial{Y_{n-1}}}{\partial{q_i}} &i\leq n\\ -sin(q_n)X_{n-1}-cos(q_n)Y_{n-1} &i= n  \end{cases}    \\
\frac{\partial{Y_n}}{\partial{q_i}}&=\begin{cases}sin(q_n)\frac{\partial{X_{n-1}}}{\partial{q_i}}-cos(q_n)\frac{\partial{Y_{n-1}}}{\partial{q_i}} &i\leq n\\ cos(q_n)X_{n-1}-sin(q_n)Y_{n-1} &i= n  \end{cases}
\end{aligned}$$
then the position could be computed with the derivatives directly:
$$\begin{aligned}
X_n&=\frac{\partial{Y_n}}{\partial{q_n}}+l_{n-1}\\
Y_n&=-\frac{\partial{X_n}}{\partial{q_n}}
\end{aligned}$$

**tangent space**