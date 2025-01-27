# Numerical Integration on Line

## Newton-Cotes quadrature

Let $I:=(-1,1)$ be the domain of integration. Let $f$ be a polynomial of degree $n$ on $I$. Then,  we create $n+1$ equidistant points on $\bar{I}$.  Let us denote these points by $\left\{ \xi \right\}_{i=0}^{n}$ :

$$
\xi_{i}=-1+\frac{2i}{n},\forall i=0,\cdots,n
$$

Let $f(\xi)$ be of the following form:

$$
f\left(\xi\right)=\sum_{k=0}^{n}a_{k}\xi^{k}
$$

Consider the following integration

$$
\alpha:=\int_{-1}^{+1}f(\xi)d\xi=\sum_{k=0}^{n}\frac{a_{k}}{k+1}\left[1-\left(-1\right)^{k+1}\right]
$$

The numerical integration is given by :

$$
\sum_{k=0}^{n}w_{k}f\left(\xi_{k}\right)
$$

Then,

$$
\sum_{k=0}^{n}\frac{a_{k}}{k+1}\left[1-\left(-1\right)^{k+1}\right]=\sum_{k=0}^{n}w_{k}f\left(\xi_{k}\right)
$$

Now, by comparing the terms on both sides containing the individual coefficients $a_{k}$ leads to the following system of linear equations:

$$
V_{ab}w_{b}=b_{a},\forall a,b=0,\cdots,n
$$

Where,

$$
V_{ab} = \phi_{a}(\xi_{b}),\quad \phi_{a}:=\xi^{a}
$$
$$
b_a = \frac{1-(-1)^{a+1}}{a+1}
$$
For Newton-Cotes point

$$
{\bf V}=\left[\begin{array}{ccccc} 1 & 1 & 1 & \cdots & 1\\ 0 & 1 & 2 & \cdots & n\\ 0 & 1^{2} & 2^{2} & \cdots & n^{2}\\ \vdots & \vdots & \vdots & \ddots & \vdots\\ 0 & 1^{n} & 2^{n} & \cdots & n^{n} \end{array}\right]
$$

$$
{\bf b}=\left\{ \begin{array}{c} 2\\ n\\ 2n^{2}/3\\ \vdots\\ 2n^{n}/(n+1) \end{array}\right\}
$$

:::note
Note that the weights depends upon $n$
:::

:::note
The Vandermonde matrix is not well conditioned and for $n>7$ some weights are negative. Therefore, Newton-Cotes formulae are mostly used only for low values of $n$
:::

:::info
$n+1$ NC points has order of accuracy $n$.
:::

### Tables of quadrature

Order of accuracy = 1

| Point number | $\xi$ | $w$ |
|:------------:|:-----:|:---:|
|      1       |  -1   |  1  |
|      2       |  -1   |  1  |


Order of accuracy = 2

| Point number | $\xi$ | $w$ |
| ------------ | ----- | --- |
| 1            | -1    | 1/3 |
| 2            | 0     | 4/3 |
| 3            | 1     | 1/3 |


Order of accuracy = 3

| Point number | $\xi$ | $w$ |
| ------------ | ----- | --- |
| 1            | -1    | 1/4 |
| 2            | -1/3  | 3/4 |
| 3            | 1/3   | 3/4 |
| 4            | 1     | 3/4 |

Order of accuracy = 4

| Point number | $\xi$ | $w$   |
| ------------ | ----- | ----- |
| 1            | -1    | 7/45  |
| 2            | -1/2  | 32/45 |
| 3            | 0     | 12/45 |
| 4            | 1/2   | 32/45 |
| 5            | 1     | 7/45  |

Order of accuracy = 5

| Point number | $\xi$ | $w$   |
| ------------ | ----- | ----- |
| 1            | -1    | 19/144  | 
| 2            | -3/5  | 75/144 |
| 3            | -1/5  | 50/144 |
| 4            | 1/5   | 50/144 |
| 5            | 3/5   | 75/144  |
| 6            | 1     | 19/144  |

Order of accuracy = 6

| Point number | $\xi$ | $w$   |
| ------------ | ----- | ----- |
| 1            | -1    | 41/420  |
| 2            | -2/3  | 216/420 |
| 3            | -1/3  | 27/420 |
| 4            | 0     | 272/420 |
| 5            | 1/3   | 27/420 |
| 6            | 2/3   | 216/420  |
| 7            | 1     | 41/420  |

Order of accuracy = 7

| Point number | $\xi$ | $w$     |
| ------------ | ----- | ------- |
| 1            | -1    | 751/8640 |
| 2            | -5/7  | 3577/8640 |
| 3            | -3/7  | 1323/8640 |
| 4            | -1/7  | 2989/8640 |
| 5            | 1/7   | 2989/8640 |
| 6            | 3/7   | 1323/8640 |
| 7            | 5/7   | 3577/8640 |
| 8            | 1     | 751/8640 |

## Legendre Gauss Quadrature

The $N+1$ point Legendre-Gauss quadrature rule is denoted by $\left\{ x_{j}^{G},w_{j}^{G}\right\} _{j=0}^{N}$.

The points $x_{j}^{G}$ are zeros of $P_{N+1}$, that is, zeros of $N+1$ order Legendre polynomial.

$$
P_{N+1}(x_{j}^{G})=0,j=0,1,\cdots,N
$$

and $\left\{ x_{j}^{G}\right\}_{j=0}^{N}$ are the eigenvalues of Jacobi matrix ${\bf J}_{N+1}$.

Weights are given by

$$
w_{j}=\frac{2}{\left[1-\left(x_{j}^{G}\right)^{2}\right]\left[\frac{dP_{N+1}}{dx}\left(x_{j}^{G}\right)\right]^{2}},j=0,\cdots,N
$$

But, we know that

$$
\frac{d}{dx}P_{N+1}\left(x_{j}^{G}\right)=\frac{N+1}{1-\left(x_{j}^{G}\right)^{2}}P_{N}\left(x_{j}^{G}\right)
$$

then weights become

$$
w_{j}=\frac{2\left[1-\left(x_{j}^{G}\right)^{2}\right]}{\left(N+1\right)^{2}\left[P_{N}\left(x_{j}^{G}\right)\right]^{2}},j=0,\cdots,N
$$

:::note
$N+1$  Legendre Gauss-Quadrature rules have order of accuracy of $2N+1$
:::

### Using easifem library

We can generate Legendre Gauss quadrature points by using [easifem](https://www.easifem.com) library. The code is given below:

```fortran
program main
  use easifembase
  implicit none
  integer( i4b ) :: n, ii
  real( dfp ), allocatable :: pt( : ), wt( : )
  type(string) :: msg, astr
  do ii = 1, 10
    n = ii; call callme
  end do
  contains
  subroutine callme
  call reallocate( pt, n, wt, n )
  call LegendreGaussQuadrature( n=n, pt=pt, wt=wt )
  msg = char_lf // char_lf // "### n = " // tostring( n ) // char_lf // char_lf
  call display(msg%chars())
  astr = MdEncode( pt .COLCONCAT. wt )
  call display( astr%chars(), "" )
  end subroutine
end program main
```

### Some Legendre Gauss Quadrature points

Order of accuracy is 1

 | Point | Weight |
 |  --- |  --- |
 | 0 | 2 |

Order of accuracy is 2

 | Point | Weight |
 |  --- |  --- |
 | -0.57735 | 1 |
 | 0.57735 | 1 |

Order of accuracy is 3

 | Point | Weight |
 |  --- |  --- |
 | -0.7746 | 0.55556 |
 | 3.71231E-16 | 0.88889 |
 | 0.7746 | 0.55556 |

Order of accuracy is 4

 | Point | Weight |
 |  --- |  --- |
 | -0.86114 | 0.34785 |
 | -0.33998 | 0.65215 |
 | 0.33998 | 0.65215 |
 | 0.86114 | 0.34785 |

Order of accuracy is 5

 | Point | Weight |
 |  --- |  --- |
 | -0.90618 | 0.23693 |
 | -0.53847 | 0.47863 |
 | 2.66893E-17 | 0.56889 |
 | 0.53847 | 0.47863 |
 | 0.90618 | 0.23693 |

Order of accuracy is 6

 | Point | Weight |
 |  --- |  --- |
 | -0.93247 | 0.17132 |
 | -0.66121 | 0.36076 |
 | -0.23862 | 0.46791 |
 | 0.23862 | 0.46791 |
 | 0.66121 | 0.36076 |
 | 0.93247 | 0.17132 |

Order of accuracy is 7

 | Point | Weight |
 |  --- |  --- |
 | -0.94911 | 0.12948 |
 | -0.74153 | 0.27971 |
 | -0.40585 | 0.38183 |
 | 1.88509E-16 | 0.41796 |
 | 0.40585 | 0.38183 |
 | 0.74153 | 0.27971 |
 | 0.94911 | 0.12948 |

Order of accuracy is 8

 | Point | Weight |
 |  --- |  --- |
 | -0.96029 | 0.10123 |
 | -0.79667 | 0.22238 |
 | -0.52553 | 0.31371 |
 | -0.18343 | 0.36268 |
 | 0.18343 | 0.36268 |
 | 0.52553 | 0.31371 |
 | 0.79667 | 0.22238 |
 | 0.96029 | 0.10123 |

Order of accuracy is 9

 | Point | Weight |
 |  --- |  --- |
 | -0.96816 | 8.12744E-02 |
 | -0.83603 | 0.18065 |
 | -0.61337 | 0.26061 |
 | -0.32425 | 0.31235 |
 | 2.76366E-17 | 0.33024 |
 | 0.32425 | 0.31235 |
 | 0.61337 | 0.26061 |
 | 0.83603 | 0.18065 |
 | 0.96816 | 8.12744E-02 |

Order of accuracy is 10

 | Point | Weight |
 |  --- |  --- |
 | -0.97391 | 6.66713E-02 |
 | -0.86506 | 0.14945 |
 | -0.67941 | 0.21909 |
 | -0.4334 | 0.26927 |
 | -0.14887 | 0.29552 |
 | 0.14887 | 0.29552 |
 | 0.4334 | 0.26927 |
 | 0.67941 | 0.21909 |
 | 0.86506 | 0.14945 |
 | 0.97391 | 6.66713E-02 |

## Legendre Gauss Lobatto Quadrature

The $n+2$ point Legendre Gauss-Lobatto quadrature rule is denoted by $\left\{ x_{j}^{L},w_{j}^{L}\right\} _{j=0}^{n+1}$, which are the eigenvalues of Jacobi Gauss-Lobatto matrix.The weights are given by

$$
w_{j}=\frac{2}{\left(n+2\right)\left(n+1\right)}\frac{1}{\left[P_{n+1}(x_{j}^{R})\right]^{2}},j=0,\cdots,n+1
$$

There is another point of view for understanding the Gauss-Lobatto quadrature points.

> $x_{0}^{L}=-1$ and $x_{n+1}^{L}=1$, the $n$ points $x_{j}^{L},j=1,\cdots n$ are zeros of $P_{n}^{1,1}(x)$ , that is zeros of $\frac{dP_{n+1}}{dx}$

:::note
$N+1$ point Gauss Legendre Lobatto quadrature rule has $2N-1$ order of accuracy.
:::

### Using easifem library

We can generate Legendre Gauss Lobatto quadrature points by using [easifem](https://www.easifem.com) library. The code is given below:

```fortran
PROGRAM main
USE easifembase
IMPLICIT NONE
INTEGER(i4b) :: n, ii
REAL(dfp), ALLOCATABLE :: pt(:), wt(:)
TYPE(string) :: msg, astr
DO ii = 1, 8
  n = ii; CALL callme
END DO
CONTAINS
SUBROUTINE callme
  CALL reallocate(pt, n + 2, wt, n + 2)
  CALL LegendreGaussLobattoQuadrature(n=n, pt=pt, wt=wt)
  msg = char_lf//char_lf//"### n+2 = " &
      & //tostring(n + 2)//char_lf//char_lf
  CALL display(msg%chars())
  astr = MdEncode(pt.COLCONCAT.wt)
  CALL display(astr%chars(), "")
END SUBROUTINE
END PROGRAM main
```
### Some Legendre Gauss Lobatto Quadrature

Three point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 0.33333 |
 | -2.66578E-17 | 1.3333 |
 | 1 | 0.33333 |

4 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 0.16667 |
 | -0.44721 | 0.83333 |
 | 0.44721 | 0.83333 |
 | 1 | 0.16667 |

5 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 0.1 |
 | -0.65465 | 0.54444 |
 | 4.1375E-17 | 0.71111 |
 | 0.65465 | 0.54444 |
 | 1 | 0.1 |

6 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 6.66667E-02 |
 | -0.76506 | 0.37847 |
 | -0.28523 | 0.55486 |
 | 0.28523 | 0.55486 |
 | 0.76506 | 0.37847 |
 | 1 | 6.66667E-02 |

7 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 4.7619E-02 |
 | -0.83022 | 0.27683 |
 | -0.46885 | 0.43175 |
 | 2.39125E-16 | 0.48762 |
 | 0.46885 | 0.43175 |
 | 0.83022 | 0.27683 |
 | 1 | 4.7619E-02 |

8 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 3.57143E-02 |
 | -0.87174 | 0.2107 |
 | -0.5917 | 0.34112 |
 | -0.2093 | 0.41246 |
 | 0.2093 | 0.41246 |
 | 0.5917 | 0.34112 |
 | 0.87174 | 0.2107 |
 | 1 | 3.57143E-02 |

9 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 2.77778E-02 |
 | -0.89976 | 0.1655 |
 | -0.67719 | 0.27454 |
 | -0.36312 | 0.34643 |
 | -2.81541E-16 | 0.37152 |
 | 0.36312 | 0.34643 |
 | 0.67719 | 0.27454 |
 | 0.89976 | 0.1655 |
 | 1 | 2.77778E-02 |

10 point Gauss-Lobatto quadrature

 | Point | Weight |
 |  --- |  --- |
 | -1 | 2.22222E-02 |
 | -0.91953 | 0.13331 |
 | -0.73877 | 0.22489 |
 | -0.47792 | 0.29204 |
 | -0.16528 | 0.32754 |
 | 0.16528 | 0.32754 |
 | 0.47792 | 0.29204 |
 | 0.73877 | 0.22489 |
 | 0.91953 | 0.13331 |
 | 1 | 2.22222E-02 |

## Chebyshev Gauss Quadrature

Let $I:=(-1,1)$ be the domain of integration. Let $f$ be a polynomial of degree $n$ on $I$. Then,  we create $n$ non-equidistant Chebyshev points on $\bar{I}$.  Let us denote these points by $\left\{ \xi \right\}_{i=1}^{n}$ :

Let $f(\xi)$ be of the following form:

$$
f\left(\xi\right)=\sum_{k=1}^{n}a_{k}\xi^{k}
$$

Then, the numerical integration is given by :

$$
\int_{-1}^{1}f(\xi)d\xi \approx \sum_{k=1}^{n}w_{k}f\left(\xi_{k}\right)
$$

In the case of Chebyshev points all weights are equal, that is,

$$
w_{k} = \frac{\pi}{n}
$$

Therefore, 

$$
\int_{-1}^{1}f(\xi)d\xi \approx \frac{\pi}{n} \sum_{k=1}^{n}f\left(\xi_{k}\right)
$$


:::note
The $n$ point Chebyshev Gauss quadrature rules achieve (2n-1)th order of accuracy.
:::

### Using EASIFEM library

We can generate Chebyshev Gauss quadrature points by using [easifem](https://www.easifem.com) library. The code is given below:

```fortran
PROGRAM main
USE easifembase
IMPLICIT NONE
INTEGER(i4b) :: n
REAL(dfp), ALLOCATABLE :: pt(:), wt(:)
TYPE(string) :: msg, astr
INTEGER(i4b) :: ii
DO ii = 1, 10
  n = ii; CALL callme
END DO
CONTAINS
SUBROUTINE callme
  CALL reallocate(pt, n, wt, n)
  CALL Chebyshev1GaussQuadrature(n=n, pt=pt, wt=wt)
    msg = char_lf// char_lf // "### n = " // tostring( n ) // char_lf // char_lf
  CALL display(msg%chars())
  astr = MdEncode(pt.COLCONCAT.wt)
  CALL display(astr%chars(), "")
END SUBROUTINE
END PROGRAM main
```

### Some Chebyshev Gauss Quadrature points

One point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | 1.03412E-13 | 3.1416 |

2 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.70711 | 1.5708 |
 | 0.70711 | 1.5708 |

3 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.86603 | 1.0472 |
 | 1.03412E-13 | 1.0472 |
 | 0.86603 | 1.0472 |

4 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.92388 | 0.7854 |
 | -0.38268 | 0.7854 |
 | 0.38268 | 0.7854 |
 | 0.92388 | 0.7854 |

5 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.95106 | 0.62832 |
 | -0.58779 | 0.62832 |
 | 1.03412E-13 | 0.62832 |
 | 0.58779 | 0.62832 |
 | 0.95106 | 0.62832 |

6 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.96593 | 0.5236 |
 | -0.70711 | 0.5236 |
 | -0.25882 | 0.5236 |
 | 0.25882 | 0.5236 |
 | 0.70711 | 0.5236 |
 | 0.96593 | 0.5236 |

7 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.97493 | 0.4488 |
 | -0.78183 | 0.4488 |
 | -0.43388 | 0.4488 |
 | 1.03412E-13 | 0.4488 |
 | 0.43388 | 0.4488 |
 | 0.78183 | 0.4488 |
 | 0.97493 | 0.4488 |

8 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.98079 | 0.3927 |
 | -0.83147 | 0.3927 |
 | -0.55557 | 0.3927 |
 | -0.19509 | 0.3927 |
 | 0.19509 | 0.3927 |
 | 0.55557 | 0.3927 |
 | 0.83147 | 0.3927 |
 | 0.98079 | 0.3927 |

9 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.98481 | 0.34907 |
 | -0.86603 | 0.34907 |
 | -0.64279 | 0.34907 |
 | -0.34202 | 0.34907 |
 | 1.03412E-13 | 0.34907 |
 | 0.34202 | 0.34907 |
 | 0.64279 | 0.34907 |
 | 0.86603 | 0.34907 |
 | 0.98481 | 0.34907 |

10 point Chebyshev Gauss quadrature

 |  |  |
 |  --- |  --- |
 | -0.98769 | 0.31416 |
 | -0.89101 | 0.31416 |
 | -0.70711 | 0.31416 |
 | -0.45399 | 0.31416 |
 | -0.15643 | 0.31416 |
 | 0.15643 | 0.31416 |
 | 0.45399 | 0.31416 |
 | 0.70711 | 0.31416 |
 | 0.89101 | 0.31416 |
 | 0.98769 | 0.31416 |

## Chebyshev Gauss Lobatto Quadrature

Chebyshev Gauss Lobatto points contains the end points, that is, $-1$ and $+1$

$$
x_{j}^{L}=-\cos\frac{\pi j}{N},j=0,\cdots,N
$$

$$
w_{0}^{R}=w_{N}^{R}=\frac{\pi}{2N}
$$

$$
w_{j}^{R}=\frac{\pi}{N},j=1,\cdots,N-1
$$

:::note
$N+1$ point Chebyshev Gauss Lobatto quadrature rule has $2N-1$ order of accuracy.
:::


### Using by EASIFEM

We can generate Chebyshev Gauss Lobatto quadrature points by using [easifem](https://www.easifem.com) library. The code is given below:

```fortran
PROGRAM main
USE easifembase
IMPLICIT NONE
INTEGER(i4b) :: n, ii
REAL(dfp), ALLOCATABLE :: pt(:), wt(:)
TYPE(string) :: msg, astr
DO ii = 1, 8
  n = ii; CALL callme
END DO
CONTAINS
SUBROUTINE callme
  CALL reallocate(pt, n + 2, wt, n + 2)
  CALL Chebyshev1GaussLobattoQuadrature(n=n, &
    & pt=pt, wt=wt)
  msg = char_lf//char_lf//"### n+2 = " &
      & //tostring(n + 2)//char_lf//char_lf
  CALL display(msg%chars())
  astr = MdEncode(pt.COLCONCAT.wt)
  CALL display(astr%chars(), "")
END SUBROUTINE
END PROGRAM main
```

### Some Chebyshev Gauss Lobatto Quadrature points

3 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.7854 |
 | 1.03412E-13 | 1.5708 |
 | 1 | 0.7854 |

4 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.5236 |
 | -0.5 | 1.0472 |
 | 0.5 | 1.0472 |
 | 1 | 0.5236 |

5 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.3927 |
 | -0.70711 | 0.7854 |
 | 1.03412E-13 | 0.7854 |
 | 0.70711 | 0.7854 |
 | 1 | 0.3927 |

6 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.31416 |
 | -0.80902 | 0.62832 |
 | -0.30902 | 0.62832 |
 | 0.30902 | 0.62832 |
 | 0.80902 | 0.62832 |
 | 1 | 0.31416 |

7 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.2618 |
 | -0.86603 | 0.5236 |
 | -0.5 | 0.5236 |
 | 1.03412E-13 | 0.5236 |
 | 0.5 | 0.5236 |
 | 0.86603 | 0.5236 |
 | 1 | 0.2618 |

8 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.2244 |
 | -0.90097 | 0.4488 |
 | -0.62349 | 0.4488 |
 | -0.22252 | 0.4488 |
 | 0.22252 | 0.4488 |
 | 0.62349 | 0.4488 |
 | 0.90097 | 0.4488 |
 | 1 | 0.2244 |

9 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.19635 |
 | -0.92388 | 0.3927 |
 | -0.70711 | 0.3927 |
 | -0.38268 | 0.3927 |
 | 1.03412E-13 | 0.3927 |
 | 0.38268 | 0.3927 |
 | 0.70711 | 0.3927 |
 | 0.92388 | 0.3927 |
 | 1 | 0.19635 |

10 point Chebyshev Gauss Lobatto

 |  |  |
 |  --- |  --- |
 | -1 | 0.17453 |
 | -0.93969 | 0.34907 |
 | -0.76604 | 0.34907 |
 | -0.5 | 0.34907 |
 | -0.17365 | 0.34907 |
 | 0.17365 | 0.34907 |
 | 0.5 | 0.34907 |
 | 0.76604 | 0.34907 |
 | 0.93969 | 0.34907 |
 | 1 | 0.17453 |






