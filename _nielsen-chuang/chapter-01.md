---
title: "Chapter 1 – Introduction and overview"
---

## 1.1 Global perspectives
Coming soon...

## 1.2 Quantum bits

### Qubit states
The bit is the fundamental concept of classical computation, the quantum
bit or *qubit* is its analog in quantum computation. A qubit is a mathematical
object that can be used to develop a general theory of quantum computation.

Like a bit can be in one of two states (0 or 1), qubits also have states. Two
possible states of a qubit are $$ |0\rangle $$ and $$ |1\rangle$$, which
correspond to the classical 0 and 1 states.

Apart from these, qubits can also be in a linear combination, or
*superposition*, of the states:

$$
| \psi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle 
$$

The numbers $$ \alpha $$ and $$ \beta $$ are complex numbers. Thus, the state of
a qubit is a vector in a two-dimensional complex vector space. The vectors $$ 
| 0 \rangle $$ and $$ | 1 \rangle $$ are called the *computational basis states*
and form an orthonormal basis for this vector space.

The state of a bit can be examined without altering it, but this is not the case
for qubits. A qubit in the state $$ | \psi \rangle = 
\alpha | 0 \rangle + \beta | 1 \rangle $$ can be measured as 0 with
probability $$ |\alpha|^2 $$ and measured as 1 with probability $$ |\beta|^2 $$.
Since the probabilities must sum to 1,

$$
|\alpha|^2 + |\beta|^2 = 1
$$

Therefore, qubit states are unit vectors in a two-dimensional complex vector
space.

> Qubit states can be manipulated and transformed in ways that lead to
> measurement outcomes which depend distinctly on the different properties of
> the state. Thus, these quantum states have have real, experimentally
> verifiable consequences, which are essential to the power of quantum
> computation and quantum information.

Superpositions imply that that a qubit's state can lie in a continuum between
the computational basis states. For example:

$$
| + \rangle = \frac{1}{\sqrt{2}} | 0 \rangle + \frac{1}{\sqrt{2}} | 1 \rangle 
$$

can be measured as 0 or 1 with probability $$ \left|\frac{1}{\sqrt{2}}\right|^2 
= \frac{1}{2} $$

### What qubits can model
Although qubits are purely mathematical objects, they can be used to represent
physical systems like:
* Two different polarizations of a photon
* The alignment of a nuclear spin in a uniform magnetic field
* Two energy states of an electron in an atom (the ground and excited states).

Expanding on the last example, by shining light with appropriate energy for an
appropriate amount of time, the electron can switch between the energy states.
We can model the energy state of the electron with a qubit, representing the
ground and excited states with the computational basis states. By reducing the
time we shine the light on the atom, an electron initially in the ground state
can be moved "half-way between the ground and excited state", modeled by a qubit
in the $$ | + \rangle $$ state.

### The Bloch Sphere

<figure class="align-right" style="width:35%">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/bloch_sphere.png" alt="The Bloch sphere">
<figcaption> The Bloch sphere </figcaption>
</figure>

The *Bloch Sphere* is a geometric representation of the state of a qubit, every 
possible state that a qubit can be in can be represented by a point on the
surface of a unit sphere.

$$
| \psi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle \\
\begin{array}{c|c}
    \begin{aligned}
        \alpha = r_0 e^{i\phi_0} \\
        \beta  = r_1 e^{i\phi_1} \\
    \end{aligned} &
    \begin{aligned}
        r_0, r_1 &\in [0, \infty) \\
        \phi_0, \phi_1 &\in [0, 2\pi] \\
    \end{aligned}
\end{array}
$$

$$
\begin{aligned}
                  &|\alpha|^2 + |\beta|^2                     & = 1 \\
    \Rightarrow   & |r_0 e^{i\phi_0}|^2 + |r_1 e^{i\phi_1}|^2 & = 1 \\
    \Rightarrow   & |r_0|^2 + |r_1|^2                         & =1 \\
    \Rightarrow   & r_0^2 + r_1^2                             & = 1 \\
    \exists\theta & \in [0, \pi] \text{ such that}            & r_0 = \cos\frac{\theta}{2} \\
                  &                                           & r_1 = \sin\frac{\theta}{2}
\end{aligned}
$$

$$
\begin{aligned}
    | \psi \rangle & = e^{i\phi_0} \cos\frac{\theta}{2} | 0 \rangle + 
                       e^{i\phi_1} \sin\frac{\theta}{2} | 1 \rangle \\

    & = e^{i\phi_0} \left( \cos\frac{\theta}{2} | 0 \rangle +
        e^{i(\phi_1 - \phi_0)} \sin\frac{\theta}{2} | 1 \rangle \right) \\

    & = e^{i\gamma} \left( \cos\frac{\theta}{2} | 0 \rangle +
        e^{i\varphi} \sin\frac{\theta}{2} | 1 \rangle \right)
\end{aligned}
$$

Note that the *global phase* term $$ e^{i\gamma} $$ has no observable effect on
the state, effectively letting us write the state as:

$$
| \psi \rangle = \cos\frac{\theta}{2} | 0 \rangle + 
                 e^{i\varphi} \sin\frac{\theta}{2} | 1 \rangle
$$

The parameters $$ \theta $$ and $$ \varphi $$ can be used as spherical
coordinates on a unit sphere, linking every point on the sphere to a state of
a qubit. You'll notice that orthogonal states are antipodal points on the Bloch
sphere.

The Bloch sphere is a good visual tool to help understand the qubit, but there
is no simple generalization of the Bloch sphere for systems with multiple
qubits.

### Information of a qubit
Despite there being infinitely many points on the Bloch sphere, implying
infinitely many qubit states, when measured, the qubit will yield only one bit
of information and then alter the state of the qubit. For example if we measure
the $$ | + \rangle $$ state as 0, the state will *collapse* to
the $$ | 0 \rangle $$ state.

> An even more interesting question would be how much information is represented
> by a qubit *if we do not measure it?* This is a trick question, because how
> can one quantify information if it cannot be measured?

We use qubits to model physical systems that exist in the universe, which means
that the universe is somehow able to keep track of the state of these systems
between measurements. So, there is "hidden information" which grows
exponentially with the number of qubits in the system. This hidden information
is called quantum information.

### 1.2.1 Multiple qubits
Two bits have four possible states: 00, 01, 10 and 11. A two qubit system has
the computational basis states $$ | 00 \rangle, | 01 \rangle, | 10 \rangle,
| 11 \rangle $$. Thus, the state of this system involve associating a complex
coefficient, *amplitude*, to each of these basis states:

$$
| \psi \rangle = \alpha_{00} | 00 \rangle + \alpha_{01} | 01 \rangle + 
                 \alpha_{10} | 10 \rangle + \alpha_{11} | 11 \rangle
$$

When the system is measured, we will get the state x (= 00, 01, 10 or 11) with
probability $$ |\alpha_x|^2 $$, leaving the system in the state $$ | x \rangle $$.

Since the probabilities must sum to 1, the normalization condition is

$$
\sum_{x \in \{0, 1\}^2} |\alpha_x|^2 = 1
$$

The system consists of two qubits, so we can choose to measure only one of them,
say the first one. The probability of measuring just the first qubit as 0 can
be calculated as $$ |\alpha_{00}|^2 + |\alpha_{01}|^2 $$, which would leave the
system in the *post-measurement* state:

$$
| \psi^{\prime} \rangle = \frac{ \alpha_{00} | 00 \rangle + \alpha_{01} | 01 \rangle }
                            {\sqrt{|\alpha_{00}|^2 + |\alpha_{01}|^2}}
$$

The term in the denominator is present to re-normalize the state.

#### The Bell State
An important two-qubit state is the Bell state, or EPR pair (named after
Einstein, Podolsky and Rosen):

$$
\frac{ | 00 \rangle + | 11 \rangle }{\sqrt{2}}
$$

> It is the key ingredient in quantum teleportation and super dense coding.

If we measure only one of the qubits in this system, we will get 0 or 1 with a
probability of $$ 1/2 $$. The post-measurement state of the system will then be
either $$ | 00 \rangle $$ or $$ | 11 \rangle $$ depending on the measurement.
Measuring one qubit of the system automatically measures the second qubit to
have the same outcome.

#### *n* qubits
The state of a system of *n* qubits can be modeled with the computational basis
states $$ | x_1 x_2 \dots x_n \rangle  $$. This means $$ 2^n $$ amplitudes are
required to define the state of this system.

If n was 500, it would require more amplitudes than the estimated number of
atoms in the universe. Somehow the universe is able to keep track of and
manipulate these many variables, and it is this potential computational power
that we aim to make use of in quantum computing.

## 1.3 Quantum computation

### 1.3.1 Single qubit gates
Classical computer circuits consist of wires that carry information (bits) and
logic gates that manipulate this information.  
The only non-trivial single bit logic gate in classical computing is the NOT
gate, which is defined by its truth table

$$
\begin{array}{c|c}
    \text{Input} & \text{Output} \\
    \hline
    0 & 1 \\
    1 & 0 \\
\end{array}
$$

Likewise, we can define a quantum NOT gate that will take $$ | 0 \rangle $$
to $$ | 1 \rangle $$ and vice versa. But this information alone does not tell us
how the gate will act on a superposition of the states.

As a property of quantum mechanics, all quantum gates are *linear*, so the
NOT gate will act on superpositions like so:

$$
\alpha | 0 \rangle + \beta | 1 \rangle \xrightarrow[ ]{X}
\alpha | 1 \rangle + \beta | 0 \rangle
$$

The notation $$X$$ is used for the NOT gate.

Since quantum gates are linear transformations, we can write them down as
matrices.

$$
X \equiv \begin{bmatrix}
    0 & 1 \\
    1 & 0
\end{bmatrix}
$$

This allows us to use standard matrix-vector notation to represent the action
of gates on quantum states

$$
X \begin{bmatrix}
    \alpha \\
    \beta
\end{bmatrix} = 
\begin{bmatrix}
    \beta \\
    \alpha
\end{bmatrix}
$$

Quantum gates can be represented using 2x2 complex matrices, but they need to
maintain the normalization condition. This can be achieved using *unitary*
matrices.

$$
U \text{ such that } UU^\dagger = I = U^\dagger U
$$

Here $$ U^\dagger $$ is the adjoint (conjugate transpose) of the matrix $$ U $$.

Thus, there are infinitely many single qubit quantum gates.  
Since all quantum gates can be represented using unitary matrices, we can
define all of them by their action on the computational basis states. Here are
some examples:

$$
\begin{array}{c}
    \begin{array}{c}
        \text{Pauli Z Gate} \\

        {\begin{array}{cc}
            { Z \equiv \begin{bmatrix}
                1 &  0 \\
                0 & -1
            \end{bmatrix} }
            &
            { \begin{array}{c}
                Z | 0 \rangle =  | 0 \rangle \\
                Z | 1 \rangle = -| 1 \rangle 
            \end{array} }
        \end{array}}
    \end{array} \\
    
    { } \\

    \begin{array}{c}
        \text{Hadamard Gate} \\

        {\begin{array}{cc}
            { H \equiv \frac{1}{\sqrt{2}} \begin{bmatrix}
                1 &  1 \\
                1 & -1
            \end{bmatrix} }
            &
            { \begin{array}{c}
                H | 0 \rangle = \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \\
                H | 1 \rangle = \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} 
            \end{array} }
        \end{array}}
    \end{array}

\end{array}
$$

Any 2x2 unitary matrix can be decomposed as

$$
U = e^{i \alpha}

\begin{bmatrix}
    e^{-i \frac{\beta}{2}} & 0 \\
    0                      & e^{i \frac{\beta}{2}}
\end{bmatrix}

\begin{bmatrix}
    \cos \frac{\gamma}{2} & -\sin \frac{\gamma}{2} \\
    \sin \frac{\gamma}{2} &  \cos \frac{\gamma}{2}
\end{bmatrix}

\begin{bmatrix}
    e^{-i \frac{\delta}{2}} & 0 \\
    0                      & e^{i \frac{\delta}{2}}
\end{bmatrix}
$$

Where $$ \alpha, \beta, \gamma, \delta $$ are all real numbers. The first term
is a global phase shift and the matrices are rotations.

We can generate any qubit state from an appropriate single qubit quantum gate,
and using this decomposition, we can make an arbitrarily good approximation of
any quantum gate with a fixed set of values for $$ \alpha, \beta, \gamma, \delta $$.

That is to say, we can build any single qubit quantum gate with a finite set of
single qubit quantum gates.  
More generally, an arbitrary quantum computation on any number of qubits can be
generated with a finite set of quantum gates. This set is called a *universal
set* of gates.

### 1.3.2 Multiple qubit gates
The prototypical example of a multi-qubit gate is the CNOT (Controlled NOT)
gate.

<figure style="width:35%" class="align-right">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/cnot.png">
<figcaption>The representation of the CNOT gate in a quantum circuit</figcaption>
</figure>

It takes two inputs: the Control qubit ($$ \bullet $$) and the Target qubit
($$ \oplus $$). For some computational basis state $$ | a, b \rangle $$ if the
first (left) qubit is the control and the second qubit is the target, the CNOT
gate transforms the state like so:

$$
\begin{array}{c|c}
    \begin{align}
        | a, b \rangle & \xrightarrow[]{\operatorname{CNOT}}  | a, b \oplus a \rangle \\
        | 00 \rangle & \xrightarrow[]{\operatorname{CNOT}}  | 00 \rangle \\
        | 01 \rangle & \xrightarrow[]{\operatorname{CNOT}}  | 01 \rangle \\
        | 10 \rangle & \xrightarrow[]{\operatorname{CNOT}}  | 11 \rangle \\
        | 11 \rangle & \xrightarrow[]{\operatorname{CNOT}}  | 10 \rangle \\
    \end{align}
    
    &
    U_{CN} = 
    \begin{bmatrix}
        1 & 0 & 0 & 0 \\
        0 & 1 & 0 & 0 \\
        0 & 0 & 0 & 1 \\
        0 & 0 & 1 & 0 \\
    \end{bmatrix}
\end{array}
$$

The CNOT gate is a sort of generalization of the classical XOR gate, but there
is no direct quantum equivalent of the 2 bit logic gates AND, OR, NAND etc.  
Since all gates are unitary operations, they must be invertible or reversible.
The classical logic gates take 2 bit inputs and map them to a 1 bit output which
makes it impossible to exactly determine the input given the output, ie they are
not reversible.

> Understanding how to do classical logic in this reversible or invertible sense
> will be a critical step in understanding how to harness the power of quantum
> mechanics for computation.

There are more multi-qubit gates, but they can all be composed using CNOT gates
and single qubit gates.

### 1.3.3 Measurements in bases other than the computational basis
The states $$ | 0 \rangle $$ and $$ | 1 \rangle $$ are only one possible choice
of orthonormal bases of the qubit state space. Another orthonormal basis is the
*diagonal* or *Hadamard* basis:

$$ 
    \begin{align}
        | + \rangle & = \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \\
        | - \rangle & = \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}}
    \end{align}
$$

Through a change of basis, we can rewrite a superposition of one basis set as a
superposition of another basis set.

$$
    \begin{align}
        | \psi \rangle & =  \alpha | 0 \rangle + \beta | 1 \rangle \\
        | \psi \rangle & =  \alpha \left( \frac{ | + \rangle + | - \rangle }{\sqrt{2}} \right) +
                            \beta  \left( \frac{ | + \rangle - | - \rangle }{\sqrt{2}} \right) \\
        | \psi \rangle & =  \left( \frac{\alpha + \beta}{\sqrt{2}} \right) | + \rangle +
                            \left( \frac{\alpha - \beta}{\sqrt{2}} \right) | - \rangle
    \end{align}
$$

Written like this, it is possible to treat the Hadamard basis like the
computational basis, letting us measure:  
'+' with a probability of $$ \left| \frac{\alpha + \beta}{\sqrt{2}} \right|^2 $$  
'-' with a probability of $$ \left| \frac{\alpha - \beta}{\sqrt{2}} \right|^2 $$

In general, for an orthonormal basis $$ \{ | a \rangle , | b \rangle \} $$, the
superposition $$ | \psi \rangle = \alpha | a \rangle + \beta | b \rangle  $$
can be measured as:  
'a' with probability $$ |\alpha|^2 $$  
'b' with probability $$ |\beta|^2 $$

### 1.3.4 Quantum circuits
Quantum circuits, akin to logic diagrams, are visual representations of quantum
processes: computation, communication and even quantum noise.

The lines carry information in the form of qubits. Reading the circuit from left
to right, we can follow the passage of time in the circuit.

By convention, the default state of a qubit is $$ | 0 \rangle $$ if not
otherwise mentioned.

#### Qubit swapping circuit
The following circuit of three CNOT gates can be used to swap the state of two
qubits in the system.

<figure style="width:80%" class="align-center">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/swap_circuit.png" style="width:40%">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/swap_gate.png"    style="width:40%">
<figcaption>Qubit swap circuit and an equivalent schematic symbol notation for this common circuit</figcaption>
</figure>

$$
\begin{align}
    | a, b \rangle  & \rightarrow | a, b \oplus a \rangle \\
                    & \rightarrow | a \oplus b \oplus a, b \oplus a \rangle = | b, b \oplus a \rangle \\
                    & \rightarrow | b, b \oplus a \oplus b \rangle = | b, a \rangle 
\end{align}
$$

#### Restrictions of quantum circuits
Due to the nature of quantum mechanics, these features of logic circuits don't
occur in quantum circuits.

<dl>
    <dt> FANIN </dt>
        <dd>When two or more wires join at a point, OR-ing their bits at the
        join.<br>
        This isn't allowed in quantum circuits since such a process would
        not be reversible.</dd>
    <dt> FANOUT </dt>
        <dd>When two or more wires emerge from the same point, the previous
        copying the bit to each wire.<br>
        This isn't allowed in quantum circuits because quantum states cannot
        be copied.</dd>
    <dt> Feedback loops </dt>
        <dd>When the output of a gate is connected to its input. Not present in
        quantum circuits because they require a FANIN.</dd>
</dl>

#### Notation
Lines are used to represent qubits, lines with a slash through them represent
multiple qubits.

Gates are represented by a box with the Gate's name in them.

<img class="align-center" style="width:40%" src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/U_gate.png">

For any gate U, we can make a controlled-U gate, like the CNOT gate.

<img class="align-center" style="width:40%" src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/controlled_U_gate.png">

Measurements are represented with a meter, they convert qubits into
probabilistic bits. The double line is used to represent classical information.

<img class="align-center" style="width:40%" src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/meter.png">

### 1.3.5 Qubit copying circuit?
Logic circuits allow copying bits and we can do this for qubits in the
computational basis states using a CNOT gate, but we can't copy states in
superposition.

<figure style="width:40%" class="align-right">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/CNOT_copy.png">
<figcaption>Using the CNOT gate to copy a qubit x in a computational basis state.</figcaption>
</figure>

If we tried to use the CNOT to copy a superposition, we'll get the following
state:

$$
\begin{align}
    | \psi \rangle                     & = [a| 0 \rangle + b| 1 \rangle] | 0 \rangle   \\
                                       & = a | 00 \rangle + b | 10 \rangle \\
    \operatorname{CNOT} | \psi \rangle & = a | 00 \rangle + b | 11 \rangle 
\end{align}
$$

But, this state isn't what we would get on copying the state.

$$
\begin{align}
    | \psi \rangle | \psi \rangle & = [a| 0 \rangle + b| 1 \rangle][a| 0 \rangle + b| 1 \rangle] \\
                                  & = a^2 | 00 \rangle + ab | 01 \rangle + ab | 10 \rangle + b^2 | 11 \rangle 
\end{align}
$$

So, the CNOT gate only acts as a qubit copier if

$$
    \begin{array}{c|c}
        \begin{aligned}
            a^2 = a \\
            a \in {0,1}
        \end{aligned} &
        \begin{aligned}
            b^2 = b \\
            b \in {0,1}
        \end{aligned}
    \end{array}
$$

With the only valid solutions being $$a=1, b=0$$ or $$a=0, b=1$$

There is no possible way to copy a qubit in superposition. This is the
*no-cloning theorem*. (Proof in [Chapter 12](../chapter-12/#proof-of-the-no-cloning-theorem))

### 1.3.6 Example: Bell states
This circuit takes the computational basis states of a two-qubit system and maps
them to the Bell states, an orthonormal basis of entangled states.

<figure style="width:35%" class="align-right">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/bell-state.png">
<figcaption>A quantum circuit to create entanglement.</figcaption>
</figure>

$$
\begin{array}{c|c|c}
    | x, y \rangle & H                                            & \operatorname{CNOT} \\
    \hline
    | 00 \rangle   & \frac{| 00 \rangle + | 10 \rangle}{\sqrt{2}} & | \beta_{00} \rangle = \frac{| 00 \rangle + | 11 \rangle}{\sqrt{2}}  \\
    | 01 \rangle   & \frac{| 01 \rangle + | 11 \rangle}{\sqrt{2}} & | \beta_{01} \rangle = \frac{| 01 \rangle + | 10 \rangle}{\sqrt{2}} \\
    | 10 \rangle   & \frac{| 00 \rangle - | 10 \rangle}{\sqrt{2}} & | \beta_{10} \rangle = \frac{| 00 \rangle - | 11 \rangle}{\sqrt{2}} \\  
    | 11 \rangle   & \frac{| 01 \rangle - | 11 \rangle}{\sqrt{2}} & | \beta_{11} \rangle = \frac{| 01 \rangle - | 10 \rangle}{\sqrt{2}} 
\end{array}
$$

$$
\beta_{xy} = \frac{ | 0, y \rangle + (-1)^x | 1, \bar{y} \rangle  }{\sqrt{2}}
$$

### 1.3.7 Example: quantum teleportation
As mentioned earlier, qubit states can't be copied, but with the help of a Bell
state, the state of a single qubit can be moved around even without a quantum
channel. This is called *quantum teleportation*.

Alice wants to send Bob her qubit that is in the *target state*, $$ | \psi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle $$,
but they don't have a quantum communication channel set up between them. Suppose
Alice and Bob each share one qubit of the Bell state $$ | \beta_{00} \rangle $$.  
Under these conditions, Alice can change Bob's entangled qubit's state to the
target state through the following circuit.

<figure class="align-center" style="width:75%">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/teleportation.png">
    <figcaption>The quantum teleportation circuit. The top line represents the
    qubit Alice wants to send Bob. The middle line represents Alice's qubit of
    the entangled pair and the bottom line, Bob's.</figcaption>
</figure>

Here's how the state of the system changes, going through each gate in the
circuit. From left to right, the qubits in the state represent the qubits from
top to bottom in the circuit.

$$
\begin{align}
    | \psi \rangle | \beta_{00} \rangle         = & [| \psi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle] \left( \frac{ | 00 \rangle + | 11 \rangle }{\sqrt{2}} \right) \\
                                                = & \frac{1}{\sqrt{2}} \left[\alpha | 0 \rangle (| 00 \rangle + | 11 \rangle)  + \beta | 1 \rangle ( | 00 \rangle + | 11 \rangle)\right] \\
    \xrightarrow[]{\operatorname{CNOT} \otimes I} & \frac{1}{\sqrt{2}} \left[\alpha | 0 \rangle (| 00 \rangle + | 11 \rangle)  + \beta | 1 \rangle ( | 10 \rangle + | 01 \rangle) \right] \\
    \xrightarrow[]{H \otimes I \otimes I}         & \frac{1}{\sqrt{2}} \left[\alpha \left( \frac{| 0 \rangle + | 1 \rangle }{\sqrt{2}} \right)  (| 00 \rangle + | 11 \rangle)
                                                                           + \beta  \left( \frac{| 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) ( | 10 \rangle + | 01 \rangle) \right] \\
                                                = & \frac{1}{2} [ | 00 \rangle ( \alpha | 0 \rangle + \beta | 1 \rangle ) +
                                                                  | 01 \rangle ( \alpha | 1 \rangle + \beta | 0 \rangle ) \\
                                                  &             + | 10 \rangle ( \alpha | 0 \rangle - \beta | 1 \rangle ) +
                                                                  | 11 \rangle ( \alpha | 1 \rangle - \beta | 0 \rangle )] \\
                                                
\end{align}
$$

If Alice measure's her qubits, it will force Bob's qubit's state to one of the
four terms in the brackets, $$ | \phi \rangle $$, and will have two bits: M<sub>1</sub>,
from the top qubit and M<sub>2</sub>, from the middle qubit.  
She will send these bits to Bob through some classical communication channel so
Bob can apply quantum gates to bring his qubit into the target state.

$$
\begin{array}{|c|c|c|}
    \hline
    \operatorname{M_1 M_2} & | \phi \rangle                         & \text{Correction Gates (in order)} \\
    \hline
    00                     & \alpha | 0 \rangle + \beta | 1 \rangle & - \\
    01                     & \alpha | 1 \rangle + \beta | 0 \rangle & X \\
    10                     & \alpha | 0 \rangle - \beta | 1 \rangle & Z \\
    10                     & \alpha | 1 \rangle - \beta | 0 \rangle & X, Z \\
    \hline
\end{array}
$$

## 1.4 Quantum algorithms

### 1.4.1 Classical computations on a quantum computer
The last section brought up how classical logic gates don't have direct quantum
gate equivalents because of their inherent irreversibility. It is however,
possible to emulate classical logic circuits using the *Toffoli gate*.

<figure class="align-center" style="width:50%">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/toffoli.png">
<figcaption>The Toffoli gate is a controlled CNOT gate.</figcaption>
</figure>

$$
\begin{array}{c|c}
    \begin{array}{c|c}
        \text{Inputs} & \text{Outputs} \\
        \hline
        \begin{array}{ccc}
            a & b & c \\
            \hline
            0 & 0 & 0 \\
            0 & 0 & 1 \\
            0 & 1 & 0 \\
            0 & 1 & 1 \\
            1 & 0 & 0 \\
            1 & 0 & 1 \\
            1 & 1 & 0 \\
            1 & 1 & 1 \\
        \end{array}
        
        &
        
        \begin{array}{ccc}
            a^\prime & b^\prime & c^\prime \\
            \hline
            0 & 0 & 0 \\
            0 & 0 & 1 \\
            0 & 1 & 0 \\
            0 & 1 & 1 \\
            1 & 0 & 0 \\
            1 & 0 & 1 \\
            1 & 1 & 1 \\
            1 & 1 & 0 \\
        \end{array}
    \end{array}

    &

    \begin{bmatrix}
        1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
        0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
        0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\
    \end{bmatrix}

\end{array}
$$

<figure style="width:50%" class="align-right">
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/toffoli-nand.png"> <br>
<img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/toffoli-fanout.png">
<figcaption>Qubit swap circuit and an equivalent schematic symbol notation for this common circuit</figcaption>
</figure>

NAND is a universal logic gate and together with FANOUT can fully capture
deterministic logic in quantum circuits.

Non-deterministic logic allows random bits to be used in the computation. This
can be achieved in quantum circuits by passing one of the computational basis
states through a Hadamard gate and then measuring it.

### 1.4.2 Quantum parallelism

> Quantum parallelism is a fundamental feature of many quantum algorithms.

Quantum parallelism is essentially the ability to simultaneously evaluate the
output of a function for multiple inputs.

Suppose we have a function $$ f : \{0,1\} \rightarrow \{0,1\} $$

We can define a two-qubit quantum gate $$ U_f $$ such that

$$
    U_f | x, y \rangle = | x, y \oplus f(x) \rangle 
$$

If we pass the qubit states $$ \left( \frac{| 0 \rangle + | 1 \rangle }{\sqrt{2}} \right) | 0 \rangle $$
to this gate, we get the following state:

$$
    \frac{ | 0, f(0) \rangle + | 1, f(1) \rangle }{\sqrt{2}}
$$

This state has information about all of the function's inputs and outputs, but
it isn't immediately useful because when we measure the state, it will collapse
into a state that only has information about one of the function's
outputs: $$ | 0, f(0) \rangle $$ or $$ | 1, f(1) \rangle $$.  
In order to take advantage of quantum parallelism, we need to extract *global information*
of the function from the superposition.

The next two sections discuss two examples of how to do this.

### 1.4.3 Deutsch's algorithm
Consider a function $$ f : \{0,1\} \rightarrow \{0,1\} $$.

There are four possible functions that f could be:
* $$ f_0(x) = 0       : f_0(0) = 0, f_0(1) = 0 $$
* $$ f_1(x) = x       : f_1(0) = 0, f_1(1) = 1 $$
* $$ f_2(x) = \bar{x} : f_2(0) = 1, f_2(1) = 0 $$
* $$ f_3(x) = 1       : f_3(0) = 1, f_3(1) = 1 $$

The functions $$ f_0 $$ and $$ f_3 $$ are *constant* functions because the
output is the same, regardless of the input.  
The functions $$ f_1 $$ and $$ f_2 $$ are *balanced* functions because the
number of inputs that give output 0 is equal to the number of inputs that give
output 1.

Under the classical computing framework, the only way to tell if the function is
balanced or constant is by evaluating the function for both inputs.

Deutsch's algorithm is a quantum algorithm that can figure this out by only
evaluating the function once, on a superposition.

<figure class="align-center" style="width:80%">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/deutsch.png">
    <figcaption>The circuit representation of Deutsch's algorithm</figcaption>
</figure>

Here's how the state of the system evolves as it goes through this circuit

$$
\begin{align}
    | 0 \rangle | 1 \rangle \xrightarrow[]{H \otimes H} & \left( \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \right) \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) \\
                                                        = & \frac{ | 00 \rangle      - | 01 \rangle                 + | 10 \rangle      - | 11 \rangle }{2} \\
                                      \xrightarrow[]{U_f} & \frac{ | 0, f(0) \rangle - | 0, \overline{f(0)} \rangle + | 1, f(1) \rangle - | 1, \overline{f(1)} \rangle  }{2} \\
                                                        = & \begin{cases}
                                                                \frac{1}{2} [ (| 0 \rangle + | 1 \rangle) | f(0) \rangle - ( | 0 \rangle + | 1 \rangle ) | \overline{f(0)} \rangle  ], & \text{if } f(0) = f(1) \\
                                                                \frac{1}{2} [ (| 0 \rangle - | 1 \rangle) | f(0) \rangle - ( | 0 \rangle - | 1 \rangle ) | \overline{f(0)} \rangle  ], & \text{if } f(0) \neq f(1)
                                                            \end{cases} \\
                                                        = & \begin{cases}
                                                                \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \frac{ | f(0) \rangle - | \overline{f(0)} \rangle }{\sqrt{2}}, & \text{if } f(0) = f(1) \\
                                                                \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \frac{ | f(0) \rangle - | \overline{f(0)} \rangle }{\sqrt{2}}, & \text{if } f(0) = f(1) \\
                                                            \end{cases} \\
                                        
\end{align}
$$

We know that $$ f(0) \in \{0,1\} $$ so

$$
\begin{align}
    f(0) = f(1)    & \equiv f(0) \oplus f(1) = 0 \\
    f(0) \neq f(1) & \equiv f(0) \oplus f(1) = 1 \\
\end{align}
$$

The value $$ f(0) \oplus f(1) $$ is a global property of the function f since it
requires information about more than one input of the function. It tells us if
the function is constant (0) or balanced (1). Here's what the state looks like
for each function $$ f $$ can be.

$$
\begin{align}
    | \psi \rangle =              & \begin{cases}
                                        \left( \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \right) \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) & \text{if } f = f_0 \\
                                        \left( \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \right) \left( \frac{ | 1 \rangle - | 0 \rangle }{\sqrt{2}} \right) & \text{if } f = f_3 \\

                                        \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) & \text{if } f = f_1 \\
                                        \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) \left( \frac{ | 1 \rangle - | 0 \rangle }{\sqrt{2}} \right) & \text{if } f = f_2 \\
                                    \end{cases} \\
    \xrightarrow[]{H \otimes I} &   \begin{cases}
                                        | 0 \rangle  \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) & \text{if } f = f_0 \\
                                        | 0 \rangle  \left( \frac{ | 1 \rangle - | 0 \rangle }{\sqrt{2}} \right) & \text{if } f = f_3 \\

                                        | 1 \rangle \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) & \text{if } f = f_1 \\
                                        | 1 \rangle \left( \frac{ | 1 \rangle - | 0 \rangle }{\sqrt{2}} \right) & \text{if } f = f_2 \\
                                    \end{cases} \\
                                = & (-1)^{f(0)} | f(0) \oplus f(1) \rangle | - \rangle
\end{align}
$$

Now, when we measure the first qubit, it will tell us whether $$ f $$ is
constant or balanced.

### 1.4.4 The Deutsch-Jozsa algorithm
The Deutsch-Jozsa algorithm is a generalization of Deutsch's algorithm for
functions $$ f : \{0,1\}^n \rightarrow \{0,1\} $$ that we know to be either
constant or balanced.

A classical computer would need to evaluate the function for at
most $$ \frac{2^n}{2} + 1 $$ inputs to see which type of function it is.

 Just like before, a quantum computer can do this in one evaluation of $$ f $$.

#### Hadamard transform
Similar to the previous case, if we have a function $$ f : \{0,1\}^n \rightarrow \{0,1\} $$,
we can define an (n+1)-qubit quantum gate, $$ U_f $$, the first n qubits for the
input of $$ f $$, and the last qubit for the output, such that

$$
    U_f | x \rangle | y \rangle = | x \rangle | y \oplus f(x) \rangle
$$

If we want to generate a state that has complete information of the function
like we did before, we need to pass every input qubit in the $$ | + \rangle $$
state and the output qubit in the $$ | 0 \rangle $$ state.

If they start in the $$ | 0 \rangle $$ state, we can prepare the input qubits by
passing them all through a Hadamard gate. Passing n-qubits through Hadamard
gates is the Hadamard transform, represented by the gate $$ H^{\otimes n} $$.

$$
    H^{\otimes n} | 0 \rangle^{\otimes n} = \frac{1}{\sqrt{2^n}} \sum_{x \in \{0,1\}^n} | x \rangle 
$$

Let's see the general action of the Hadamard transform on a computational basis
state $$ | x \rangle $$ and use the state $$ | 110 \rangle  $$ as an example.

$$
    x \in \{0,1\}^n \\
    x = x_1 x_2 ... x_n \\
    \forall x, z \in \{0,1\}^n \\
    x \cdot z = (x_1 \cdot z_1) \oplus (x_2 \cdot z_2) \oplus ... \oplus (x_n \cdot z_n) \\
$$

$$
    H^{\otimes n} | x \rangle = \frac{1}{\sqrt{2^n}} \sum_{z \in \{0,1\}^n} (-1)^{z \cdot x} | z \rangle 
$$

$$
\begin{align}
    H^{\otimes 3} | 110 \rangle = & H | 1 \rangle \otimes H | 1 \rangle \otimes H | 0 \rangle \\
                                = & \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) \otimes \left( \frac{ | 0 \rangle - | 1 \rangle }{\sqrt{2}} \right) \otimes \left( \frac{ | 0 \rangle + | 1 \rangle }{\sqrt{2}} \right) \\
                                = & \frac{1}{\sqrt{2^3}}\begin{bmatrix}
                                                              | 000 \rangle + | 001 \rangle - | 010 \rangle - | 011 \rangle \\
                                                            - | 100 \rangle - | 101 \rangle + | 110 \rangle + | 111 \rangle
                                                        \end{bmatrix}
\end{align}
$$

#### The algorithm
<figure class="align-center" style="width:80%">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/nielsen-chuang/chapter-01/deutsch-jozsa.png">
    <figcaption>The circuit representation of the Deutsch-Jozsa algorithm</figcaption>
</figure>

$$
\begin{align}
    | 0 \rangle ^{\otimes n} \otimes | 1 \rangle \xrightarrow[]{H^{\otimes (n+1)}}  & H^{\otimes n} | 0 \rangle ^{\otimes (n+1)} \otimes H | 1 \rangle \\
                                                                                =   & \frac{1}{\sqrt{2^n}} \sum_{x} (| x \rangle) \otimes \frac{| 0 \rangle - | 1 \rangle}{\sqrt{2}} \\
                                                                                =   & \frac{1}{\sqrt{2^n}} \sum_{x} \left(| x \rangle \otimes \frac{| 0 \rangle - | 1 \rangle}{\sqrt{2}}\right) \\
                                                                \xrightarrow[]{U_f} & \frac{1}{\sqrt{2^n}} \sum_{x} \left( | x \rangle \otimes \frac{ | f(x) \rangle - | \overline{f(x)} \rangle  }{\sqrt{2}}  \right) \\
                                                                                =   & \frac{1}{\sqrt{2^n}} \sum_{x} (-1)^{f(x)} \left( | x \rangle \otimes \frac{ | 0 \rangle - | 1 \rangle  }{\sqrt{2}}  \right) \\
                                            \xrightarrow[]{H^{\otimes n} \otimes I} & \frac{1}{\sqrt{2^n}} \sum_{x} \left( (-1)^{f(x)} H^{\otimes n} | x \rangle \otimes \left( \frac{ | 0 \rangle - | 1 \rangle  }{\sqrt{2}} \right) \right) \\
                                                                                =   & \frac{1}{\sqrt{2^n}} \sum_{x} \left( (-1)^{f(x)} \left( \frac{1}{\sqrt{2^n}} \sum_z (-1)^{z \cdot x} | z \rangle \right) \otimes \left( \frac{ | 0 \rangle - | 1 \rangle  }{\sqrt{2}} \right) \right) \\
                                                                                =   & \frac{1}{2^n} \sum_{z} \sum_{x} (-1)^{f(x) + z \cdot x} | z \rangle \otimes \left( \frac{ | 0 \rangle - | 1 \rangle  }{\sqrt{2}} \right) \\

\end{align}
$$

When we measure the first n qubits, we get the bit string $$ z $$ with
probability $$ \left| \frac{1}{2^n} \sum_{x} (-1)^{f(x) + z \cdot x} \right|^2 $$.
The probability of measuring the bit string of all 0s can be calculated as

$$
\begin{align}
    P(z=00...0) = & \left| \frac{1}{2^n} \sum_{x} (-1)^{f(x) + 0 \cdot x} \right|^2 \\
                = & \left| \frac{1}{2^n} \sum_{x} (-1)^{f(x)} \right|^2 \\
\end{align}
$$

If $$ n_0 $$ is the number of times $$ f $$ outputs 0 and $$ n_1 $$ is the
number of times it outputs 1

$$
\begin{align}
    P(z=00...0) = & \left| \frac{1}{2^n} (n_0 - n_1) \right|^2 \\
                = & \begin{cases}
                        \left| \frac{\pm 2^n}{2^n} \right|^2,                            & \text{if } f \text{ is constant, ie } & n_0 = 2^n \text{ or } n_1 = 2^n \\
                        \left| \frac{1}{2^n} \left( 2^{n-1} - 2^{n - 1} \right) \right|^2, & \text{if } f \text{ is balanced, ie } & n_0 = n_1 = \frac{2^n}{2}
                    \end{cases} \\
                = & \begin{cases}
                        \left| \pm 1 \right|^2,  & \text{if } f \text{ is constant} \\ 
                        \left| 0 \right|^2    ,  & \text{if } f \text{ is balanced}
                \end{cases} \\
    P(z=00...0) = & \begin{cases}
                        1, & \text{if } f \text{ is constant} \\ 
                        0, & \text{if } f \text{ is balanced}
                \end{cases}
\end{align}
$$

### 1.4.5 Quantum algorithms summarized
Coming soon...

## 1.5 Experimental quantum information processing
Coming soon...

## 1.6 Quantum information
Coming soon...
