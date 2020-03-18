---
flavor: "A basic introduction to complex numbers, which are used to describe quantum states."
---
## Introduction
Complex numbers originally arose when attempting to find solutions to cubic
equations. That being said, it's a lot easier to introduce them in the context
of the quadratic equation:

$$
x^2 + 1 = 0
$$

If we attempt to solve this using the quadratic formula:

$$
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a} \\
$$ {: text-center}
For the equation: $$ax^2+bx+c=0$$

We get the following:

$$
x = \frac{-0 \pm \sqrt{0^2 -4(1)(1)}}{2(1)} \\
x = \pm \frac{\sqrt{4(-1)}}{2} \\
x = \pm \frac{2\sqrt{-1}}{2} \\
x = \pm \sqrt{-1}
$$

If we restrict ourselves accept solutions that exist only the set of real
numbers $$\mathbb{R}$$, then this equation doesn't have any solutions, because
there is no real number that is the square root of -1.  
However, if we allow ourselves to define a new number system where we define a
number $$ i := \sqrt{-1} $$, that historically has been called an *imaginary*
number, we can now define a solution to the quadratic equation.

From the imaginary number $$ i $$, and the set of real numbers, we can define a
new set of numbers.

$$ 
\mathbb{C} := \{ a+ib | a, b \in \mathbb{R} \}
$$

This set is the set of complex numbers.

## Notation
For a complex number $$ z = a + ib $$:
* $$ a $$ is the *real part* of $$ z $$, denoted by $$ \Re(z) $$ or
  $$ \operatorname{Re}(z) $$
* $$ b $$ is the *imaginary part* of $$ z $$, denoted by $$ \Im(z) $$ or
  $$ \operatorname{Im}(z) $$

A real number $$ a $$ can be written as the complex number $$ a + i0 $$, ie. it
doesn't have an imaginary part, we can drop the "$$ +0i $$" as it is understood.

A purely imaginary number $$ ib $$ can be written as the complex number $$ 0 + 
ib $$, ie. it doesn't have a real part, we can drop the "$$ 0 + $$" as it
also, is understood. 

## Algebra of Complex Numbers
### Addition
Given two complex numbers, $$ z_1 = a_1 + ib_1 $$ and $$ z_2 = a_2 + ib_2$$, we
can add them by adding their real and imaginary parts respectively.

$$
z_1 + z_2 = (a_1 + a_2) + i(b_1 + b_2)
$$

And in general if we have $$ n $$ complex numbers $$ z_1, z_2, ..., z_n $$, we
can add them like so:

$$
\sum_{j=1}^{n} z_j = \sum_{j=1}^{n} \Re(z_j) + i \sum_{j=1}^{n} \Im(z_j)
$$

### Multiplication
From the definition of a complex number, we've used the product of a real
number $$ b $$ with the imaginary number $$ i $$ as a purely imaginary number $$
bi $$.  
Using this, we can multiply a complex number $$ z $$ by a real number $$ c $$ by
multiplying the real and imaginary parts of $$ z $$ by $$ c $$.

$$
c \cdot z = r \cdot \Re(z) + i(r\cdot\Im(z))
$$

We've also defined $$ i = \sqrt{-1} $$, so $$ i \cdot i = -1 $$.
We can calculate the powers of $$ i $$:

$$
i^1 = i \\
i^2 = -1 \\
i^3 = -i \\
i^4 = 1 \\
i^k = i^{k \mod 4}
$$

So, we can find the product of two complex numbers $$ z_1 = a_1 + ib_1 $$ and $$
z_2 = a_2 + ib_2 $$ like so:

$$
z_1 \cdot z_2 = (a_1 + ib_1)(a_2 +ib_2) \\
= a_1 \cdot a_2 + a_1 \cdot ib_2 + ib_1 \cdot a_2 + ib_1 \cdot ib_2 \\
= a_1a_2 + i(a_1b_2) + i(b_1a_2) + (-1)(b_1b_2) \\
= (a_1a_2 - b_1b_2) + i(a_1b_2 + a_2b_1)
$$

Not exactly as elegant as addition but we can make this easier for ourselves
by looking at a different form of writing down complex numbers.
## Forms of Complex Numbers
### Cartesian Form
The way we've looked a complex numbers thus far has been in the *Cartesian* or
*Rectangular* form.

Every complex number can be identified with a unique ordered pair $$(\Re(z), 
\Im(z))$$ which we can use as coordinates in a 2 dimensional space.

The *Complex Plane* is one such space, it's a Euclidean space with the same
coordinates. The horizontal axis represents the real part of the complex numbers
and the vertical axis their imaginary parts.

![Cartesian Form of a complex number, image from Wikipedia]({{site.url}}{{site.baseurl}}/assets/backgrounds/complex-numbers/cartesian-form.png)

### Polar Form
On a Euclidean plane, we can also represent a point with polar coordinates $$ (r,
\varphi) $$ that are the distance of the point from the origin and the 
counter-clockwise angle the positive horizontal axis maxes with the ray joining
the origin to the point.

To represent our complex number $$ z = a + ib $$ using our polar coordinates of
the point we can see that:
$$ a = r \cos \varphi $$
$$ b = r \sin \varphi $$
Therefore,

$$
z = r \cos \varphi + i r \sin \varphi \\
= r (\cos \varphi + i \sin \varphi)
$$

![Polar Form of a complex number]({{site.url}}{{site.baseurl}}/assets/backgrounds/complex-numbers/polar-form.png)

Using the Pythagoras theorem, we can calculate $$ r = \sqrt{a^2+b^2} $$,
we call this the *modulus* of the complex number, written as $$ |z| $$.

The angle $$ \varphi $$ is called the *argument* or *phase* of the complex
number, usually taken in the interval $$(-\pi, \pi]$$. It is written
as $$ \arg(z) $$

### Euler Form 
Expressing the sin and cos functions in their Taylor series expansions, and
put them into the expression for the polar form of a complex number gives us
Euler's formula:

$$
\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + ... \\
\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + ... \\
e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + ... \\
\\
\cos \varphi + i\sin \varphi  = 1 + i\varphi - \frac{\varphi^2}{2!} - i\frac{\varphi^3}{3!} + ... \\
= 1 + i\varphi + \frac{(i\varphi)^2}{2!} + \frac{(i\varphi)^3}{3!} + ... \\
\Rightarrow e^{i\varphi} = \cos \varphi + i \sin \varphi
$$

The Euler form of a complex number is
$$ z = |z|e^{i \arg(z)} $$

This form makes multiplication exponentiation a lot easier to perform:

$$
z_1 \cdot z_2 = |z_1|e^{i \varphi_1} \cdot |z_2|e^{i \varphi_2} \\
= |z_1||z_2|e^{i (\varphi_1 + \varphi_2)}
$$

$$
z^k = {(|z|e^{i\varphi})}^k \\
= |z|^k e^{ik\varphi}
$$

## Complex Conjugate

!["Complex Conjugate, image taken from Wikipedia"]({{site.url}}{{site.baseurl}}/assets/backgrounds/complex-numbers/complex-conjugate.png){: .align-right}
The complex conjugate of a complex number $$ z $$ (written as $$ \overline{z} $$ 
or $$ z^* $$), is a mirror image of $$ z $$ on the complex plane about the real
axis.

$$
\overline{z} = \Re(z) -i\Im(z) = |z|e^{-i\arg(z)}
$$

### Properties
For any complex numbers $$ z, z_1, z_2 $$:

$$
\overline{z_1 + z_2} = \overline{z_1} + \overline{z_2}
$$

$$
\overline{z_1 \cdot z_2} = \overline{z_1} \cdot \overline{z_2}
$$

$$
z \cdot \overline{z} = |z|^2
$$