# Tetrahedron

## Four node tetrahedron

## Ten node tetrahedron

## Straight edge tetrahedron

## Isoparametric tetrahedron

## Serendipity tetrahedron

## Lagrange basis

Let's us denote the basis function on tetrahedron element by $\phi_{j}$.
Let's us denote the interpolation points by $\mathbf{x}_{i}$
Then, the Lagrange polynomials are given by:

$$
l_{i} = \sum_{j}{c_{j, i} \phi_{j}}
$$

The coefficients are selected by using following properties of Lagrange polynomials.

$$
l_{i}(\mathbf{x}_{j}) = \delta_{ij}
$$

The Vandermonde matrix for basis $\phi_{j}$ and interpolation points $x_i$ is given below.

$$
\mathbf{V}(i, j) = \phi_{j}(\mathbf{x}_i)
$$

Then, the coefficients are given by

$$
\mathbf{C}= \mathbf{V}^{-1}
$$

:::note
The $j$th column of C denotes the coefficients for $j$th Lagrange polynomial.
:::

:::tip
Lagrange polynomials depends upon the interpolation points and the basis functions. The basis function can be given by simple monomials, orthogonal polynomials, or heirarchical polynomials.
:::

## Monomial based Lagrange polynomials

The monomial based basis functions are given by

$$
\mathcal{P}_{N}=\left\{ x_{1}^{i}x_{2}^{j}x_{3}^{k} :0\le i,j,k;i+j+k\le N\right\}
$$