# Lesson 1 of 50 — NumPy for ML: Arrays & Vectorized Math
*~15 minutes | Phase 1: ML Foundations*

---

## 🧠 Concepts

### Why NumPy?

Machine learning is fundamentally about doing math on large collections of numbers — thousands of pixel values, millions of training examples, weight matrices with millions of parameters. Python lists are flexible but slow; they process one element at a time in pure Python.

**NumPy** solves this by storing data in contiguous memory blocks and offloading math to optimised C/Fortran routines. The result: operations that would take seconds in plain Python run in milliseconds.

### The ndarray

The core object is the **n-dimensional array** (`ndarray`). Think of it as a grid that can be:
- 1-D: a vector `[1, 2, 3]`
- 2-D: a matrix (rows × columns), e.g. a dataset where each row is a sample
- 3-D+: e.g. a batch of images (batch × height × width × channels)

### Vectorized Math

Instead of looping over elements, NumPy operations apply to *every element at once*:

```python
# Slow Python loop
result = [x * 2 for x in my_list]

# Fast NumPy vectorization
result = my_array * 2   # applies to all elements simultaneously
```

This pattern — no explicit loops, math applied element-wise or across axes — is called **vectorization** and is the cornerstone of efficient ML code.

### Key concepts to know
- **shape**: the dimensions of an array, e.g. `(100, 3)` = 100 rows, 3 columns
- **dtype**: the data type (float32, float64, int64, …). ML models almost always use `float32` to save memory
- **broadcasting**: NumPy's rule for applying operations between arrays of different (but compatible) shapes, e.g. adding a shape-`(3,)` bias to every row of a shape-`(100, 3)` matrix

---

## 🐍 Python Exercise

```python
import numpy as np

# -----------------------------------------------------------
# 1. Creating arrays
# -----------------------------------------------------------
a = np.array([1.0, 2.0, 3.0])          # 1-D vector
B = np.array([[1, 2, 3],
              [4, 5, 6]], dtype=np.float32)  # 2-D matrix (2×3)

print("a shape:", a.shape)     # (3,)
print("B shape:", B.shape)     # (2, 3)
print("B dtype:", B.dtype)     # float32

# -----------------------------------------------------------
# 2. Common initialisers
# -----------------------------------------------------------
zeros  = np.zeros((3, 4))          # all zeros, shape 3×4
ones   = np.ones((2, 2))           # all ones
rand   = np.random.randn(4, 4)     # standard normal (μ=0, σ=1)
eye    = np.eye(3)                 # 3×3 identity matrix

# -----------------------------------------------------------
# 3. Vectorized arithmetic (no Python loops!)
# -----------------------------------------------------------
x = np.array([1.0, 4.0, 9.0, 16.0])

print("x + 10  :", x + 10)          # [11. 14. 19. 26.]
print("x * 0.5 :", x * 0.5)         # [0.5  2.  4.5  8. ]
print("sqrt(x) :", np.sqrt(x))      # [1.  2.  3.  4. ]
print("x²      :", x ** 2)          # [  1.  16.  81. 256.]

# -----------------------------------------------------------
# 4. Aggregation along axes
# -----------------------------------------------------------
data = np.array([[2.0, 4.0, 6.0],
                 [1.0, 3.0, 5.0]])

print("Column means:", data.mean(axis=0))   # mean of each column → [1.5 3.5 5.5]
print("Row sums    :", data.sum(axis=1))    # sum of each row    → [12.  9.]

# -----------------------------------------------------------
# 5. Broadcasting — add a bias vector to every row
# -----------------------------------------------------------
weights = np.random.randn(5, 3)   # 5 samples, 3 features
bias    = np.array([0.1, -0.2, 0.3])  # shape (3,)

output = weights + bias   # bias is broadcast across all 5 rows
print("After bias shape:", output.shape)   # (5, 3)

# -----------------------------------------------------------
# 6. Dot product — the core of a linear layer
# -----------------------------------------------------------
X = np.random.randn(10, 4)   # 10 samples, 4 features
W = np.random.randn(4, 2)    # weight matrix: 4 inputs → 2 outputs
b = np.zeros(2)              # bias for 2 outputs

Z = X @ W + b               # matrix multiply then add bias
print("Linear layer output shape:", Z.shape)   # (10, 2)

# -----------------------------------------------------------
# Expected output (values will vary due to random init):
# a shape: (3,)
# B shape: (2, 3)
# B dtype: float32
# x + 10  : [11. 14. 19. 26.]
# x * 0.5 : [0.5 2.  4.5 8. ]
# sqrt(x) : [1. 2. 3. 4.]
# x²      : [  1.  16.  81. 256.]
# Column means: [1.5 3.5 5.5]
# Row sums    : [12.  9.]
# After bias shape: (5, 3)
# Linear layer output shape: (10, 2)
# -----------------------------------------------------------
```

---

## ⚡ Tiny Challenge

1. Create a NumPy array of 1 000 evenly spaced values between 0 and 2π using `np.linspace`. Compute `sin` and `cos` of every value without a loop.

2. Given a matrix `M = np.random.randn(6, 4)`, compute the **L2 norm** (Euclidean length) of each row. The result should be a 1-D array of shape `(6,)`. *Hint: `np.linalg.norm` or squaring + summing + square-rooting along `axis=1`.*

3. Without using any loop, normalise each column of `M` so that it has zero mean and unit variance. *(This is called **standardisation** and is one of the most common data-prep steps in ML.)*

<details>
<summary>💡 Hints & Answers</summary>

**Challenge 1**
```python
t = np.linspace(0, 2 * np.pi, 1000)
s = np.sin(t)
c = np.cos(t)
```

**Challenge 2**
```python
M = np.random.randn(6, 4)
norms = np.linalg.norm(M, axis=1)          # shape (6,)
# or manually:
norms = np.sqrt((M ** 2).sum(axis=1))
```

**Challenge 3**
```python
mean = M.mean(axis=0)          # shape (4,) — one mean per column
std  = M.std(axis=0)           # shape (4,) — one std per column
M_norm = (M - mean) / std      # broadcasting does the rest
```

</details>

---

## 🔑 Key Takeaways

- NumPy `ndarray`s replace Python lists for numerical work — they're orders of magnitude faster thanks to vectorisation.
- Every array has a **shape** (dimensions) and a **dtype** (numeric type); use `float32` in ML pipelines.
- Avoid Python `for` loops over array elements — NumPy operations apply to the whole array at once.
- **Broadcasting** lets NumPy apply math between arrays of different but compatible shapes automatically.
- The matrix multiply `X @ W + b` is literally what a single linear (dense) layer of a neural network computes — you'll see it again in every lesson from here on.

---

## 📬 Feedback
Reply to your Slack message with: **too easy**, **too hard**, or **just right** — and I'll adjust tomorrow's lesson accordingly.
