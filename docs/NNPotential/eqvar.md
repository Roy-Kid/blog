# Invariances and Equivariances

 For example, no matter where a molecule is and how they are oriented, the total energy should same. This is called translational and rotational invariance. Also, the output of model should not change with the sequence of your input, that calls permutation invariance. Invariance means a property not changed with respect to some transformation. Some properties do change with other transformations, let's say, the dipole of molecule would change with rotation. This is called equivariance. By using *informal* mathematics, we can define invariance and equivariance as follows:

$$
    f(g(x)) = f(x) \quad \text{invariance} \\
    f(g(x)) = g(f(x)) \quad \text{equivariance}
$$
where $f$ is our model or property calculator, and $g$ is a operation.

Invariance and equivariance plays a crucial role in the design of neural network potentials, it would reduce the freedom of the model and make the model more general. Here is a list of invariances and equivariances we should consider when designing a neural network potential:

| transformation | equivariance |
| --- | --- |
| Matrix Determinant |Permutation Invariance|
| Eigendecomposition | Permutation Invariance|
| Reduction (sum, mean) | Permutation Invariance|
| Pairwise Vector/Distance | Translation/Rotation Invariance|
| Angles | Translation/Rotation Invariance|
| Atom-centered Symmetry Functions | Rotation/Translation Invariance|
| Trajectory Alignment | Rotation/Translation Invariance|
| Molecular Descriptors | All invariant|
| convolution | Translation Invariance|

## Kick start with group theory

Before we dive into equivairant network, we need some math tools. The first one is group theory. Group theory is a branch of mathematics that studies the algebraic structures known as groups. A group is a general object in mathematics. A group is a set of elements that can be combined in a binary operation whose output is another member of the group. The element can be anything, such as integer, english letter etc. Here we’re interested in groups of transformations that move points in a space. Operations like rotation, scaling, mirroring, or translating of single points. As you read about groups here, remember that the elements of the groups are not numbers or points. The group elements are transformations that act on points in the space. Notice I’m being a bit nebulous on what the space is for now. Let’s first define a group with elements ${a, b, c...}$:

* Closure: The output of the binary operation is always a member of the group;
* Associativity: $a\dot b \dot c = c \dot (b\dot c)$
* Identity: There is an element $e$ such that $a\dot e = e\dot a = a$
* Inverse: For every element $a$ in the group, there is an element $a^{-1}$ such that $a\dot a^{-1} = a^{-1}\dot a = e$

Another important property is **commutativity**, which means $a\dot b \ne b\dot a$. If a group is commutative, it is called an abelian group. The number of element in a group is called **order**, written as $|G|$. [TODO: element dot and group action]

## How to use group theory in equivariant network

Our dataset usually comes up with pairs, let's say $(x, y)$, where $x$ is something likes coordinates and elements, and $y$ is the property we already know. For our model, we want to train it as a blackbox which input is $x$ and predict some other property, which means $f:x\to y$. Notice $x$ and $y$ neither same in its dimension nor number or property. We usually call the $f$ is an operator. 

An element $g$ of group $G$ can act on the input or an operator $f:x\to y$. If $f$ is an invariant operator, we have:

$$
    f: gx \to y
$$

and if $f$ is an equivariant operator:

$$
    f: gx \to gy
$$