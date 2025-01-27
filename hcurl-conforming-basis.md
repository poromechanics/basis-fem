# Hcurl conforming basis

In finite element computation of Maxwell's equation, it was found that vector-valued finite elements, whose components span $H^{1}$conforming polynomial subspaces, are inappropriate. This finding motivated researchers to develop the theory of **H**(curl)-conforming finite elements.

- This has led to the application of Whitney elements \[204\] that constitute a lowest-order approximation over the element with constant tangential components on the edges.
- However, there is an increasingly widespread interest in the use of higher- order finite element schemes.
- Cubic finite elements were constructed in \[4, 89, 202\] for triangular meshes.
- A basis that allows for arbitrary order of approximation on triangles and tetrahedra can be found in \[203\].
- Other two-dimensional finite elements of variable order have been proposed in \[160\].
- For a more theoretical discussion of degrees of freedom on hybrid meshes with uniform order of approximation see \[115, 116, 139\].
- The problem of deriving bases for arbitrary order approximation of H (curl) and H (div) was addressed mainly in more recent works \[5, 6, 67, 65, 183\].

## Conformity requirements

Consider a domain $\Omega^{h}\subset R^{d}$ covered with a finite element mesh $\mathcal{T}_{p}^{h}$ . Consider a function $\mathbf{v}:\Omega^{h}\rightarrow R^{d}$ such that

1. $v\vert_{K}\in\left[H^{1}\left(K\right)\right]^{d}$ for $\forall K\in\mathcal{T}_{p}^{h}$

2. for each common face $f=\bar{K}_{1}\cap\bar{K}_{2},\bar{K}_{1},\bar{K}_{2}\in\mathcal{T}_{p}^{h}$ , the trace of the tangential component $\boldsymbol{n}\times\boldsymbol{v}$ on $f$ is continuous.

Then $\boldsymbol{v}\in\boldsymbol{H}\left(curl\right)$.

In comparison with the space $H^{1}$, where the requirement of global continuity of approximation constrained the function values at the vertices and on edges and faces, the space $\boldsymbol{H}\left(curl\right)$ has reduced conformity requirements. This appropriately simplifies the hierarchic structure of master element shape functions. Note that there will be no vertex functions in Q, as function values at vertices are not constrained in $\boldsymbol{H}(curl)$.

In the case of scalar $H^{1}$ conforming space, the shape functions restricted to edges vanishes at vertices, in order not to interfere with values of vertex functions. In the $\boldsymbol{H}(curl)$-conforming case, however, tangential components of edge functions do not have to vanish at element vertices anymore, and thus we can use the Legendre polynomials $P_{0},P_{1},\cdots$ to generate the corresponding polynomial subspaces.

Legendre polynomials are a natural choice suggested also by the De Rham diagram, as they appear in tangential components of gradients of scalar edge functions.

## De Rham diagram

In 2D and 3D following relationship is followed.

$$
H^{1}\stackrel{\nabla}{\rightarrow}\boldsymbol{H}(\text{curl})
$$

In other words, every $\boldsymbol{H}(curl)$-conforming element $\mathcal{K}^{curl}:=\left(K,Q,\sum^{curl}\right)$ can be obtained from an appropriate scalar finite element $\mathcal{K}^{1}:=\left(K,W,\sum^{1}\right)$, such that

$$
W\stackrel{\nabla}{\rightarrow}Q
$$
