# Differential complexes

## Introduction

Recently, it has been found by several researchers that differential complexes are an important tool in the study of finite element methods. This is because finite element differential complexes characterise finite element spaces and the operators among them, which are crucial for the stability of numerical formulations [@christiansen2018; @arnold2002], and fast solvers [@hiptmair2007]. Bossavit pointed out that the lowest order mixed finite elements correspond to constructs in algebraic topology known as Whitney forms [@bossavit1998a].

Following complexes have been proposed in the literature:

- de Rham complex[@hiptmair2002; @arnold2006a]
- Stokes complex [@guzman2014; @neilan2015]
- Darcy-Stokes complex [@mardal2002a; @tai2006]
- Elasticity complex [@arnold2006b; @arnold2008]

Stokes complexes and Darcy--Stokes complexes have the same differential operators as the standard de Rham complexes, and the only difference is that the spaces of Stokes and Darcy--Stokes have higher continuity.

The finite element de Rham sequences can be based on incomplete polynomials, such as Nedelec elements of first kind, Raviart-Thomas elements, or complete polynomials, such as Nedelec elements of second kind and Brezzi-Douglas-Marini elements.

Vector elements cannot be represented by Lagrange nodal basis functions.

## De Rham diagram

In 2D, there are two forms:

$$
H^{1}\stackrel{\nabla}{\rightarrow}H(\text{curl})\stackrel{\nabla\times}{\rightarrow}L^{2}
$$

$$
H^{1}\stackrel{\nabla\times}{\rightarrow}H(\text{div})\stackrel{\nabla\cdot}{\rightarrow}L^{2}
$$

In 3D, we have

$$
H^{1}\stackrel{\nabla}{\rightarrow}H(\text{curl})\stackrel{\nabla\times}{\rightarrow}H(\text{div})\stackrel{\nabla\cdot}{\rightarrow}L^{2}
$$

In 2D, the vector-valued **curl** of a scalar function $\phi$ is defined by

$$
\nabla\times\phi=\left(\begin{array}{c}
-\frac{\partial\phi}{\partial x_{2}}\\
\frac{\partial\phi}{\partial x_{1}}
\end{array}\right)=\mathcal{T}\nabla\phi
$$

where, $\mathcal{T}$is a 90 degree counter clockwise rotation operator, that is

$$
\mathcal{T}\left(\begin{array}{c}
x\\
y
\end{array}\right)=\left(\begin{array}{c}
-y\\
x
\end{array}\right)
$$

## Literature review

### Hiptmair's work

Hiptmair [@hiptmair1999; @hiptmair2002] extended Whitney forms to high order, that is, higher degree polynomials and Nedelec elements to any space dimension.

These high order spaces of can be referred to as trimmed polynomial differential forms, since for a given degree, some of the top degree polynomials are (carefully) removed from the space.
These spaces are naturally spanned by products of polynomials with Whitney forms, but this is not a tensor product.

### Arnold-Falk-Winther

Arnold, Falk and Winther developed the idea of Finite Element Exterior Calculus [@arnold2002; @arnold2010]

In [@arnold2006] the construction of Hiptmair was reworked in terms of the Koszul complex, emphasizing the fundamental duality, through degrees of freedom, between the denominated $\mathcal{P}_{r}^{-}\varLambda^{k}$ and $\mathcal{P}_{r}\varLambda^{k}$ spaces there, which correspond to Nédélec's first and second family. It was also placed in a general framework of discretizations of Hilbert complexes by subcomplexes, which has applications to other situations, such as elasticity.

In [@arnold2009] bases are proposed for differential forms in arbitrary space dimension, and these have been used for implementations by [@kirby2014].

### Christiansen's work

On high order finite element spaces of differential forms [@christiansen2016]

- The high order finite element spaces of differential forms due to Raviart-Thomas-Nedelec-Hiptmair fit into the framework of finite element systems, in an elaboration of the finite element exterior calculus of Arnold-Falk-Winther.
- Based on observations by Bossavit, we provide new low order degrees of freedom. As an alternative to existing choices of bases, we provide canonical resolutions in terms of scalar polynomials and Whitney forms.
- A notion of finite element systems (FES) has also been developed. It is a general theory, abstracting the good properties of known mixed finite elements, but allowing for cellular decompositions of space and non-polynomial differential forms. In precisely determined circumstances, they provide good subcomplexes of the de Rham complex. This framework can be used to construct dual finite elements, minimal ones, tensor-products, and upwinded variants.

## Forms

### Coordinates for vectors

Vectors are invariant objects in math. However, description of a vector requires adoptation of coordinate system. A coordinate system is a collection of points. For example in $R^{2}$ the location of a point is given by $(x,y)$, in $R^{3}$ it is given by $\left(x_{1},x_{2},x_{3}\right)$, and in $R^{n}$ it is given by $\left(x_{1},\cdots,x_{n}\right)$. So coordinates are a way of assigning a set of numbers to a point in space.

In other words, coordinates are functions which take points of a space and return a set of numbers. For example, consider a plane $P\subset R^{2}$, then the $x$ coordinate is a function defined as $x:P\rightarrow R$, such that $\forall p\in P$, $x(p)$ and $y(p)$ give us two numbers, $\left(x(p),y(p)\right)$ denoting the coordinates of point $p$.

### Tangent space (1-Form)

1-form is a linear functional which acts on a vector and returns a number. Consider $T_{p}R^{2}$ for some fixed point, $p$, then a linear function $\omega:T_{p}R^{2}\rightarrow R$ is given by

$$
\omega:=\omega\left(\left\langle dx,dy\right\rangle \right)=adx+bdy=\left\langle a,b\right\rangle \cdot\left\langle dx,dy\right\rangle
$$

Hence, to specify a 1-form on $T_{p}R^{2}$ we need two parameters $a,b$.

$$
\begin{aligned}\omega\left(\left\langle dx,dy\right\rangle \right) & =\frac{\left\langle a,b\right\rangle }{\Vert\left\langle a,b\right\rangle \Vert}\cdot\left\langle dx,dy\right\rangle \Vert\left\langle a,b\right\rangle \Vert\\
 & =\Vert\left\langle a,b\right\rangle \Vert\mathcal{P}_{<a,b>}\left\langle dx,dy\right\rangle 
\end{aligned}
$$

> Evaluating a 1-form on a vector is the same as projecting the vector onto some line and then multiplying with the length of that line. Evaluating a 1-form on a vector is the same as projecting onto each coordinate axis, scaling each by some constant and adding the results.

### Tangent space (2-Forms)

A 2-form acts on a pair of vectors and returns a number. 2-form can be written in terms of two 1-form. Let $\omega$ and $\nu$ be two 1-forms, then 2-form is given by

$$
\omega\wedge\nu\left(v_{1},v_{2}\right)=\left|\begin{array}{cc}
\omega\left(v_{1}\right) & \nu\left(v_{1}\right)\\
\omega\left(v_{2}\right) & \nu\left(v_{2}\right)
\end{array}\right|
$$

Properties of 2-form

- Skew-symmetric $\omega\wedge\nu(v_{1},v_{2})=-\omega\wedge\nu(v_{2},v_{1})$
- $\omega\wedge\nu(v,v)=0$
- $\omega\wedge\nu(v_{1},v_{2})=-\nu\wedge\omega(v_{2},v_{1})$
- $\omega\wedge\omega(v_{1},v_{2})=0$
- $\omega\wedge\nu(\alpha v_{1}+\beta v_{2},v_{3})=\alpha\omega\wedge\nu(v_{1},v_{3})+\beta\omega\wedge\nu(v_{2},v_{3})$
- $\omega\wedge\nu(\alpha v_{1},v_{2})=\alpha\omega\wedge\nu(v_{1},v_{2})=\omega\wedge\nu(v_{1},\alpha v_{2})$
- $\left(\omega+\nu\right)\wedge\psi=\omega\wedge\psi+\nu\wedge\psi$

All 2-forms on $T_{p}R^{3}$ can be written as a product of 1-forms. Every 2-form on $T_{p}R^{3}$projects paris of vectors onto some plane and returns the area of the resulting parallelogra, scaled by some constant.

If V is a vector, then $\left\langle V\right\rangle ^{-1}$be the corresponding 1-form.

If $\alpha$ and $\beta$ are 1-forms on $T_{p}R^{3}$ and $V$ is a vector in the plane spaned by $\left\langle \alpha\right\rangle$ and $\left\langle \beta\right\rangle$ then there is a vector, $W$, in this plane such that $\alpha\wedge\beta=\left\langle V\right\rangle ^{-1}\wedge\left\langle W\right\rangle ^{-1}.$

If $\omega_{1}=\alpha_{1}\wedge\beta_{1}$ and $\omega_{2}=\alpha_{2}\wedge\beta_{2}$ are 2-forms on $T_{p}R^{3}$ then there exist 1-forms, $\alpha_{3}$ and $\beta_{3}$ such that $\omega_{1}+\omega_{2}=\alpha_{3}\wedge\beta_{3}$.
