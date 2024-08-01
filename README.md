# SVD for Learning Word Representations

This repository explains the use of Singular Value Decomposition (SVD) for learning word representations in detail.

## 1. Theory

**Singular Value Decomposition (SVD):** SVD is a matrix factorization technique that decomposes a matrix \(A\) into three matrices:

A = UΣV^T

Where:
- U is a matrix whose columns are the left singular vectors of A.
- Σ  is a diagonal matrix containing the singular values of A.
- V (or V^T) is a matrix whose columns are the right singular vectors of A.

**Learning Word Representations:** To learn word representations, we often use a co-occurrence matrix X, where each entry X_{ij} represents the number of times word i  co-occurs with word j within a certain context window.

By applying SVD to the co-occurrence matrix, we can reduce its dimensionality and obtain dense word vectors that capture semantic relationships between words.

## 2. Numerical Example

Consider a small corpus: "I like deep learning" and "I like NLP".

1. **Build the Vocabulary:**
   - Vocabulary: ["I", "like", "deep", "learning", "NLP"]

2. **Create the Co-occurrence Matrix:**
   
   Let's assume a context window of 1 (one word to the left and right):

   |       | I | like | deep | learning | NLP |
   |-------|---|------|------|----------|-----|
   | I     | 0 | 2    | 0    | 0        | 0   |
   | like  | 2 | 0    | 1    | 1        | 1   |
   | deep  | 0 | 1    | 0    | 1        | 0   |
   | learning | 0 | 1    | 1    | 0        | 0   |
   | NLP   | 0 | 1    | 0    | 0        | 0   |

3. **Apply SVD:**
   
   Let  X be the co-occurrence matrix. Perform SVD on  X:

   X = UΣV^T

   For simplicity, let's assume we truncate to k = 2  dimensions.

## 3. Mathematical Explanation with Examples

**Step-by-Step SVD:**

1. **Compute \( X^T X \):**
   

   Given the co-occurrence matrix \( X \):

\[ X^T X = \]

|       | I | like | deep | learning | NLP |
|-------|---|------|------|----------|-----|
| I     | 0 | 2    | 0    | 0        | 0   |
| like  | 2 | 0    | 1    | 1        | 1   |
| deep  | 0 | 1    | 0    | 1        | 0   |
| learning | 0 | 1    | 1    | 0        | 0   |
| NLP   | 0 | 1    | 0    | 0        | 0   |

\(\times\)

|       | I | like | deep | learning | NLP |
|-------|---|------|------|----------|-----|
| I     | 0 | 2    | 0    | 0        | 0   |
| like  | 2 | 0    | 1    | 1        | 1   |
| deep  | 0 | 1    | 0    | 1        | 0   |
| learning | 0 | 1    | 1    | 0        | 0   |
| NLP   | 0 | 1    | 0    | 0        | 0   |


2. **Compute Eigenvalues and Eigenvectors:**

   The eigenvalues of \( X^T X \) give us the singular values (diagonal entries of \( \Sigma \)), and the eigenvectors give us \( U \) and \( V \).

3. **Form the Matrices \( U \), \( \Sigma \), and \( V^T \):**

   For our example, this results in:

   \[
   U = 
   \begin{bmatrix}
       ... \\
       ... \\
   \end{bmatrix}, \quad
   \Sigma = 
   \begin{bmatrix}
       ... & 0 \\
       0 & ... \\
   \end{bmatrix}, \quad
   V^T = 
   \begin{bmatrix}
       ... & ... & ... \\
       ... & ... & ... \\
   \end{bmatrix}
   \]

   (Note: Actual values would depend on the calculation of eigenvalues and eigenvectors.)

## 4. Real-time Example of a Corpus

Consider a small corpus:
"I like deep learning"
"I like NLP"
"NLP is fun"
"deep learning is fun"


1. **Vocabulary:**
   - ["I", "like", "deep", "learning", "NLP", "is", "fun"]

2. **Create the Co-occurrence Matrix:**
   
   Assuming a context window of 1:

   |       | I | like | deep | learning | NLP | is | fun |
   |-------|---|------|------|----------|-----|----|-----|
   | I     | 0 | 2    | 0    | 0        | 0   | 0  | 0   |
   | like  | 2 | 0    | 1    | 0        | 1   | 0  | 0   |
   | deep  | 0 | 1    | 0    | 1        | 0   | 1  | 0   |
   | learning | 0 | 0  | 1    | 0        | 0   | 1  | 0   |
   | NLP   | 0 | 1    | 0    | 0        | 0   | 1  | 1   |
   | is    | 0 | 0    | 1    | 1        | 1   | 0  | 2   |
   | fun   | 0 | 0    | 0    | 0        | 1   | 2  | 0   |

3. **Apply SVD:**
   
   Perform SVD on the co-occurrence matrix \( X \):

   \[ X = U \Sigma V^T \]

## 5. Code Example for a Small Corpus

Here's a simple Python code example using `numpy` and `scipy` for SVD:

```python
import numpy as np
from scipy.linalg import svd

# Sample corpus
corpus = ["I like deep learning", "I like NLP", "NLP is fun", "deep learning is fun"]

# Create a vocabulary
vocab = list(set(" ".join(corpus).split()))
vocab_size = len(vocab)
word_to_index = {word: i for i, word in enumerate(vocab)}

# Create the co-occurrence matrix
co_occurrence = np.zeros((vocab_size, vocab_size))

for sentence in corpus:
    words = sentence.split()
    for i in range(len(words)):
        for j in range(max(0, i-1), min(len(words), i+2)):
            if i != j:
                co_occurrence[word_to_index[words[i]], word_to_index[words[j]]] += 1

# Perform SVD
U, Sigma, Vt = svd(co_occurrence)

# Reduce dimensionality to 2 (for visualization)
k = 2
U_k = U[:, :k]
Sigma_k = np.diag(Sigma[:k])
Vt_k = Vt[:k, :]

# Get word representations
word_representations = np.dot(U_k, Sigma_k)

# Print word representations
for word, index in word_to_index.items():
    print(f"Word: {word}, Representation: {word_representations[index]}")
```

