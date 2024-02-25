# Tensors and Shape

Tensors are the generalization of vectors (rank 1) and matrices (rank 2) to arbitrary rank. Rank can be defined as the number of indices required to get individual elements of a tensor. A matrix requires two indices (row, column), and is thus a rank 2 tensor. We may say in normal conversation that a matrix is a “two-dimensional object” because it has rows and columns, but this is ambiguous because the row could be 6 dimensions and the columns could be 1 dimension. Always use the word rank to distinguish vectors, matrices, and higher-order tensors. The components that make up rank are called axes (plural of axis). The dimension is how many elements are in a particular axis. The shape of a tensor combines all of these. A shape is a tuple (ordered list of numbers) whose length is the rank and elements are the dimension of each axis.

## Einstein Summation

## Tensor Operations

### Reduction Operations

### Element Operations

### Broadcasting

## Shape Manipulation

## View vs Copy