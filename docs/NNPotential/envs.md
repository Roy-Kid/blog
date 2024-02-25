# Representation of chemical environments

For a ground-state electronic structure calculation, an atomic structure is completely characterized by the number of electrons, the positions of the nuclei and their identities (nuclear charges), and in principle a machine learning model could use the same information as a representation of its input. 

However, the conflict is chemical space is infinity but the dataset or the ability to produce data is finited. We hope our model is generalized and it can reflect the real physics. Luckily, the structure is not random, and it has some intrinsic relations and constraints we can leverage. More specifically, a structure and its label we got from a quantum chemistry calculation can represent a set of chemical environments, i.e., a water molecule would fluctuate very quickly, but a series of conformations fitted to distribution. So the development of good representations or descriptor is to find a transferability but unique method to represent the chemical environment.

In this chapter, we will introduce some charicteristics of chemical environments and how to represent them.

## Symmetry

Using Cartesian coordinates to encode atom positions and molecule configuration is straightforward but is ineffecient. It depends on its absolute position, orientation in space, and the atom order, means that configurations that are completely equivalent can be represented by many different Cartesian values. For example, no matter how molecule translated or rotated or the atom order changed, the total energy should be the same, thus it can be represented by one descriptor or feature vectors.

Some properties do not change with respect to some transformation, such as the total energy of a molecule, this is called invariance. Others change with some operations, such as the dipole of molecule would change with rotation, this is called equivariance. By using those intrinsic relations, we can reduce a lot of freedom of the model. This important topic we will introduce in the next chapter.

Another symmetry is, if we got a molecule configuration $\{\mathbf{r}, \mathbf{a}\}$, it not only means the molecule can only be at one position, but can be expressed by a prossibility distribution, i.e., the most probable position is $\vec{r}$, but still have some probability around it. We can take leverage it by expressing it as an atom density $\sum_i g(\mathbf r - \mathbf r_i)$, which $g$ is a smooth, real, positive function(e.g. a normalized Gaussian), obtained by summing over localized functions centered on the positions.

## Smoothness

The overwhelming majority of atomic-scale properties are continuous, smooth functions of the atomic coordinates, and the underhood technique of ML is automatic differentiation. That means each component or transformation should be differentiable and smooth, and the derivative also should be smooth. Aformationed atom density is a good example of smooth process.

Why local chemical environment is so called local is because we introduce a artificial cutoff to limit the range of the interaction, which means the truncate is not smooth. We can introduce a cutoff function to smear it. Cutoff function should monotonously decreasing, for example we can use a cosine function:

$$
  
$$
