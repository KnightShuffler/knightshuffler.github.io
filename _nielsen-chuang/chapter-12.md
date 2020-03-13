---
title: "Chapter 12 – Quantum information theory"
---

Note: I've only added the proof of the no-cloning theorem at the moment.

## 12.1 Distinguishing quantum states and the accessible information

### 12.1.1 The Holevo bound
The rest of the content coming soon...

#### Proof of the no-cloning theorem
Let us assume there is a unitary operation, $$ U $$, that takes two qubit
inputs: the data qubit, in an arbitrary pure state $$ | \psi \rangle $$
and the target qubit which is some standard pure state $$ | s \rangle $$.  
The action of this operation copies the state of the data qubit into the target
qubit, leaving the data qubit unchanged.

$$
    | \psi \rangle \otimes | s \rangle \xrightarrow[]{U} U (| \psi \rangle \otimes | s \rangle) = | \psi \rangle \otimes | \psi \rangle
$$

Let there be two qubit states $$ | \psi \rangle $$ and $$ | \phi \rangle $$ that
we copy with this procedure:

$$
\begin{align}
    U (| \psi \rangle \otimes | s \rangle) & = | \psi \rangle \otimes | \psi \rangle \\
    U (| \phi \rangle \otimes | s \rangle) & = | \phi \rangle \otimes | \phi \rangle
\end{align}
$$

Taking the inner product of these two equations gives us:

$$
\begin{align}
        (\langle \psi | \otimes \langle s |) U^\dagger U (| \phi \rangle \otimes | s \rangle)  = & (\langle \psi | \otimes \langle \psi |)  (| \phi \rangle \otimes | \phi \rangle) \\
        \Rightarrow  (\langle \psi | \otimes \langle s |) (| \phi \rangle \otimes | s \rangle) = & (\langle \psi | \otimes \langle \psi |)  (| \phi \rangle \otimes | \phi \rangle) \\
        \Rightarrow \langle \psi | \phi \rangle \times \langle s | s \rangle                   = & \langle \psi | \phi \rangle \times \langle \psi | \phi \rangle \\
        \Rightarrow \langle \psi | \phi \rangle                                                = & (\langle \psi | \phi \rangle)^2 \\
\end{align}
$$

This equation has only two solutions for $$ \langle \psi | \phi \rangle $$, 0
and 1.  
If 1, then $$ | \psi \rangle = | \phi \rangle $$.  
If 0, then $$ | \psi \rangle $$ and $$ | \phi \rangle $$ are orthogonal.

So only orthogonal states can be copied by a unitary operation.

### 12.1.2 Example applications of the Holevo bound
Coming soon...

## 12.2 Data compression
Coming soon...

## 12.3 Classical information over noisy quantum channels
Coming soon...

## 12.5 Entanglement as a physical resource
Coming soon...

## 12.6 Quantum cryptography
Coming soon...