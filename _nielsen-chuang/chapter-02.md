---
title: Introduction to quantum mechanics
---

> Quantum mechanics is the most accurate and complete description of the world
> known.

## 2.1 Linear algebra
The mathematical model of quantum computing is manipulating vectors in a complex
vector space $$ \mathbb{C}^n $$. These vectors represent the *quantum state* of
the system being described.

We'll use the following mathematical notation:

<table>
    <tr style="border-bottom: 2px solid; background-color: #CFD4D3">
        <th style="border-right: 1px solid"> Notation </th>
        <th> Description </th>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$z^*$$</td>
        <td>Complex conjugate of the complex number <script type="math/tex">z</script></td>
    </tr>
    <tr>
        <td style="border-right: 1px solid"> $$ \mathbf{0} $$ </td>
        <td>The zero vector</td>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$| \psi \rangle$$</td>
        <td>A ket. Can be thought of like a column vector</td>
    </tr>
        <td style="border-right: 1px solid">$$\langle \psi |$$</td>
        <td>A bra, the dual of the ket. Can be thought of as a row vector</td>
    <tr>
        <td style="border-right: 1px solid">$$\langle \psi | \phi \rangle$$</td>
        <td>The inner product of <script type="math/tex">|\psi \rangle</script> and <script type="math/tex">| \phi \rangle</script> </td>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$| \psi \rangle \otimes | \phi \rangle$$</td>
        <td>The tensor product of <script type="math/tex">|\psi \rangle</script> and <script type="math/tex">| \phi \rangle</script> </td>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$A^*$$</td>
        <td>The complex conjugate of the matrix <script type="math/tex">A</script></td>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$A^T$$</td>
        <td>The transpose of the matrix <script type="math/tex">A</script></td>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$A^\dagger$$</td>
        <td>The Hermitian conjugate or adjoint of the matrix <script type="math/tex">A</script>, <script type="math/tex">A^\dagger = (A^T)^*</script></td>
    </tr>
    <tr>
        <td style="border-right: 1px solid">$$\langle \psi | A | \phi \rangle$$</td>
        <td>The inner product between <script type="math/tex">| \psi \rangle</script> and <script type="math/tex">A | \phi \rangle</script> <br>
        Also the inner product between <script type="math/tex">A^\dagger |\psi \rangle</script> and <script type="math/tex">| \phi \rangle</script> </td>
    </tr>
</table>

### 2.1.1 Bases and linear independence
A linear combination of kets is a weighted sum of the vectors, where the
weights can be any complex number.

$$ | \psi \rangle = \sum_i a_i | v_i \rangle $$

A set of vectors $$ \{ | v_1 \rangle, \dots , | v_n \rangle \} $$ is said to be
linearly independent if the only they have a unique linear combination (when all
the weights are 0) that gives us the zero vector.

$$ \mathbf{0} = \sum_i 0 | v_i \rangle $$

A set of $$ n $$ linearly independent vectors forms a *basis* of an $$ n $$-dimensional
vector space. Every vector in the vector space can be written as a unique linear
combination of the basis vectors.

$$
\text{ Two bases of } \mathbb{C}^2 \\

\begin{array}{c|c}
    | a_1 \rangle = \begin{bmatrix}
        1 \\ 0
    \end{bmatrix}, | a_2 \rangle = \begin{bmatrix}
        0 \\ 1
    \end{bmatrix} & 

    | b_1 \rangle = \begin{bmatrix}
        1 \\ 1
    \end{bmatrix}, | b_2 \rangle = \begin{bmatrix}
        1 \\ -1
    \end{bmatrix} \\
\end{array} \\

\begin{aligned}
    | \psi \rangle &= \begin{bmatrix}
                            2 \\ 1
                      \end{bmatrix} \\
                   &= 2| a_1 \rangle + 1 | a_2 \rangle \\
                   &= 1.5 | b_1 \rangle + 0.5 | b_2 \rangle 
\end{aligned}

$$

### 2.1.2 Linear operators and matrices
A linear operator $$ A: V \rightarrow W $$ is a linear function mapping from vector
space to vector space.

$$
A \left( \sum_i a_i | v_i \rangle \right) = \sum_i a_i A | v_i \rangle
$$

Some examples:
* $$ I_V $$ is the identity operator in vector space $$ V $$, if there is no
  ambiguity then we can remove the subscript. It maps the input vector onto
  itself:  
$$ I | \psi \rangle = | \psi \rangle  $$
* $$ \mathbf{0} $$ is the zero operator, it maps the input vector to the
  zero vector:  
$$ \mathbf{0} | \psi \rangle = \mathbf{0} $$

These operators can be represented with matrices, for example in
the $$ \mathbb{C}^2 $$ vector space:

$$
\begin{array}{c|c}
    I \equiv \begin{bmatrix}
        1 & 0 \\
        0 & 1
    \end{bmatrix} &

    \mathbf{0} \equiv \begin{bmatrix}
        0 & 0 \\
        0 & 0
    \end{bmatrix}
\end{array}
$$

If we look at kets as column vectors, we can calculate the output of a linear
operator with a matrix-vector product.

### 2.1.3 The Pauli matrices
The following four matrices called the *Pauli matrices* will be very useful when
studying quantum computing:

$$
\begin{array}{c c}
    \sigma_0 \equiv I \equiv \begin{bmatrix}
        1 & 0 \\
        0 & 1
    \end{bmatrix} &
    \sigma_1 \equiv \sigma_x \equiv X \equiv \begin{bmatrix}
        0 & 1 \\
        1 & 0
    \end{bmatrix} \\

    \sigma_2 \equiv \sigma_y \equiv Y \equiv \begin{bmatrix}
        0 & -i \\
        i & 0
    \end{bmatrix} &

    \sigma_3 \equiv \sigma_z \equiv Z \equiv \begin{bmatrix}
        1 & 0 \\
        0 & -1
    \end{bmatrix}
\end{array}
$$

### 2.1.4 Inner products
An *inner product* is a function that maps two vectors from a vector space to a
complex number. Let's use the notation $$ ( | \psi \rangle , | \phi \rangle ) $$
to represent the inner product between $$ | \psi \rangle $$ and $$ | \phi \rangle $$.

The inner product must follow these properties:  
* **Linearity in the second argument**:  
$$ ( | a \rangle , \sum_i \lambda_i | b_i \rangle ) = \sum_i \lambda_i ( | a \rangle , | b_i \rangle ) $$
* **Conjugate symmetry**:  
$$ ( | a \rangle , | b \rangle ) = ( | b \rangle , | a \rangle )^* $$
* **Positive-definiteness**:  
$$ ( | a \rangle , | a \rangle ) \geq 0 $$ and  
$$ ( | a \rangle , | a \rangle ) = 0 \text{ iff } | a \rangle = \mathbf{0} $$


#### Dot product
The dot product is an inner product of $$ \mathbb{C}^n $$ defined as:

$$
\begin{aligned}
    ( | v \rangle , | w \rangle )   & \equiv ( (v_1, ..., v_n), (w_1, ..., w_n) ) \\
                                    & = \sum_{i=1}^{n} v_i^* w_i \\
                                    & = [v_1^*, \dots, v_n^*] \begin{bmatrix} w_1 \\ \vdots \\ w_n \end{bmatrix}
\end{aligned}
$$
gi
<p>This value of the dot product gives us the projection of
<script type="math/tex"> | w \rangle </script> on
<script type="math/tex"> | v \rangle </script>.</p>

<p>We can write the dot product in the Dirac notation as <script type="math/tex">\langle v | w \rangle</script>.</p>

Here, the bra $$ \langle v | $$ is the dual vector of the ket $$ | v \rangle $$,
looking at their matrix representations:

$$
\begin{array}{c}
    | v \rangle \equiv \begin{bmatrix}
        v_1 \\
        \vdots \\
        v_n
    \end{bmatrix}

    \\

    \langle v | \equiv \begin{bmatrix} v_1 \\ \vdots \\ v_n \end{bmatrix} ^ \dagger
    = [v_1^*, \dots, v_n^*]
\end{array}
$$

So, the dot product can be thought of as a matrix-vector product, this will be
the inner product that we default to.

If the inner product of two vectors is 0, then the vectors are said to be
orthogonal. Orthogonal vectors are always linearly independent, so $$n$$
orthogonal vectors will form a basis for an $$n$$-dimensional vector space.

#### Norm
The norm of a vector is defined:

$$
\| | v \rangle \| = \sqrt{ \langle v | v \rangle }
$$

If the norm is 1, we call it a unit vector.

A set of vectors is called *orthonormal* if they are orthogonal unit vectors.

#### Gram-Schmidt procedure
Given a basis $$ \{ | w_1 \rangle , \dots , | w_n \rangle  \} $$ for some vector
space $$ V $$ with an inner product, we can use the Gram-Schmidt procedure to
produce an orthonormal basis $$ \{ | v_1 \rangle , \dots , | v_n \rangle  \} $$.

1. $$ | v_1 \rangle := \frac{ | w_1 \rangle  }{ \| | w_1 \rangle \| } $$
2. Define the remaining orthonormal basis vectors through an inductive process.
For $$ 1 \lt k \leq n $$:

$$
| v_k \rangle := \frac{ | w_{k} \rangle - \sum_{i=1}^{k-1} \langle v_i | w_k \rangle | v_i \rangle }
                { \| | w_{k} \rangle - \sum_{i=1}^{k-1} \langle v_i | w_k \rangle | v_i \rangle \| }
$$

#### Outer product and Dirac notation for matrices
From now on whenever we talk about the matrix representation of a linear
operator, we will assume that the matrix is written in respect to orthonormal
input and output bases.

The product of a ket and a bra is a linear operator, we can see this if we treat
bras as row vectors and kets as column vectors, their product will be a matrix.

Defined entirely in the Dirac notation:

$$
\begin{aligned}
    ( | w \rangle \langle v | ) | v^\prime \rangle  = & | w \rangle \langle v | v^\prime \rangle \\
                                                    = & (\langle v | v^\prime \rangle) | w \rangle 
\end{aligned}
$$

Linear combinations of outer products can be used to define more operators

$$
\begin{aligned}
    \left( \sum_i a_i | w_i \rangle \langle v_i | \right) | v^\prime \rangle    = & \sum_i a_i (\langle v_i | v^\prime \rangle) | w_i \rangle
\end{aligned}
$$

If the kets labeled $$ i $$ form an orthonormal basis of the vector space $$ V $$,
we can write any vector as a unique linear combination of these basis
kets $$ | v \rangle = \sum_i v_i | i \rangle  $$, where $$ v_i = \langle i | v \rangle $$.

<p>We can define the identity operator <script type="math/tex"> I </script> as <script type="math/tex"> \sum_i | i \rangle \langle i | </script></p>

$$
\begin{aligned}
    \left( \sum_i | i \rangle \langle i | \right) | v \rangle   = & \sum_i \langle i | v \rangle | i \rangle \\
                                                                = & \sum_i v_i | i \rangle \\
                                                                = & | v \rangle 
\end{aligned}
$$

From this, we can write down any operator, $$ A $$, from vector
space $$ V $$ to $$ W $$. If $$ | v_i \rangle $$ and $$ | w_j \rangle $$ form
orthonormal bases of $$ V $$ and $$ W $$ respectively:

$$
\begin{aligned}
    A   = & I_W A I_V \\
        = & \left( \sum_j | w_j \rangle \langle w_j | \right) A \left( \sum_i | v_i \rangle \langle v_i | \right) \\
        = & \sum_{i,j} | w_j \rangle \langle w_j | A | v_i \rangle \langle v_i | \\
        = & \sum_{i,j} (\langle w_j | A | v_i \rangle ) | w_j \rangle \langle v_i | 
\end{aligned}
$$

### 2.1.5 Eigenvectors and eigenvalues
<p><script type="math/tex">| v \rangle </script> is said to be an <i>eigenvector</i>
of a linear operator <script type="math/tex">A</script> if there is a complex
number <script type="math/tex">\lambda</script> such that 
$$ A | v \rangle = \lambda | v \rangle $$</p>

<p>This <script type="math/tex">\lambda</script> is called the <i>eigenvalue</i>
of <script type="math/tex">| v \rangle</script>.</p>

Every linear operator has at least one eigenvalue, and you can calculate them by
finding the roots of the characteristic equation

$$
\det |A - \lambda I| = 0
$$

The *eigenspace* corresponding to an eigenvalue $$ \lambda $$ is the set of all
eigenvectors associated with the eigenvalue. This is a subspace of the input
vector space.

$$
V_\lambda = \{ | v \rangle : A | v \rangle = \lambda | v \rangle  \}
$$

If an eigenspace is more than one-dimensional, it is called *degenerate*. For
example for the matrix

$$
A = \begin{bmatrix}
    2 & 0 & 0 \\
    0 & 0 & 0 \\
    0 & 0 & 2
\end{bmatrix}
$$

The vectors $$ (1,0,0) $$ and $$ (0,0,1) $$ are linearly independent and both
are associated with the eigenvalue 2. Thus, the eigenspace for eigenvalue 2 is
degenerate.

#### Diagonal representation
A diagonal representation for an operator $$ A $$ on a vector space $$ V $$ is
a representation of $$ A $$ of the form:

$$
A = \sum_i \lambda_i | i \rangle \langle i |
$$

Where <script type="math/tex"> | i \rangle </script> form an orthonormal set of
eigenvectors of $$ A $$ with corresponding eigenvalues $$ \lambda_i $$.

An operator is called *diagonalizable* if it has a diagonal representation.

##### Diagonal representations of the Pauli matrices:

$$
\begin{array}{c c}
    | 0 \rangle = \begin{bmatrix}
        1 \\ 0
    \end{bmatrix}, &
     | 1 \rangle = \begin{bmatrix}
        0 \\ 1
    \end{bmatrix} \\

| + \rangle = \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}}, &
| - \rangle = \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \\

| i  \rangle = \frac{ | 0 \rangle + i| 1 \rangle }{\sqrt{2}}, &
| -i \rangle = \frac{ | 0 \rangle - i| 1 \rangle }{\sqrt{2}} \\

\end{array}
$$

$$
\begin{array}{c c}
    I = \begin{bmatrix}
        1 & 0 \\
        0 & 1
    \end{bmatrix} = | 0 \rangle \langle 0 | + | 1 \rangle \langle 1 | 

    &

    X = \begin{bmatrix}
        0 & 1 \\
        1 & 0
    \end{bmatrix} = | + \rangle \langle + | - | - \rangle \langle - | \\

    Y = \begin{bmatrix}
        0 & -i \\
        i & 0
    \end{bmatrix} = | i \rangle \langle i | - | -i \rangle \langle -i |

    &

    Z = \begin{bmatrix}
        1 & 0 \\
        0 & -1
    \end{bmatrix} = | 0 \rangle \langle 0 | - | 1 \rangle \langle 1 | 
\end{array}
$$

### 2.1.6 Adjoints and Hermitian operators
For any linear operator $$ A $$ on the vector space $$ V $$, there exists a
unique linear operator $$ A^\dagger $$ such that for all $$ | v \rangle , | w \rangle \in V $$

$$
( | v \rangle , A | w \rangle ) = ( A^\dagger | v \rangle , | w \rangle )
$$

This linear operator is called the *adjoint* or *Hermitian conjugate* of $$ A $$.  
In the matrix representation, the adjoint acts as a conjugate transpose $$ A^\dagger = (A^*)^T $$,
which is how we define bras

$$
\langle v | = | v \rangle ^\dagger
$$

The adjoint of a composition of operators: $$ (AB)^\dagger = B^\dagger A^\dagger $$

#### Hermitian operators and projectors
A linear operator that is its own adjoint is called a *Hermitian* or *self-adjoint*
operator.

An important class of Hermitian operators are *projectors*. They project vectors
into a subspace of the vector space.

Let $$ V $$ be a $$d$$-dimensional vector space and $$ W $$ be a $$k$$-dimensional
subspace of $$ V $$. It is possible to find an orthonormal basis $$ \{ | i \rangle : 1 \leq i \leq d \} $$
of $$ V $$ such that $$ \{ | i \rangle : 1 \leq i \leq k \} $$ is an orthonormal
basis of $$ W $$, and then $$ \{ | i \rangle : k \lt i \leq d \} $$ forms an
orthonormal basis of $$ W^\mathsf{C} $$, the orthogonal complement of $$ W $$.  

$$ 
\forall | w \rangle \in W \\
\forall | q \rangle \in W^\mathsf{C} \\
\langle w | q \rangle = 0
$$

We can define the projector onto $$ W $$ as
<script type="math/tex"> P_W = \sum_{i=1}^{k} | i \rangle \langle i | </script>.
Which is independent of our choice of orthonormal basis.  
We can then, define the projector onto $$ W^\mathsf{C} $$ as $$ P_{W^\mathsf{C}} = I - P_W $$

If $$ P $$ is the projector onto any subspace, we can write the projector onto
its orthogonal complement as $$ Q $$.

#### Normal operators and the spectral decomposition
A linear operator $$ N $$ is called a *normal* operator if $$ N N^\dagger = N^\dagger N $$.

All Hermitian operators are normal, but only normal operators with real
eigenvalues are Hermitian.

The spectral theorem tells us that an operator is diagonalizable if and only if
it is a normal operator. The diagonal representation is also called the
*spectral decomposition*.

#### Unitary operators
A linear operator $$ U $$ is called a *unitary* operator if $$ UU^\dagger = I = U^\dagger U $$.

Unitary operators preserve inner products:

$$
\begin{aligned}
    ( | v \rangle , | w \rangle )       = & ( U | v \rangle , U | w \rangle ) \\
    
    \langle v | U^\dagger U | w \rangle = & \langle v | I | w \rangle \\
                                        = & \langle v | w \rangle 

\end{aligned}
$$

Unitary operators map orthonormal bases to orthonormal bases, ie
if $$ \{| i \rangle \} $$ form an orthonormal basis, so does $$ \{ U | i \rangle \} $$
because unitary operators preserve inner products.

If $$ \{ | v_i \rangle \} $$ and $$ \{ | w_i \rangle \} $$ are orthonormal
bases, then a unitary matrix that maps all $$ | v_i \rangle $$ to $$ | w_i \rangle $$
can be defined as:

$$
U = \sum_i | w_i \rangle \langle v_i | 
$$

By their definition, unitary operators are normal and so have a spectral
decomposition.

#### Positive operators
A Hermitian operator $$ A $$ is called a *positive* operator if, for every
vector $$ | v \rangle $$

$$
\langle v | A | v \rangle \geq 0
$$

If it is strictly greater than 0, then the operator is called *positive definite*.

Positive operators have a spectral decomposition $$ \sum_i \lambda_i | i \rangle \langle i | $$
with non-negative eigenvalues $$ \lambda_i $$.

### 2.1.7 Tensor products
The tensor product $$ \otimes $$ is a tool to fuse vector spaces into one larger
vector space. It is used to study the state of multiple quantum systems
(eg 2 qubits).

Let $$ V $$ be an $$m$$-dimensional vector space and $$ W $$ a $$n$$-dimensional
vector space. $$ V \otimes W $$ is an $$mn$$-dimensional vector space.

$$
V \otimes W = \text{span} \left( \{ | v \rangle \otimes | w : | v \rangle \in V \text{ and } | w \rangle \in W \} \right)
$$

Often, the $$\otimes$$ is omitted in favor of shorthands like
<script type="math/tex"> | v \rangle | w \rangle  </script>,
<script type="math/tex"> | v, w \rangle  </script> and
<script type="math/tex"> | vw \rangle  </script>.

If <script type="math/tex"> | i \rangle  </script> form an orthonormal basis
of $$ V $$ and <script type="math/tex"> | j \rangle  </script> form an
orthonormal basis of $$ W $$, then <script type="math/tex"> | i \rangle \otimes | j \rangle  </script>
forms a basis of $$ V \otimes W $$.

The tensor product is linear in both arguments

$$
z (| v \rangle  \otimes | w_1 \rangle)                                  = (z | v \rangle ) \otimes (z | w \rangle ) \\
(\nu_1 | v_1 \rangle + \nu_2 | v_2 \rangle) \otimes | w \rangle         = \nu_1 ( | v_1 \rangle \otimes | w \rangle ) + \nu_2 ( | v_2 \rangle \otimes | w \rangle ) \\
| v_1 \rangle \otimes (\omega_1 | w_1 \rangle + \omega_2 | w_2 \rangle) = \omega_1 ( | v \rangle \otimes | w_1 \rangle ) + \omega_2 ( | v \rangle \otimes | w_2 \rangle )
$$

If $$ A $$ and $$ B $$ are linear operators on $$ V $$ and $$ W $$
respectively, $$ A \otimes B $$ is a linear operator on $$ V \otimes W $$.

$$
( A \otimes B ) ( | v \rangle \otimes | w \rangle ) = ( A | v \rangle ) \otimes ( B | w \rangle ) \\
\forall | v \rangle \in V \text{ and } \forall | w \rangle \in W
$$

An inner product for $$ V \otimes W $$:

$$
\left( a | v \rangle \otimes | w \rangle , b | v^\prime \rangle \otimes | w^\prime \rangle  \right) = a^*b \langle v | v^\prime \rangle \langle w | w^\prime \rangle 
$$

We can see the way vectors and operators are fused with the tensor product if we
switch to the matrix representation.

$$A$$ is an $$ m \times n $$ matrix and $$ B $$
is a $$ p \times q $$ matrix. $$ A \otimes B $$ is a $$ mp \times nq $$ matrix.

$$
A \otimes B = \begin{bmatrix}
    A_{11} B & A_{12} B & \dots  & A_{1n} B \\
    A_{21} B & A_{22} B & \dots  & A_{2n} B \\
    \vdots   & \vdots   & \ddots & \vdots B \\
    A_{m1} B & A_{m2} B & \dots  & A_{mn} B
\end{bmatrix}
$$

Examples:

$$
\begin{aligned}
    \begin{bmatrix} 1 \\ 2 \end{bmatrix} \otimes \begin{bmatrix} a \\ b \end{bmatrix}   = & \begin{bmatrix}
                                                                                                1 \begin{bmatrix}
                                                                                                    a \\ b
                                                                                                \end{bmatrix}

                                                                                                \\
                                                                                                
                                                                                                2 \begin{bmatrix}
                                                                                                    a \\ b
                                                                                                \end{bmatrix}
                                                                                            \end{bmatrix} \\
                                                                                        
                                                                                        = & \begin{bmatrix}
                                                                                            a \\ 
                                                                                            b \\ 
                                                                                            2a \\ 
                                                                                            2b
                                                                                        \end{bmatrix} \\
\end{aligned}

\\

\begin{aligned}
    X \otimes Y = & \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix} \otimes \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix} \\
                
                = & \begin{bmatrix}
                    0 \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix} & 1 \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix} \\
                    1 \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix} & 0 \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}
                \end{bmatrix}

                \\
                
                = & \begin{bmatrix}
                    0 & 0  & 0 & -i \\
                    0 & 0  & i & 0  \\
                    0 & -i & 0 & 0  \\
                    i & 0  & 0 & 0
                \end{bmatrix}
\end{aligned}

$$

The notation $$ x^{\otimes k} $$ means that we tensor $$ x $$ with itself $$ k $$ times.

### 2.1.8 Operator functions
Given a function $$ f : \mathbb{C} \rightarrow \mathbb{C} $$, we can define a
function  $$ f $$ on normal operators $$ A $$.  
If $$ \sum_a \lambda_a | a \rangle \langle a | $$ is the spectral decomposition
of $$ A $$, then

$$
    f(A) = \sum_a f(\lambda_a) | a \rangle \langle a | 
$$

For example:

$$
\begin{aligned}
    e^Z =       & e^{ | 0 \rangle \langle 0 | - | 1 \rangle \langle 1 |  } \\
        =       & e^1 | 0 \rangle \langle 0 | + e^{-1} | 1 \rangle \langle 1 | \\
        \equiv  & \begin{bmatrix}
            e & 0 \\
            0 & e^{-1}
        \end{bmatrix}
\end{aligned}
$$

#### Trace
The *trace* of a matrix is defined as the sum of its diagonal elements. This is
independent of the choice of basis.

$$
\text{tr}(A) = \sum_i A_{ii}
$$

Since this is independent of the choice of basis, we can define the trace of an
operator in the Dirac notation as

$$
\text{tr}(A) = \sum_i \langle i | A | i \rangle 
$$

<p> where <script type="math/tex"> | i \rangle  </script> form an orthonormal basis.</p>

The trace is linear

$$ \text{tr}(aA + bB) = a \text{ tr}(A) + b \text{ tr}(B) $$  

and cyclic

$$ \text{tr}(ABC) = \text{tr}(CAB) = \text{tr}(BCA) $$

Because of this cyclic property, the trace of an operator does not change under
a unitary *similarity transformation*: $$ A \rightarrow U A U^\dagger $$

$$
\begin{aligned}
    \text{tr}(U A U^\dagger)    = & \text{tr}(U^\dagger U A) \\
                                = & \text{tr}(I A) \\
                                = & \text{tr}(A)
\end{aligned}
$$

If $$ | i \rangle $$ form an orthonormal basis, with $$ | \psi \rangle $$ being
one of these basis vectors:

$$
\begin{aligned}
    \text{tr}( A | \psi \rangle \langle \psi | )    = & \sum_i \langle i (| A | \psi \rangle \langle \psi) | i \rangle \\
                                                    = & \langle \psi | A | \psi \rangle \langle \psi | \psi \rangle
                                                        + \sum_{i \neq \psi} \langle i | A | \psi \rangle \langle \psi | i \rangle  \\
                                                    = & \langle \psi | A | \psi \rangle (1)
                                                        + \sum_{i \neq \psi} \langle i | A | \psi \rangle (0) \\
                                                    = & \langle \psi | A | \psi \rangle
\end{aligned}
$$

This can also be seen as a result of the cyclic nature of the trace:

$$
\begin{aligned}
    \text{tr}( A | \psi \rangle \langle \psi | )    = & \text{tr}( \langle \psi | A | \psi \rangle  ) \\
                                                    = & \langle \psi | A | \psi \rangle
\end{aligned}
$$

### 2.1.9 The commutator and anti-commutator
The *commutator* between two linear operators is defined

$$
[A,B] := AB - BA
$$

If its value is 0, then the operators commute ($$ AB = BA $$).

The *anti-commutator* is similarly defined

$$
\{A,B\} := AB + BA
$$

If its value is 0, then the operators anti-commute ($$ AB = -BA $$).

#### Simultaneous diagonalization theorem
If $$A$$ and $$B$$ are Hermitian operators, then $$[A,B] = 0 $$ if and only if
there exists an orthonormal basis such that both $$A$$ and $$B$$  are diagonal
with respect to that basis. We call $$A$$ and $$B$$ *simultaneously diagonalizable*
in this case.

ie. the linear operators $$ A $$ and $$ B $$ commute if and only if they have
the same eigenvectors.

<input style="display:none;" type="button" value="Show Proof" id="btn">

<div id="proof" style="display: none;">
<strong>Proof:</strong><br/>
<p><strong>I. </strong>Assume <script type="math/tex"> A </script> and <script type="math/tex"> B </script>
have diagonalizations in the same orthonormal basis.</p>

$$
\begin{aligned}
    A               = & \sum_i a_i | i \rangle \langle i | \\
    B               = & \sum_i b_i | i \rangle \langle i | \\
                      & \\
    \Rightarrow AB  = & \left(\sum_i a_i | i \rangle \langle i |\right) \left(\sum_j b_j | j \rangle \langle j |\right) \\
                    = & \sum_i a_i | i \rangle \langle i | \left( \sum_j b_j | j \rangle \langle j | \right) \\
                    = & \sum_i \sum_j a_i b_j | i \rangle \langle i | | j \rangle \langle j | \\
                    = & \sum_{i=j} a_i b_i | i \rangle \langle i | | i \rangle \langle i | + \sum_{i \neq j} a_i b_j | i \rangle \langle i | | j \rangle \langle j | \\
                    = & \sum_i a_i b_i | i \rangle \langle i | \\
                    & \\
    \text{and } BA  = & \left(\sum_i b_i | i \rangle \langle i |\right) \left(\sum_j a_j | j \rangle \langle j |\right) \\
                    = & \sum_i b_i | i \rangle \langle i | \left( \sum_j a_j | j \rangle \langle j | \right) \\
                    = & \sum_i \sum_j b_i a_j | i \rangle \langle i | | j \rangle \langle j | \\
                    = & \sum_{i=j} b_i a_i | i \rangle \langle i | | i \rangle \langle i | + \sum_{i \neq j} b_i a_j | i \rangle \langle i | | j \rangle \langle j | \\
                    = & \sum_i a_i b_i | i \rangle \langle i | \\
                    = & AB \\
    
    \Rightarrow       & [A,B] = 0
\end{aligned}
$$

<p><strong>II. </strong>Assume <script type="math/tex"> [A,B] = 0 </script> </p>

<p><script type="math/tex"> V_a </script> is <script type="math/tex"> A </script>'s
eigenspace corresponding to eigenvalue <script type="math/tex"> a </script>.
<script type="math/tex"> | a, j \rangle  </script> forms an orthonormal basis
for <script type="math/tex"> V_a </script>.

$$
\begin{aligned}
    A(B | a,j \rangle ) = & (AB) | a,j \rangle \\
                        = & BA | a,j \rangle \\
                        = & B (a | a,j \rangle ) \\
                        = & a (B | a,j \rangle) \\
    \Rightarrow           & B | a,j \rangle \in V_a \\
\end{aligned}
$$
</p>

<input type="button" value="Hide Proof" id="btn2" >

</div>

<script>
    document.getElementById("btn").addEventListener("click", function(){
        var proof = document.getElementById("proof");

        if (proof.style.display == "none") {
            proof.style.display = "block";
            document.getElementById("btn").value = "Hide Proof";
        } else {
            proof.style.display = "none";
            document.getElementById("btn").value = "Show Proof";
        }
    });

    document.getElementById("btn2").addEventListener("click", function(){
        var proof = document.getElementById("proof");

        if (proof.style.display == "none") {
            proof.style.display = "block";
            document.getElementById("btn").value = "Hide Proof";
        } else {
            proof.style.display = "none";
            document.getElementById("btn").value = "Show Proof";
        }
    });
</script>


### 2.1.10 The polar and singular value decompositions

#### Polar decomposition
Any linear operator $$ A $$ can be written as a composition of a unitary
operator $$ U $$ and a positive operator $$ J, K $$.

$$
A = UJ = KU \\
J = \sqrt{A^\dagger A} \\
K = \sqrt{A A^\dagger}
$$

If $$ A $$ is invertible, then $$ U $$ is unique.

<input type="button" id ="polar-btn" value="Show Proof">

<div style="display: none;" id= "polar-proof">
<strong>Proof: </strong>
<p> <script type="math/tex"> J </script> is a positive operator, so it has a
spectral decomposition <script type="math/tex"> J = \sum_i \lambda_i | i \rangle \langle i |  </script>
where <script type="math/tex"> \lambda_i \geq 0 </script>, for an orthonormal
eigenbasis <script type="math/tex"> | i \rangle  </script>.
</p>

$$
\begin{array}{c|c}
\begin{aligned}
    | \psi_i \rangle                               := & A | i \rangle \\
    \Rightarrow \langle \psi_i |  \psi_i \rangle    = & \langle i | A^\dagger A | i \rangle \\
                                                    = & \langle i | J^2 | i \rangle \\
                                                    = & \langle i | (\lambda_i^2 | i \rangle ) \\
                                                    = & \lambda_i^2 \langle i | i \rangle \\
                                                    = & \lambda_i^2
\end{aligned}

& 

\begin{aligned}
    | e_i \rangle                          := & \frac{| \psi_i \rangle}{\| | \psi_i \rangle  \|} \\
                                            = & \frac{| \psi_i \rangle}{\lambda_i} \\
    \Rightarrow \langle e_i | e_j \rangle   = & \frac{1}{\lambda_i \lambda_j} \langle \psi_i | \psi_j \rangle \\
                                            = & \frac{1}{\lambda_i \lambda_j} \langle i | A^\dagger A | j \rangle \\
                                            = & \frac{ \lambda_j^2 }{\lambda_i \lambda_j} \langle i | j \rangle \\
                                            = & \begin{cases}
                                                    \lambda_i , & \text{ if } i = j \\
                                                    0,          & \text{ otherwise }
                                                \end{cases}
\end{aligned}
\end{array}
$$

<p>Note that this does not immediately imply that
<script type="math/tex"> | e_i \rangle </script> forms an orthonormal basis
since there may be some <script type="math/tex"> i </script> such that
<script type="math/tex"> \lambda_i = 0 </script><br/>
We can use the Gram-Schmidt procedure to gt an orthonormal basis that contains
<script type="math/tex"> | e_i \rangle  </script> where
<script type="math/tex"> \lambda_i \neq 0 </script>. We shall now call this
basis <script type="math/tex"> | e_i \rangle  </script>.
</p>

$$
\begin{aligned}
    U                                      := & \sum_i | e_i \rangle \langle i | \\
    \Rightarrow UJ                          = & \left( \sum_j | e_j \rangle \langle j | \right) \left( \sum_i \lambda_i | i \rangle \langle i | \right) \\
                                            = & \sum_j \sum_i \lambda_i | e_j \rangle \langle j | | i \rangle \langle i | \\
                                            = & \sum_j \sum_i \lambda_i \langle j | i \rangle | e_j \rangle \langle i | \\
                                            = & \sum_{i=j} \lambda_i | e_i \rangle \langle i | + \sum_{i \neq j } 0 \\
                                            = & \sum_{i} \lambda_i | e_i \rangle \langle i | \\
    \Rightarrow UJ | i \rangle              = & (\sum_{j} \lambda_j | e_j \rangle \langle j |) | i \rangle \\
                                            = & \lambda_i | e_i \rangle \langle i | i \rangle \\
                                            = & \lambda_i | e_i \rangle \\
                                            = & | \psi_i \rangle \\
                                            = & A | i \rangle \\
\end{aligned}
$$

<p> Since both <script type="math/tex"> UJ </script> and <script type="math/tex"> A </script>
map the orthonormal basis <script type="math/tex"> | i \rangle  </script> to the
same vectors, they are equal.
</p>

<p>A similar proof can be done for <script type="math/tex"> A = KU </script></p>.

<br/>
<input type="button" id ="polar-btn2" value="Hide Proof">
</div>

<script>
document.getElementById("polar-btn").addEventListener("click", function(){
    var proof = document.getElementById("polar-proof");

    if (proof.style.display == "none") {
        proof.style.display = "block";
        document.getElementById("polar-btn").value = "Hide Proof";
    } 
    else {
        proof.style.display = "none";
        document.getElementById("polar-btn").value = "Show Proof";
    }
});

document.getElementById("polar-btn2").addEventListener("click", function(){
    var proof = document.getElementById("polar-proof");

    if (proof.style.display == "none") {
        proof.style.display = "block";
        document.getElementById("polar-btn").value = "Hide Proof";
    } 
    else {
        proof.style.display = "none";
        document.getElementById("polar-btn").value = "Show Proof";
    }
});
</script>

#### Singular value decomposition
A square matrix $$ A $$ can be written as the product

$$
A = UDV
$$

Where $$ U $$ and $$ V $$ are unitary matrices, and $$ D $$ is a diagonal matrix.

The diagonal elements of $$ D $$ are called the singular values of $$ A $$.

**Proof:**

The polar decomposition of $$ A $$: $$ A = SJ $$, where $$ S $$ is a unitary
matrix. $$ J $$ is a positive matrix so its spectral decomposition is $$ J = TDT^\dagger $$,
where $$ T $$ is a unitary matrix and $$ D $$ is a diagonal matrix with $$J$$'s
eigenvalues on the diagonal.

$$
\begin{aligned}
    A   = & SJ \\
        = & STDT^\dagger \\
        = & (ST) D (T^\dagger) \\
        = & U D V
\end{aligned}
$$


## 2.2 The postulates of quantum mechanics

### 2.2.1 State space
> **Postulate 1:** Associated to any isolated physical system is a complex
> vector space with inner product (that is, a Hilbert space) known as the
> *state space* of the system. The system is completely described by
> its *state vector*, which is a unit vector in the system's state space.

The simplest quantum system is the *qubit* (quantum bit), which is associated
with a  2-dimensional state space. $$ | 0 \rangle  $$ and $$ | 1 \rangle $$ form
an orthonormal basis in the state space, analogous to the two states 0 and 1
that a classical bit has.

So, any vector $$ | \psi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle $$,
where $$ \langle \psi | \psi \rangle = |\alpha|^2 + |\beta|^2 = 1 $$, is a valid
state that a qubit can be in.

**Terminology**

$$
| \psi \rangle = \sum_i \alpha_i | \psi_i \rangle
$$

<p>
<script type="math/tex"> | \psi \rangle  </script> is a linear combination, or
<i>superposition</i>, of the states <script type="math/tex"> | \psi_i \rangle  </script>.<br/>
<script type="math/tex"> \alpha_i </script> are the <i>amplitudes</i> for each
<script type="math/tex"> | \psi_i \rangle  </script>.
</p>

### 2.2.2 Evolution
> **Postulate 2:** The evolution of a *closed* quantum system is described by a
> *unitary transformation*. That is, the state $$ | \psi \rangle $$ of the
> system at the time $$ t_1 $$ is related to the state $$ | \psi^\prime \rangle $$
> of the system at time $$ t_2 $$ by a unitary operator $$ U $$ which depends
> only on the times $$ t_1 $$ and $$ t_2 $$,
> 
> $$ | \psi^\prime \rangle = U | \psi \rangle  $$

We've already seen the [Pauli matrices](#{{"213 The Pauli matrices" | slugify}})
in the previous section. They all can be used to represent unitary operators
that act on closed quantum systems. Another important gate is the *Hadamard*
gate, $$ H $$.

$$
H | 0 \rangle = \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \\
H | 1 \rangle = \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \\
H \equiv \frac{1}{\sqrt{2}} \begin{bmatrix}
    1 &  1 \\
    1 & -1 
\end{bmatrix}
$$

Note that this postulate only tells us how a closed quantum system evolves
between two fixed points in time. In order to see the continuos time evolution,
a more refined version of the postulate is needed:

> **Postulate 2$$^\prime$$:** The time evolution of a the state of a closed
> quantum system is described by the *Schrödinger equation*,
> 
> $$ i \hbar \frac{\mathrm{d} | \psi \rangle }{\mathrm{d}t} = H | \psi \rangle $$

Here $$ H $$ is not the Hadamard operator, it is a fixed Hermitian operator for
the system and is called the *Hamiltonian*. If we know the Hamiltonian of a
system, then we understand its dynamics completely.

The term $$ \hbar $$ is the reduced Planck's constant and the value is usually
absorbed into the Hamiltonian $$ \frac{\mathrm{d} | \psi \rangle }{\mathrm{d}t} = -i H^\prime | \psi \rangle $$,
where $$ H^\prime = H/\hbar $$.

#### Hamiltonian
As a Hermitian operator, a Hamiltonian has a spectral
decomposition:

$$ 
    H = \sum_E E | E \rangle \langle E |
$$

By convention we call the orthonormal $$ | E \rangle $$ *energy eigenstates*, or
*stationary states* and  $$ E $$ the energy of $$ | E \rangle $$.  
The energy eigenstate corresponding to the lowest energy is called the
*ground state*.

#### The solution of the Schrödinger's equation
One solution of the Schrödinger's equation is

$$
\begin{aligned}
    | \psi(t_2) \rangle = & \mathrm{exp}\left( \frac{-i H (t_2 - t_1)}{\hbar} \right) | \psi(t_1) \rangle \\
                        = & \sum_E \left( e^{\frac{-i}{\hbar} E (t_2 - t_1) } | E \rangle \langle E | \right) | \psi(t_1) \rangle \\
                        = & U(t_1,t_2) | \psi(t_1) \rangle 
\end{aligned}
$$

This is a unitary operator, and in fact any operator $$ \mathrm{exp}(iK) $$
where $$ K $$ is a Hermitian is a unitary operator.

#### How to "apply" quantum gates
So far, we have talked about closed quantum systems, yet in order to make a
quantum computer, we will need to interact with the qubits in it. Let's say the
qubits represent isolated atoms in the quantum computer, and a laser is used to
alter the state of the qubits. We can consider this computer to be our isolated
quantum system.

As an isolated quantum system, the computer has a Hamiltonian that describes its
evolution. If we look only at the effects on only the atoms, the behavior of the
atom's state vector can be approximated with another Hamiltonian,
*the atomic Hamiltonian*. The atomic Hamiltonian depends on properties of the
laser that we can control and change at will.

More generally, it is possible to write time-varying Hamiltonians for quantum
systems that depend on parameters under the experimentalists' control. These
systems are not closed but we can use Schrödinger's equation to approximate
their evolution.

### 2.2.3 Quantum measurement
The previous two postulates tell us that closed quantum systems can be
represented by state vectors and how these vectors evolve over time. They do not
tell us what the state vector of a system is at any time.  

If we try to figure out what the state vector of a system is, we will need to
choose a basis in the state space to *measure* the system's state vector in.  
However, quantum systems seem to somehow know when they are measured and their
state vectors immediately get projected onto exactly one of your
*measurement basis* vectors at the time of measurement.

> **Postulate 3:** Quantum measurements are described by a collection $$ \{M_m\} $$
> of *measurement operators*. These are operators acting on the state space of
> the system being measured. The index $$ m $$ refers to the measurement
> outcomes that may occur in the experiment. If the state of the quantum system
> is $$ | \psi \rangle $$ immediately before the measurement then the
> probability that result $$ m $$ occurs is given by
> 
> <script type="math/tex; mode=display"> p(m) = \langle \psi | M_m^\dagger M_m | \psi \rangle </script>
> 
> and the state of the system after the measurement is
> 
> $$ \frac{M_m | \psi \rangle }{\sqrt{\langle \psi | M_m^\dagger M_m | \psi \rangle}} $$
> 
> The measurement operators satisfy the *completeness equation*
> 
> $$ \sum_m M_m^\dagger M = I $$

The completeness equation expresses the fact that probabilities sum to one:

$$ 1 = \sum_m p(m) = \sum_m \langle \psi | M_m^\dagger M_m | \psi \rangle $$

#### Measurement in the computational basis
Given a qubit in the state $$ | \psi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle $$,
if it is measured in the computational basis, $$ | 0 \rangle, | 1 \rangle $$
and because they are orthonormal, the measurement operators
are $$ M_0 = | 0 \rangle \langle 0 | $$
and $$ M_1 = | 1 \rangle \langle 1 | $$.

These are projection operators onto computational basis states, they are
Hermitian, $$ M_m^\dagger = M_m $$,  and $$ M_m^2 = M_m $$.

$$
\begin{array}{c|c}
    \text{Measuring as 0} & \text{Measuring as 1} \\
    \hline
    \begin{aligned}
        p(0)    = & \langle \psi | M_0^\dagger M_0 | \psi \rangle \\
                = & \langle \psi | M_0^2 | \psi \rangle \\
                = & \langle \psi | M_0 | \psi \rangle \\
                = & ( \alpha^* \langle 0 | + \beta^* \langle 1 | ) (\alpha | 0 \rangle) \\
                = & |\alpha|^2 \langle 0 | 1 \rangle \\
                = & |\alpha|^2 \\

        | \psi^\prime \rangle   = & \frac{M_0 | \psi \rangle }{\sqrt{\langle \psi | M_0^\dagger M_0 | \psi \rangle}} \\
                                = & \frac{\alpha}{|\alpha|} | 0 \rangle \\
    \end{aligned}
    
    &

    \begin{aligned}
        p(1)    = & \langle \psi | M_1^\dagger M_1 | \psi \rangle \\
                = & \langle \psi | M_1^2 | \psi \rangle \\
                = & \langle \psi | M_1 | \psi \rangle \\
                = & ( \alpha^* \langle 0 | + \beta^* \langle 1 | ) (\beta | 1 \rangle) \\
                = & |\beta|^2 \langle 1 | 1 \rangle \\
                = & |\beta|^2 \\

        | \psi^\prime \rangle   = & \frac{M_1 | \psi \rangle }{\sqrt{\langle \psi | M_1^\dagger M_1 | \psi \rangle}} \\
                                = & \frac{\beta}{|\beta|} | 1 \rangle \\
    \end{aligned}

\end{array}
$$

In a later section, we will discuss how factors with a unit modulus can be
ignored when considering a quantum state, effectively making the
post-measurement states $$ | 0 \rangle  $$ and $$ | 1 \rangle $$ respectively.

### 2.2.4 Distinguishing quantum states
It is impossible to distinguish between two states that are not orthogonal. The
idea behind this can be explained through a game between Alice and Bob.

Alice prepares a system in the quantum state <script type="math/tex"> | \psi_i \rangle, 1 \leq i \leq n </script>
from a set of state vectors <script type="math/tex"> \{ | \psi_i \rangle \} _{i=1}^{n} </script>
that both Alice and Bob agreed on. Bob has to determine which state the system
is in.  

Note that if Bob measures the system, the state will change so he must determine
the state using exactly one measurement.

If the set of state vectors is orthonormal, Bob can measure the system similar
to how we measured in the computational basis in the last section.

<input type="button" id="ortho-btn" value="Show How">

<div style="display: none;" id="ortho-content">
<p> Define the measurement operators
<script type="math/tex; mode=display">
    M_i := \begin{cases}
        | \psi_i \rangle \langle \psi_i |                               & , 1 \leq i \leq n \\
        \sqrt{ I - \sum_{i = 1}^{n} | \psi_i \rangle \langle \psi_i |}   & , i = 0
    \end{cases}
</script>
We can see the probability of measuring the particular <script type="math/tex"> | \psi_i \rangle  </script> is 1.
<script type="math/tex; mode=display">
    \begin{aligned}
    p(i)    = & \langle \psi_i | M_i^\dagger M_i | \psi_i \rangle \\
            = & \langle \psi_i | \psi_i \rangle \\
            = & 1
    \end{aligned}
</script>

</p>

<br/>
<input type="button" id="ortho-btn2" value="Hide How">
</div>

<script>
document.getElementById("ortho-btn").addEventListener("click", function(){
    var proof = document.getElementById("ortho-content");
    
    if (proof.style.display == "none") {
        proof.style.display = "block";
        document.getElementById("ortho-btn").value = "Hide How";
    } 
    else {
        proof.style.display = "none";
        document.getElementById("ortho-btn").value = "Show How";
    }
});

document.getElementById("ortho-btn2").addEventListener("click", function(){
    var proof = document.getElementById("ortho-content");
    
    if (proof.style.display == "none") {
        proof.style.display = "block";
        document.getElementById("ortho-btn").value = "Hide How";
    } 
    else {
        proof.style.display = "none";
        document.getElementById("ortho-btn").value = "Show How";
    }
});
</script>

If however there are any two vectors
<script type="math/tex"> | \psi_1 \rangle, | \psi_2 \rangle  </script>
in the set that are not orthogonal, there is no reliable way to distinguish them.

<input type="button" id="nonortho-btn" value="Show Proof">

<div style="display: none;" id="nonortho-content">
<p>
<script type="math/tex; mode=display"> 
    | \psi_2 \rangle = \alpha | \psi_1 \rangle + \beta | \phi \rangle \\
    |\alpha|^2 + |\beta|^2 = 1 \\
    \alpha, \beta \neq 0
</script>
<script type="math/tex"> | \psi_2 \rangle  </script> can be written as a linear
combination of <script type="math/tex"> | \psi_1 \rangle  </script> and another
vector in the state space orthonormal to <script type="math/tex"> | \psi_1 \rangle  </script>.</p>
<p> Let there be some function
<script type="math/tex"> f : \{1, \dots, n\} \rightarrow \{1, \dots, n\} </script>
such that <script type="math/tex"> f(j) = i </script> means that Bob guesses the
state is <script type="math/tex"> | \psi_i \rangle  </script> when the initial
state was <script type="math/tex"> | \psi_j \rangle </script>.<br/>
<script type="math/tex; mode=display">
    E_i := \sum_{j:f(j)=i} M_j^\dagger M_j \\
    \langle \psi_1 | E_1 | \psi_1 \rangle = 1 \\
    \color{Red}{\langle \psi_2 | E_2 | \psi_2 \rangle = 1}
</script>
</p>
<p>
<script type="math/tex; mode=display">
    \begin{aligned}
        \sum_i E_i                                                                                                  = & I \\
        \Rightarrow \sum_i \langle \psi_1 | E_i | \psi_1 \rangle                                                    = & 1 \\
        \Rightarrow \langle \psi_1 | E_1 | \psi_1 \rangle + \sum_{i \neq 1} \langle \psi_1 | E_i | \psi_1 \rangle   = & 1 \\
        \Rightarrow 1 + \sum_{i \neq 1} \langle \psi_1 | E_i | \psi_1 \rangle                                       = & 1 \\
        \Rightarrow \sum_{i \neq 1} \langle \psi_1 | E_i | \psi_1 \rangle                                           = & 0 \\
        \Rightarrow \langle \psi_1 | E_2 | \psi_1 \rangle                                                           = & 0 \\
        \Rightarrow \sqrt{E_2} | \psi_1 \rangle                                                                     = & 0
    \end{aligned}
</script>
<script type="math/tex; mode=display">
\begin{aligned}
    \langle \psi_2 | E_2 | \psi_2 \rangle                 = & ( \alpha^* \langle \psi_1 | + \beta^* \langle \phi | ) E_2 ( \alpha | \psi_1 \rangle + \beta | \phi \rangle  ) \\
                                                          = & |\alpha|^2 \langle \psi_1 | E_2 | \psi_1 \rangle  + |\beta|^2 \langle \phi | E_2 | \phi \rangle \\
                                                            & + \alpha^* \beta \langle \psi_1 | E_2 | \phi \rangle + \alpha \beta^* \langle \phi | E_2 | \psi_1 \rangle \\
                                                          = & |\beta|^2 \langle \phi | E_2 | \phi \rangle \\
                                                       \leq & |\beta|^2 \\
                                                        \lt & 1 \\
    \color{Red}{\langle \psi_2 | E_2 | \psi_2 \rangle \lt}  & \color{Red}{1}
\end{aligned}
</script>
This is a contradiction, and so no such measurement operators can be reliable.
</p>

<br/>
<input type="button" id="nonortho-btn2" value="Hide Proof">
</div>

<script>
document.getElementById("nonortho-btn").addEventListener("click", function(){
    var proof = document.getElementById("nonortho-content");
    
    if (proof.style.display == "none") {
        proof.style.display = "block";
        document.getElementById("nonortho-btn").value = "Hide Proof";
    } 
    else {
        proof.style.display = "none";
        document.getElementById("nonortho-btn").value = "Show Proof";
    }
});

document.getElementById("nonortho-btn2").addEventListener("click", function(){
    var proof = document.getElementById("nonortho-content");
    
    if (proof.style.display == "none") {
        proof.style.display = "block";
        document.getElementById("nonortho-btn").value = "Hide Proof";
    } 
    else {
        proof.style.display = "none";
        document.getElementById("nonortho-btn").value = "Show Proof";
    }
});
</script>


### 2.2.5 Projective measurements
> **Projective measurements:** A projective measurement is described by an
> observable, $$M$$, a Hermitian operator on the state space of the system being
> observed. The observable has a spectral decomposition,
> 
> $$ M = \sum_m m P_m , $$
> 
> where $$P_m$$ is the projector onto the eigenspace of $$M$$ with eigenvalue $$m$$.
> The possible outcomes of the measurement correspond to the eigenvalues, $$m$$,
> of the observable. Upon measuring the state $$ | \psi \rangle $$, the
> probability of getting result $$m$$ is given by
> 
> $$ p(m) = \langle \psi | P_m | \psi \rangle . $$
> 
> Given that outcome $$m$$ occurred, the state of the quantum system immediately
> after the measurement is 
> 
> $$ \frac{ P_m | \psi \rangle }{ \sqrt{ p(m) } } . $$ 

This is a special case of postulate 3 where the measurement operators are also
orthogonal.

$$
\begin{aligned}
    \text{Completeness Relation: } & \sum_m M_m^\dagger M_m = I \\
    \text{Orthogonality: }         & M_m M_{m^\prime} = \delta_{m, m^\prime} M_m
\end{aligned}
$$

#### Expectation
The *expectation* of the observable $$M$$ is defined:

$$
\begin{aligned}
\mathbf{E}(M)   = & \sum_m m p(m) \\
                = & \sum_m m \langle \psi | P_m | \psi \rangle \\
                = & \langle \psi | \left( \sum_m m P_m \right) | \psi \rangle \\
                = & \langle \psi | M | \psi \rangle \\
\end{aligned}
$$

This is the average value we measure from $$M$$, if we were to repeat the
experiment multiple times. It is also written $$ \langle M \rangle $$.

#### Standard Deviation
The standard deviation of the measurements $$ \Delta(M) $$ can be calculated:

$$
\begin{aligned}
    \left[ \Delta(M) \right] ^2             = & \mathbf{E}[ ( M - \mathbf{E}[M] )^2 ] \\
                            = & \langle M^2 - \langle M \rangle^2 + 2 M \langle M \rangle \rangle \\
                            = & \langle M^2 \rangle - \langle M \rangle^2 \\
    \Rightarrow \Delta(M)   = & \sqrt{ \langle M^2 \rangle - \langle M \rangle^2 }

\end{aligned}
$$

#### Observables
An observable, $$M$$, can be defined by an orthonormal measurement basis, $$ | m \rangle $$.  
<script type="math/tex"> P_m </script> is the projector onto $$ | m \rangle $$

$$
P_m P_{m^\prime} = \delta_{m, m^\prime} P_m \\
\sum_m P_m = I \\
M = \sum_m m P_m
$$

We can also describe projective measurements with the help of the Pauli matrices.
An observable $$ \overrightarrow{v} \cdot \overrightarrow{\sigma} = v_1 \sigma_1 + v_2 \sigma_2 + v_3 \sigma_3 $$
can be defined for any three dimensional vector $$v$$. This observable is called
the *spin* along the $$ \overrightarrow{v} $$ axis.

### 2.2.6 POVM Measurements
With projective measurements, it was impossible distinguish between
non-orthogonal state vectors. Using *Positive Operator-Valued Measure*, or *POVM*
measurements, we are able to do this.

From [Postulate 3](#223-quantum-measurement), if we are using Measurement
operators $$ M_m $$ to measure a state $$ | \psi \rangle $$, the probability of
outcome $$m$$ occurring is $$ p(m) = \langle \psi | M_m^\dagger M_m | \psi \rangle $$.

$$
    E_m        := M_m^\dagger M_m \\
    \sum_m E_m  = I \\
    p(m)        = \langle \psi | E_m | \psi \rangle \\
$$

Thus, $$ E_m $$s is enough to determine the probabilities of the measurement
outcomes. They are also, as the name implies, positive operators. These
operators $$ E_m $$ are called *POVM elements* and the complete
set $$ \{ E_m \} $$ is called a POVM.

If we only know the POVM, we can define the measurement operators

$$
    M_m := \sqrt{E_m}
$$

If $$ M_m = E_m $$, then this is a projective measurement.

#### Distinguishing non-orthogonal states
Similar to before, Alice has prepared a qubit in one of the
states $$ | \psi_1 \rangle = | 0 \rangle  $$
or     $$ | \psi_1 \rangle = (| 0 \rangle + | 1 \rangle) / \sqrt{2} = | + \rangle  $$ and Bob
must figure out which state it was. Consider the POVM containing elements

$$
\begin{aligned}
    E_1         = & k | 1 \rangle \langle 1 | \\
    E_2         = & k | - \rangle \langle - | \\
    E_3         = & I - E_1 - E_2 \\
    \text{Where, }& k = 2-\sqrt{2} \\
                  & | - \rangle = \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}}
\end{aligned}
$$

<!-- E_3 = & \left(1 - \frac{k}{2} \right) | 0 \rangle \langle 0 | + \left( 1 - \frac{3k}{2} \right) | 1 \rangle \langle 1 | \\
          & + \frac{k}{2}\left( | 0 \rangle \langle 1 | + | 1 \rangle \langle 0 |  \right) \\ -->

Bob can successfully tell Alice which state she had prepared the qubit in
without making a mistake using this POVM. But, there is a chance that Bob will
not get any useful information from the measurement. Let us look at the
measurement probabilities to see why:

$$
\begin{array}{|c|c|}
    \hline
    \text{Alice chose } | \psi_1 \rangle & \text{Alice chose } | \psi_2 \rangle \\
    \hline

    \begin{aligned}
        p(1|\psi_1) = & \langle \psi_1 | E_1 | \psi_1 \rangle \\
                    = & k \langle 0 | 1 \rangle \langle 1 | 0 \rangle \\
                    = & 0
    \end{aligned}

    &

    \begin{aligned}
        p(1|\psi_2) = & \langle \psi_2 | E_1 | \psi_2 \rangle \\
                    = & k \langle + | 1 \rangle \langle 1 | + \rangle \\
                    = & \frac{k}{2} = 1 - \frac{1}{\sqrt{2}}
    \end{aligned} 

    \\

    \begin{aligned}
        p(2|\psi_1) = & \langle \psi_1 | E_2 | \psi_1 \rangle \\
                    = & k \langle 0 | - \rangle \langle - | 0 \rangle \\
                    = & \frac{k}{2} = 1 - \frac{1}{\sqrt{2}}
    \end{aligned}

    &

    \begin{aligned}
        p(2|\psi_2) = & \langle \psi_2 | E_2 | \psi_2 \rangle \\
                    = & k \langle + | - \rangle \langle - | + \rangle \\
                    = & 0
    \end{aligned}

    \\

    \begin{aligned}
        p(3|\psi_1) = & \langle \psi_1 | E_3 | \psi_1 \rangle \\
                    = & \langle 0 | I | 0 \rangle - \langle 0 | E_1 | 0 \rangle - \langle 0 | E_2 | 0 \rangle \\
                    = & 1 - 0 - \frac{k}{2} \\
                    = & \frac{1}{\sqrt{2}}
    \end{aligned}

    &

    \begin{aligned}
        p(3|\psi_2)  = & \langle \psi_2 | E_3 | \psi_2 \rangle \\
                = & \langle + | I | + \rangle - \langle + | E_1 | + \rangle - \langle + | E_2 | + \rangle \\
                = & 1 - \frac{k}{2} - 0\\
                = & \frac{1}{\sqrt{2}}
    \end{aligned} \\

    \hline

\end{array}
$$

From this distribution, we see that if Bob measures:
* Outcome 1: The initial state of the system was <script type="math/tex"> | \psi_2 \rangle </script>.
* Outcome 2: The initial state of the system was <script type="math/tex"> | \psi_1 \rangle </script>.
* Outcome 3: Bob can not determine the initial state of the system.

This measurement can distinguish between the non-orthogonal states, but it will
disturb the state of the system on doing so.

This type of measurement is generally used when the main item of interest is the
probability distribution of the measurement outcomes.

### 2.2.7 Phase
#### Global Phase
The states $$ | \psi \rangle  $$ and $$ e^{i \theta} | \psi \rangle $$ are
called equal up to a *global phase factor* of $$ e^{i \theta} $$. The
*global phase* is the angle $$ \theta $$.

These states have the exact same measurement statistics

$$
    p(m) = \langle \psi | M_m^\dagger M_m | \psi \rangle = \langle \psi | e^{-i \theta} M_m^\dagger M_m e^{i \theta} | \psi \rangle 
$$

Since their measurement probabilities are the same (ie, there is no observable
difference between the states), it is impossible for one to distinguish states
that differ by a global phase factor. Because of this, we can ignore global
phase factors.

#### Relative Phase
Consider a qubit in the state $$ | \psi \rangle = (e^{i \theta_0} | 0 \rangle + e^{i \theta_1} | 1 \rangle) / \sqrt{2}  $$.
The amplitudes of the state vector have the same magnitude, we can eliminate a
global phase factor of $$ e^{i \theta_0} $$ to get the state vector:

$$
\begin{aligned}
    | \psi \rangle  = & \frac{e^{i \theta_0}}{\sqrt{2}} \left( | 0 \rangle + e^{i (\theta_1 - \theta_0)} \right) \\
                    = & \frac{1}{\sqrt{2}} \left( | 0 \rangle + e^{i \phi } | 1 \rangle  \right) \\
\end{aligned}
$$

The amplitudes of this vector differ by a *relative phase* of $$ \phi $$.

Note that this phase difference is completely dependent on the choice of basis,
and is not an intrinsic property of the state vector itself.

State vectors that differ only by a relative phase in some basis can not be
regarded as equal because under the same state evolution (quantum circuit) there
may be observable differences.

### 2.2.8 Composite systems
Coming soon...

### 2.2.9 Quantum mechanics: a global view
Coming soon...

## 2.3 Application: superdense coding
Coming soon...

## 2.4 The density operator
Coming soon...

## 2.5 The Schmidt decomposition and purifications
Coming soon...

## 2.6 EPR and the Bell inequality
Coming soon...

