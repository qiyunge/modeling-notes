# Eigen Decompostion

## PURPOSE

Compute the eigenvalues and eigenvectors of a square matrix, providing a spectral representation that reveal its intrinsic directions and associated scalar magnitudes.

This algorithm is used to analyze linear operators that act on a finite-dimensional vector space.

---

## INPUT

- A square matrix $A \in \mathbb{R}^{dxd}
- Structural assumptions may apply:
  - Symmetric (most common in practice)
  - Diagonalizable
- Optional numerical parameters:
  - tolerance
  - maximum iterations(for iterative variants)

---

## OUTPUT

- Eigenvalues:
  - $\lambda_1, \lambda_2, \ldots, \lambda_n \in \mathbb {R} (or \mathbb{C} in the general case)$
- Eigenvectors:
  - $v_1, v_2, \ldots, v_d$
- Spectral representation:
  - $A = V \Lambda V^{-1}$ (general case)
  - $A = V \Lambda V^{\top}$ (symmetric case)

---

## WHAT IT SOLVES

The algorithm solves the spectral problem:

Find non-zero vectors v and scalar $\lambda$ such that:
$$
Av = \lambda v
$$

Equivalently, it identifies invariant directions of the linear transformation defined by A, along which the action of A reduces to scalar scaling.

---

## HOW IT WORKS (Conceptual)

At a conceptual level, eigen decomposition proceeds by:

- Identifying directions that remain collinear under the action of A
- Decomposing the space into invariant subspaces
- Expressing A as a linear combination of projections onto these subspaces

For symmetric matrices:

- Eigenvectors form an orthonormal basis
- Eigenvalues are real
- The matrix is orthogonally diagonalizable

For general matrices:

- Eigenvectors may not be orthogonal
- Eigenvalues may be complex
- Diagonalization may not exist or may be numerically unstable

The specific numerical procedure depends on matrix properties and
is abstracted away at this level.

---

## COMPUTATIONAL PROPERTIES

For a dense matrix A ∈ ℝ^{d×d}:

- Time complexity:
  - O(d³) for full eigen decomposition
- Space complexity:
  - O(d²)

Properties:

- Exact for ideal arithmetic
- Sensitive to numerical conditioning
- Stability improves significantly for symmetric matrices

---

## ASSUMPTIONS AND CONDITIONS

- The matrix must be square
- Diagonalizability is required for full decomposition
- For orthogonal diagonalization:
  - A must be symmetric (real case)
- Eigenvectors are defined up to scalar multiplication
- Eigenvalue multiplicity affects uniqueness of eigenvectors

---

## LIMITATIONS

- Computationally expensive for large d
- Not suitable for large-scale problems without approximation
- Sensitive to noise and rounding errors for non-symmetric matrices
- Cannot be applied directly to rectangular matrices

---

## RELATION TO MODELS

Eigen decomposition operates on mathematical objects produced by models such as:

- Covariance-based models
- Quadratic form models
- Linear operator models

It does not define these models, but provides a way to analyze
their associated linear transformations.

---

## NOTES

- In practice, specialized variants exist for:
  - symmetric matrices
  - sparse matrices
  - partial spectrum computation
- For large-scale problems, iterative methods or SVD-based approaches
  are often preferred
