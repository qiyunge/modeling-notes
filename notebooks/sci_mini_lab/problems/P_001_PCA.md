# PCA - Principal Component Analysis

## 1. Problem

### 1.1 Problem Statement

Given a set of high-dimensional data samples:
$$
x_1, x_2, \ldots, x_n \in \mathbb{R}^d
$$

the goal is to represent the data in a lower-dimensional subspace ($k \ll d$) while preserving as much relevant information as possible.

---

### 1.2 Objective

- Find a set of orthogonal directions $v_1,v_2, \ldots, v_k$
- Such that the sample variance(a statistic) of the data projected onto these directions is maximized

$$
\max_{v} S^2(v)= \frac{1}{n}\sum_{i=1}^{n} \bigl( v^\top X_i - v^\top\bar{X} \bigr)^2

$$

- Use a small number of dimensions to capture the dominant structure of the data

---

### 1.3 Assumptions

- The data has been centered(zero mean)
- Only linear structure is considered
- Information is measured using second-order statistics (variance/ covariance)

---

## 2. Model

This problem is formulated using the following modeling abstractions:

- **Covaiance Model**

The global structure of the data is described by second-order statistics

- **Quadratic Form Model**

Projected variance can be expressed as a quadratic form optimaztion problem.

See model definition in:

- [M-001_Covariance.md](../models/M_001_Covariance.md)
- M_002_Quadratic_Form.md



