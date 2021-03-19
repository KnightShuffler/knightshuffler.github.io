---
layout: math-page
title: Complex Numbers
category: entangled-kittens
toc: true
read_time: false
---

Complex numbers are essential in the mathematical formulation of quantum mechanics. In this chapter,
I will quickly go over the basics of complex numbers and state some of their properties.

## Imaginary Numbers
The imaginary unit, $$i$$, is a number defined such that

$$ i^2 = -1 $$


**Some Properties of $$i$$:**

$$i^3 = (i^2)\cdot i = (-1)\cdot i = -i$$


$$i^4 = {(i^2)}^2 = (-1)^2 = 1 = i^0$$


$$i\cdot(-i) = 1 $$


$$\frac{1}{i} = -i$$


We call the product of a real number and $$i$$ an "imaginary number".

## Complex Numbers
The sum of a real number and an imaginary number is called a "complex number".

$$ z = a + ib,\; z\in\mathbb{C},\, a,b \in \mathbb{R}$$


$$a$$ is called the real part of $$z$$

$$\Re(z) = a$$
 
and $$b$$ is called the imaginary part of $$z$$

$$\Im(z) = b$$


### The Complex Plane
We can represent complex numbers as points on a two-dimensional plane called the complex plane. The 
horizontal axis is called the real axis and the vertical axis is called the imaginary axis.

The point on the plane with Cartesian coordinates $$(a,b)$$ represents the complex number $$z=a+ib$$.

<figure>
    <img src="/assets/entangled-kittens/complex-numbers/complex-plane.png" alt="The complex plane">
    <figcaption>Fig. 1.1  - The complex plane</figcaption>
</figure>

### Algebra of Complex Numbers
#### Addition
To add complex numbers, add their real and imaginary parts respectively to get the sum

$$ (a+ib) + (c+id) = (a+c) + i(b+d) $$

#### Multiplication
To multiply complex numbers, FOIL them

$$ (a+ib)(c+id) = (ac-bd) + i(ad + bc) $$

#### Absolute Value
The distance from the origin to the complex number $$z$$ in the complex plane is called the magnitude 
or the absolute value of $$z$$.

$$ |z| = \sqrt{a^2 + b^2} $$

#### Complex Conjugate
Mirroring $$z$$ about the real axis on the complex plane gives us its complex conjugate, $$z^*$$. This 
corresponds to flipping the sign of the imaginary part of $$z$$.

$$ z^* = a - ib $$


Multiplying $$z$$ with its complex conjugate gives us the square of the absolute value:

$$ zz^* = (a+ib)(a-ib) = a^2 - (ib)^2 = a^2 + b^2 = |z|^2 $$


As a rule of thumb, if asked to calculate the complex conjugate of an expression, just replace every
$$i$$ with $$(-i)$$.

## Polar Form of Complex Numbers
The polar coordinates $$(r,\phi)$$ the complex plane correspond to Cartesian coordinates
$$(r\cos\phi, r\sin\phi)$$, which correspond to the complex number 

$$ z = r(\cos\phi + i\sin\phi) $$


This is the polar form of a complex number. Comparing this to the Cartesian form,
$$z = a+ib$$, we have:

$$ r = |z| = \sqrt{a^2 + b^2} $$


$$ \phi = \tan^{-1}\left(\frac{b}{a}\right) $$

<figure >
    <img src="/assets/entangled-kittens/complex-numbers/polar-form.png" alt="Polar coordinates on the complex plane">
    <figcaption>Fig. 1.2  - Polar form of a complex number</figcaption>
</figure>

### Euler's Formula
Complex numbers with $$|z| = 1$$ can be written $$ z = \cos\phi + i\sin\phi $$.
Another way of writing these numbers is 

$$ e^{i\phi} = \cos\phi + i\sin\phi $$

This is Euler's formula. The details of why this is true involves writing the power series expansions 
of $$e^x, \sin x, $$ and $$\cos x$$, which I won't cover here.

In quantum computing literature, you'll see numbers of the form $$e^{i\phi}$$ referred to as "phases".
Sometimes you'll see the complex number itself referred to as the phase, other times the angle $$\phi$$ 
will be called the phase. In either case remember that the complex number $$e^{i\phi}$$ will be present
somewhere in that context.

### Multiplication
Multiplication in polar form is much simpler thanks to Euler's formula. Given two complex numbers 
$$z_1 = r_1 e^{i\phi_1}$$ and $$z_2 = r_2 e^{i\phi_2}$$,

$$ z_1 z_2 = (r_1r_2) e^{i(\phi_1 + \phi_2)} = (r_1r_2)[\cos(\phi_1+\phi_2) + i\sin(\phi_1+\phi_2)] $$
