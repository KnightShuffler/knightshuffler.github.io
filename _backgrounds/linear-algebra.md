---
flavor: "Some basic properties of vectors, vector spaces and linear transformations, which are used to describe quantum systems."
---
Quantum states are represented using vectors in a complex vector space, called a
Hilbert Space. If you don't know what any of those terms mean, this page has a
basic run down of the things you'll need to know when studying quantum
computing.
## Vectors
### Vector Spaces
The way I think about vectors is that they are objects that can be represented
using an ordered list of numbers. If the collection of these objects follow
[certain properties](https://en.wikipedia.org/wiki/Vector_space#Definition),
then they form a *vector space*.

An example: The vector space 
$$ \mathbb{R}^2 = \left\{\begin{pmatrix}
    x \\
    y
\end{pmatrix} | x,y \in \mathbb{R}\right\}$$

Its elements can be used to represent multiple things like points on a plane,
2 dimensional veclocity of a particle and more.

**Note:** Vectors don't have to be written vertically, if you wanted to write
the elements down horizontally separated by commas, or in any other fashion
as long as you could tell the order of the vector that's fine. I write them down
vertically to be consistent with the idea of column vectors which we'll discuss
in the matrix section.

In general we'll be looking at vector spaces of the
type 
$$ \mathbb{C}^n = \left\{ \begin{pmatrix}
    z_1 \\
    \vdots \\
    z_n
\end{pmatrix} | z_1, ..., z_n \in \mathbb{C} \right\} $$
when studying quantum computing.

The numbers that we use to define our vector space, real or complex, are known
as *scalars*. I'll use $$ \mathbb{F} $$ to represent the set of scalars
henceforth.

Every vector space has a notion of vector addition and scalar
multiplication:

$$
\mathbf{u, v} \in \mathbb{F}^n, c \in \mathbb{F} \\
\mathbf{u} + \mathbf{v} = \begin{pmatrix}
    u_1 + v_1 \\
    \vdots \\
    u_n + v_n
\end{pmatrix} \\
c \cdot \mathbf{v} = \begin{pmatrix}
    c v_1 \\
    \vdots \\
    c v_n 
\end{pmatrix}
$$

The vector $$0$$ is the vector represented by a list of all 0s in the vector
space.

### Linear Combinations and Basis Sets
Suppose we have a set of vectors $$ \{\mathbf{v}_i\}_{i=1}^{n} $$. A vector $$ 
\mathbf{v} = \sum_{i=1}^{n} c_i \mathbf{v}_i $$, for some scalars $$ \{c_i\}_{i=1}^{n} $$,
is a *linear combination* of the the vectors.

The set of all vectors that can be expressed as a linear combination of the
vectors is known as the *span* of those vectors.

A set of vectors are said to be a linearly independent if, and only if, the only
linear combination of the vectors that generates the $$0$$ vector is if all of
the scalars are 0. Otherwise they are linearly dependent.

A set of vectors $$ \{\mathbf{v}_i\}_{i=1}^{n} $$ is called a basis of a vector
space $$V$$ if every vector $$\mathbf{v}$$ in $$V$$ can uniquely be expressed as
a linear combination of the vectors.

There are infinitely many basis sets, *bases*, for any vector space (except for
the vector space containing only the $$0$$ vector).

The *dimension* of a vector space $$V$$ is the number of elements in any of its
bases, written as $$\dim(V)$$.

The standard basis of the vector space $$ \mathbb{F}^n $$ is the set
$$ 
\left\{ \begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0\end{pmatrix},
\begin{pmatrix} 0 \\ 1 \\ \vdots \\ 0\end{pmatrix}, ...,
\begin{pmatrix} 0 \\ 0 \\ \vdots \\ 1\end{pmatrix}
 \right\} 
$$

#### Change of Basis
I introduced vectors as objects that can be represented by ordered lists of
scalars, however, this representation is not unique (except for the $$ 0 $$
vector). Our representation depends on the basis we choose to use.

For example, using the standard basis of $$\mathbb{R}^2$$, we may represent a
vector as $$ \begin{pmatrix} 2 \\1 \end{pmatrix}$$ but under the basis $$
\left\{ 
    \begin{pmatrix} 1 \\ 1 \end{pmatrix}, \begin{pmatrix} 1 \\ -1 \end{pmatrix}
\right\}
$$ we could represent the same vector as $$ \begin{pmatrix} 1.5 \\ 0.5
\end{pmatrix} $$

The representation comes from the scalars in the linear combinations generating
the vector using a basis. If we call the vector in question $$\mathbf{v}$$, then

$$
\mathbf{v} = 2 \begin{pmatrix} 1 \\ 0 \end{pmatrix} + 1 \begin{pmatrix} 0 \\ 1 \end{pmatrix}
= 1.5 \begin{pmatrix} 1 \\ 1 \end{pmatrix} + 0.5 \begin{pmatrix} 1 \\ -1 \end{pmatrix}
$$

**Note:** The ordering of the basis set matters in our representation.

### Inner Products
An *inner product* is a function mapping two vectors in a vector space $$V$$ to a
scalar

$$
\langle\cdot, \cdot\rangle : V \times V \rightarrow \mathbb{F}
$$

with the properties:  
* **Positivity:** $$ \langle\mathbf{v,v}\rangle \geq 0 $$ 
* **Definiteness:** $$ \langle\mathbf{v,v}\rangle = 0 \iff \mathbf{v} = 0 $$
* **Linearity in first argument:** $$ \langle a \mathbf{u} + b \mathbf{v}, \mathbf{w}\rangle = 
a\langle\mathbf{u}, \mathbf{w}\rangle + b\langle\mathbf{v}, \mathbf{w}\rangle $$
* **Conjugate Symmetry:** $$ \langle \mathbf{u}, \mathbf{v} \rangle = 
\overline{\langle \mathbf{v}, \mathbf{u} \rangle} $$

#### Dot Product
The standard inner product, also called the *dot product*, for $$\mathbb{R}^n$$:

$$
\mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^{n} u_i v_i
$$

The dot product can be generalize for $$\mathbb{C}^n$$:

$$
\mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^{n} \overline{u_i}v_i
$$

The *norm* of a vector under a given inner product is defined as

$$
\|\mathbf{v}\| = \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}
$$

#### Norm
For the dot product, the norm looks becomes:

$$
\|\mathbf{v}\| = \sqrt{\sum_{i=1}^{n}\overline{v_i}v_i} = 
\sqrt{\sum_{i=1}^{n}|v_i|^2}
$$

Using the dot product and its norm, we can find the angle between two vectors:

$$
\cos \theta = \frac{\Re(\mathbf{u} \cdot \mathbf{v})}{\|\mathbf{u}\|\|\mathbf{v}\|}
$$

#### Orthogonality
Two vectors are said to be *othogonal* if their inner product is 0.

A set of mutually orthogonal vectors each with a norm of 1, they are called an
*orthonormal* set of vectors.

Given an orthogonal basis $$ \{\mathbf{e}_1, ..., \mathbf{e}_n\} $$, of a vector
space $$ V $$, we can find the linear combination of the basis to produce any
vector $$\mathbf{v}$$ like:

$$
\mathbf{v} = \sum_{i=1}^{n} \frac{\langle \mathbf{e}_i, \mathbf{v} \rangle}{\|\mathbf{e}_i\|} \mathbf{e}_i
$$

Each term in this sum is called the *projection* of $$\mathbf{v}$$ on $$\mathbf{e}_i$$

## Matrices and Linear Operators
### Linear Operators
A *linear operator* is a linear function mapping elements of a vector
space $$U$$ to another vector space $$V$$.

$$
\operatorname{T} : U \rightarrow V \\
\forall \mathbf{u, v} \in U, \forall \alpha, \beta \in \mathbb{F} \\
\operatorname{T}(\alpha \mathbf{u} + \beta \mathbf{v}) = 
\alpha \operatorname{T}(\mathbf{u}) + \beta \operatorname{T}(\mathbf{v})
$$

The linear nature of an operator means that we only need to know how the 
operator acts on the elements of a basis to understand how it acts on any
element of the domain.

We can represent linear operators (just gonna call them operators now) using
2 dimensional arrays of scalars, with $$\dim(V)$$ rows and $$\dim(U)$$ columns,
called matrices (singular, matrix).

### Matrices
Let's take a simple example of an operator $$ \operatorname{T}: \mathbb{R}^2 
\rightarrow \mathbb{R}^2 $$ that rotates the input vector about the origin,
counter-clockwise by 90 degrees.


$$
\operatorname{T} \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \color{Blue}{\begin{pmatrix} 0 \\ 1 \end{pmatrix}} \\
\operatorname{T} \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \color{Red}{\begin{pmatrix} -1 \\ 0 \end{pmatrix}}
$$

We can construct a matrix $$\operatorname{M}$$ to represent $$\operatorname{T}$$
using the standard basis for representing our vectors with 
ordering $$ \left\{\begin{pmatrix} 1 \\ 0 \end{pmatrix} , \begin{pmatrix} 0 \\ 1 
\end{pmatrix}\right\} $$ as

$$
\operatorname{M} = \begin{bmatrix}
    \color{Blue}{0} & \color{Red}{-1} \\
    \color{Blue}{1} & \color{Red}{0}
\end{bmatrix}
$$

If we have ordered bases for the operator's domain and range we can construct a
matrix to represent the operator by:
1. Calculating the output of the operator on basis vectors of the domain
   according to the basis of the range, written vertically.
2. Ordering these outputs left to right in the order of the domain's basis.

If not mentioned, we can assume that the standard basis was used to construct a
matrix.

#### Notation
* A matrix with m rows and n columns is an $$ m\times n $$ matrix.
* We can generalize the elements of a matrix like so: $$ \operatorname{M} = 
[m_{ij}]$$, here $$m_{ij}$$ is the element in the i<sup>th</sup> row and 
j<sup>th</sup> column.
* A *square matrix* has equal number of rows and columns.
* The main diagonal elements of a matrix are the elements $$m_{ii}$$, also
  called the *diagonal elements*.
  
We'll continue to study operators through their representations as matrices,
focusing mainly on square matrices.

### Transpose and Adjoint

The transpose operation mirrors the elements of the matrix about the main
diagonal.

$$
\operatorname{M} = [m_{ij}] \\
\operatorname{M}^\top = [m_{ji}]
$$

If the matrix isn't a square matrix, its dimensions will change after
transposition.

A *symmetric matrix* does not change after taking its transpose.

The adjoint operation takes the complex conjugate of every element and then
takes the transposes the matrix.

$$
\operatorname{M}^\dagger = [\overline{m_{ji}}]
$$

A *Hermitian matrix* does not change after taking its adjoint.

### Matrix Representation of Vectors
Vectors in represented in any choice of basis can be written as matrices with
* a single column, a *column vector*.
* a single row, a *row vector*.

By convention, we usually use column vectors, so we can use the vector's name to
refer to its column matrix as well. We can get row vectors by taking the
transpose or adjoint of a column vector. We can see why this is useful when we
talk about matrix multiplication.

### Matrix Multiplication
#### Dot Product
Remember that the dot product of two real vectors $$ \textbf{u}, \textbf{v} $$
was calculated as a sum of the products of their corresponding elements. We can
represent this as the product of the row vector representing $$ \textbf{u} $$
and the column vector representing $$ \textbf{v} $$.

$$
\textbf{u}\cdot\textbf{v} = \textbf{u}^\top \textbf{v} = \sum_{i} u_i v_i
$$

This is how we classify a row-column product.

For complex vectors, we needed to take the complex conjugate of the first
vector's elements, so we can represent the complex dot product as a row-column
product:

$$
\textbf{u}\cdot\textbf{v} = \textbf{u}^\dagger \textbf{v} = 
\sum_{i} \overline{u_i} v_i
$$


#### Matrix Vector Multiplication
Matrix multiplication between a matrix and a column vector gives us the output
on applying the operator on the vector.

An $$ m  \times n $$ matrix will act on a column vector of dimension $$ n \times
1 $$ to give a resultant column vector of dimension $$ m \times 1 $$.

Recall that the columns of a matrix tells us where the basis vectors of the
space will end up after applying the operator. Since every vector can be written
as a linear combination of the basis vectors, and by using the property of
linearity, we can easily calculate the product. Here's an example:

$$
\operatorname{M} = \begin{bmatrix}
    \color{Red}{1} & \color{Blue}{2} \\
    \color{Red}{3} & \color{Blue}{4} \\
    \color{Red}{5} & \color{Blue}{6}
\end{bmatrix}, 
\textbf{v} = \begin{bmatrix} x \\ y \end{bmatrix} = 
x \begin{bmatrix} 1 \\ 0 \end{bmatrix} + y \begin{bmatrix} 0 \\ 1 \end{bmatrix} 

\\

\operatorname{M}\textbf{v} = 

x \begin{bmatrix}
    \color{Red}{1} \\
    \color{Red}{3} \\
    \color{Red}{5}
\end{bmatrix} + 

y \begin{bmatrix}
    \color{Blue}{2} \\
    \color{Blue}{4} \\
    \color{Blue}{6}
\end{bmatrix} = 

\begin{bmatrix}
    \color{Red}{1} \cdot x + \color{Blue}{2} \cdot y \\
    \color{Red}{3} \cdot x + \color{Blue}{4} \cdot y \\
    \color{Red}{5} \cdot x + \color{Blue}{6} \cdot y
\end{bmatrix}

$$

If you notice, each element of the product happens to be a row-column product
of each row of the matrix with the column vector. We can use this to write the
general form of matrix-vector products.

$$
[\operatorname{M}\textbf{v}]_{i} = \sum_{j=1}^{n} m_{ij} v_j
$$

#### Matrix Matrix Multiplication
We can calculate the matrix for a composition of operators by finding the
product of their matrices.

Let's say the operators $$ \operatorname{F}, \operatorname{G} $$ corresponnd to
matrices $$ \operatorname{M}_F, \operatorname{M}_G $$ respectively. Then the
product $$ \operatorname{M}_F \operatorname{M}_G $$ will represent the
composition $$ \operatorname{F} \circ \operatorname{G} $$

The columns of $$\operatorname{M}_G$$ are where the basis vectors 
of $$\operatorname{G}$$'s domain map to in its range. So a product
of $$\operatorname{F}$$ with the columns of $$\operatorname{G}$$ give us where
the columns of $$\operatorname{G}$$ map to in $$\operatorname{F}$$'s range, ie
these vectors are where the basis vectors of the domain map to in the range
of $$\operatorname{F}$$ after the composition.

The resultant matrix is just the matrix-vector products of the first matrix and
the second matrix's columns.

In general if $$\operatorname{X}$$ is an $$ m \times n $$ matrix
and $$\operatorname{Y}$$ is an $$ n \times p $$ matrix then their product,
an $$ m \times p $$ matrix can be found with the calculations:

$$
[\operatorname{XY}]_{ik} = \sum_{j = 1}^{n} x_{ij} y_{jk}
$$

As an example:

$$
\operatorname{X} = \begin{bmatrix}
    \color{Red}{1} & \color{Blue}{2} \\ 
    \color{Red}{3} & \color{Blue}{4} \\
    \color{Red}{5} & \color{Blue}{6} \\
    \color{Red}{7} & \color{Blue}{8}
\end{bmatrix}_{4 \times 2},
\operatorname{Y} = \begin{bmatrix}
    \color{Cyan}{a} & \color{Magenta}{c} & \color{Green}{e} \\
    \color{Cyan}{b} & \color{Magenta}{d} & \color{Green}{f}
\end{bmatrix}_{2 \times 3} \\

\operatorname{XY} = \begin{bmatrix}
\color{Red}{1} \cdot \color{Cyan}{a} + \color{Blue}{2} \cdot \color{Cyan}{b} & \color{Red}{1} \cdot \color{Magenta}{c} + \color{Blue}{2} \cdot \color{Magenta}{d} & \color{Red}{1} \cdot \color{Green}{e} + \color{Blue}{2} \cdot \color{Green}{f} \\
\color{Red}{3} \cdot \color{Cyan}{a} + \color{Blue}{4} \cdot \color{Cyan}{b} & \color{Red}{3} \cdot \color{Magenta}{c} + \color{Blue}{4} \cdot \color{Magenta}{d} & \color{Red}{3} \cdot \color{Green}{e} + \color{Blue}{4} \cdot \color{Green}{f} \\
\color{Red}{5} \cdot \color{Cyan}{a} + \color{Blue}{6} \cdot \color{Cyan}{b} & \color{Red}{5} \cdot \color{Magenta}{c} + \color{Blue}{6} \cdot \color{Magenta}{d} & \color{Red}{5} \cdot \color{Green}{e} + \color{Blue}{6} \cdot \color{Green}{f} \\
\color{Red}{7} \cdot \color{Cyan}{a} + \color{Blue}{8} \cdot \color{Cyan}{b} & \color{Red}{7} \cdot \color{Magenta}{c} + \color{Blue}{8} \cdot \color{Magenta}{d} & \color{Red}{7} \cdot \color{Green}{e} + \color{Blue}{8} \cdot \color{Green}{f}
\end{bmatrix}_{4 \times 3}
$$