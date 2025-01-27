# Hexahedron

## Hexahedron8

## Hexahedron27

## Hexahedron20

## Straight edge hexahedron

## Isoparametric hexahedron

## Serendipity hexahedron

## Lagrange polynomials

## Tensor-product based basis


## Hierarchical basis

A hexahedron finite element is given by

$$
\mathcal{K}_{B} = \left ( K_{B}, \mathbb{W}_{B}, \sum_{B}^{} \right )
$$

where, $K_{B}$ denotes the biunit hexahedron reference element, which is given by

$$
K_{B} := \left\{ \mathbf{\xi} \in \mathbb{R}^{3}, \Vert \xi \Vert \le 1 \right\},
$$

and $W_{B}$ is the polynomial space, which is given by

$$
\mathbb{W}_{B}:=\left\{ w\in\mathcal{Q}_{p^{b,1},p^{b,2},p^{b,3}};w\vert_{s_{i}}\in\mathcal{Q}_{p^{s_{i},1}p^{s_{i},2}};w\vert_{e_{i}}\in\mathcal{P}_{p^{e_{j}}}\left(e_{j}\right)\right\}
$$

where, $i=1,\cdots, 6$ and $j=1, \cdots, 12$ denote the face and edges of hexahedron.

and

$$
\mathcal{Q}_{p,q,r}=\left\{ \xi_{1}^{i}\xi_{2}^{j} \xi_{3}^{k}\vert 0 \le i\le p, 0 \le j\le q, 0 \le k\le q \right\}
$$

The set of degrees of freedom $\sum_{B}$ will be uniquely identified by the a concrete choice of basis in $\mathbb{W}_B$

In above definition we denote by $p^{b,1}, p^{b,2}, p^{b,3}$ the order of polynomial in the interior of element in x, y and z directions, respectively.

There are six faces in a hexahedron which are denoted by $s_1$, $s_2$, $\cdots$, $s_6$. Each face, $s_{i}$, we have two local directions. These directions are denoted by 1, and 2. In this way, $p^{s_i,1}$ and $p^{s_i,2}$ denote the order of polynomial approximation on face $s_i$ in the 1 and 2 direction, respectively.

There are 12 edges in a hexahedron which are denoted by $e_1$ to $e_{12}$. $p^{e_j}$ denotes the order of polynomial approximation on edge $e_{j}$.

:::{.callout-note appearance="simple"}
In 3D the minimum rule controls the order of approximation on both edge and face. Local orders on faces cannot be more than the minimum of the order of approximation associated with the interior of the adjacenet elements. Local order of approximation on the edges cannot be more than the orders corresponding to faces sharing that edge.
:::

### Affine coordiantes

$$
\lambda_{1} = \frac{1}{2}(1+\xi_{1})
$$

$$
\lambda_{2} = \frac{1}{2}(1-\xi_{1})
$$

$$
\lambda_{3} = \frac{1}{2}(1+\xi_{2})
$$

$$
\lambda_{4} = \frac{1}{2}(1-\xi_{2})
$$

$$
\lambda_{5} = \frac{1}{2}(1+\xi_{3})
$$

$$
\lambda_{6} = \frac{1}{2}(1-\xi_{3})
$$


### Vertex basis

There are 8 vertices, their number and coordinates are given by

| id  | $\xi_{1}$ | $\xi_{2}$ | $\xi_{3}$ |
| --- | --------- | --------- | --------- |
| 1   | -1        | -1        | -1        |
| 2   | +1        | -1        | -1        |
| 3   | +1        | +1        | -1        |
| 4   | -1        | +1        | -1        |
| 5   | -1        | -1        | +1        |
| 6   | +1        | -1        | +1        |
| 7   | +1        | +1        | +1        |
| 8   | -1        | +1        | +1        |

For each vertex we have a vertex basis. Therefore, we have a total number of 8 vertex basis in a hexahedron. These basis will be denoted by $\phi^{v_1}_B$ to $\phi^{v_8}_B$.

$$
\phi_{B}^{v_1} = l_{0}(\xi_1) l_{0}(\xi_2) l_{0}(\xi_3)
$$

$$
\phi_{B}^{v_2} = l_{1}(\xi_1) l_{0}(\xi_2) l_{0}(\xi_3)
$$

$$
\phi_{B}^{v_3} = l_{1}(\xi_1) l_{1}(\xi_2) l_{0}(\xi_3)
$$

$$
\phi_{B}^{v_4} = l_{0}(\xi_1) l_{1}(\xi_2) l_{0}(\xi_3)
$$

$$
\phi_{B}^{v_5} = l_{0}(\xi_1) l_{0}(\xi_2) l_{1}(\xi_3)
$$

$$
\phi_{B}^{v_6} = l_{1}(\xi_1) l_{0}(\xi_2) l_{1}(\xi_3)
$$

$$
\phi_{B}^{v_7} = l_{1}(\xi_1) l_{1}(\xi_2) l_{1}(\xi_3)
$$

$$
\phi_{B}^{v_8} = l_{0}(\xi_1) l_{1}(\xi_2) l_{1}(\xi_3)
$$

where,

$$
l_{0}(y) = \frac{1}{2}(1-y)
$$

$$
l_{1}(y) = \frac{1}{2}(1+y)
$$

### Edge basis

There are 12 edges. These edges are oriented along the positive x, y, and z axis.

| p1 | p2 | axis |
| --- | --- | --- |
| 1 | 2 | x |
| 4 | 3 | x |
| 5 | 6 | x |
| 8 | 7 | x |
| 1 | 4 | y |
| 2 | 3 | y |
| 5 | 8 | y |
| 6 | 7 | y |
| 1 | 5 | z |
| 2 | 6 | z |
| 3 | 7 | z |
| 4 | 8 | z |

:::{.callout-note appearance="simple"}
On an edge $e_{j}$ only one of the coordinates changes, the remaining coordinates remain fixed (either 1 or -1).
:::

Therefore, we can write the edge bubble basis function as:

$$
\phi^{e_j}_{k} = l_{d_1}(\xi_1) l_{d_2}(\xi_2) l_{d_3}(\xi_3)
$$

:::{.callout-note  title="edge on x axis"}
For the edges along the x-axis the value of $d_2$ and $d_3$ will be either 0 or 1 depending on the value of y and z coordinates on these edges. If the y coordiantes is $+1$ then the value of $d_2$ will be $1$, otherwise it will be $0$. Similarly for $z$ and $d_3$. The value of $d_1$ would be greater than or equal to 2.
:::

:::{.callout-note title="edge on y axis"}
For the edges along the y-axis the value of $d_1$ and $d_3$ will be either 0 or 1 depending on the value of x and z coordinates on these edges. If the x coordiantes is $+1$ then the value of $d_1$ will be $1$, otherwise it will be $0$. Similarly, for $z$ and $d_3$. The value of $d_2$ would be greater than or equal to 2.
:::

:::{.callout-note title="edge on z axis"}
For the edges along the z-axis the value of $d_1$ and $d_2$ will be either 0 or 1 depending on the value of x and z coordinates on these edges. If the x coordiantes is $+1$ then the value of $d_1$ will be $1$, otherwise it will be $0$. Similarly, for $y$ and $d_2$. The value of $d_3$ would be greater than or equal to 2.
:::

### Facets bubble basis

Before we derive the basis functions on the hexahedron we should fix some notations.

There are 6 faces, two faces are normal to x-axis, two are normal to y-axis, and two faces are normal to z-axis. In this way, on each face, only two coordiantes changes. These two local direction will match the appropriate pair of global axes in lexicographic order.

We will denote the face functions by

$$
\phi^{s_{i}}_{n_1, n_2}, 2 \le n_1 \le p^{s_i,1}, 2 \le n_2 \le p^{s_i,2}
$$

These functions are given by

$$
\phi^{s_{i}}_{n_1, n_2}=l_{d_1}(\xi_1)l_{d_2}(\xi_2)l_{d_3}(\xi_3)
$$

- On faces which are normal to x-axis, $d_1$ is 1 if $x=1$, and $d_1$ is 0 if $x=-1$.
- On faces which are normal to y-axis, $d_2$ is 1 if $y=1$, and $d_2$ is 0 if $y=-1$.
- On faces which are normal to z-axis, $d_3$ is 1 if $z=1$, and $d_3$ is 0 if $z=-1$.

### Cell bubble basis

The cell bubble basis are denoted by

$$
\phi^{b}_{n_1, n_2, n_3}, 2 \le n_1 \le p^{b,1}, 2 \le n_2 \le p^{b,2}, 2 \le n_3 \le p^{b,3}
$$

### Summary

| type  | order                | dim | entity |
| ---   | -------------------- | --- | --- |
| Vertex| always               | 1                 | 1 |
| Edge  | $p^{e_j} \ge 2$      | $p^{e_j}-1$                | 12 |
| Facet | $p^{s_i,1:2} \ge 2$  | $(p^{s_i,1}-1)(p^{s_i,2}-1)$  | 6 |
| Cell  | $p^{b,1:3} \ge 2$    | $(p^{b,1}-1)(p^{b,2}-1)(p^{b,3}-1)$| 1 |
