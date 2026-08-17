## ⚠️ Limitations of the Perceptron

While the Perceptron was a foundational breakthrough in neural networks, it has a critical limitation: **it can only learn linearly separable patterns**.

### Why This Happens

A Perceptron is a **single-layer neural network** that produces a **binary output** by learning a linear decision boundary (a straight line in 2D, or a hyperplane in higher dimensions) that separates two classes.

- ✅ **If the data is linearly separable** — meaning a straight line/hyperplane can cleanly divide the classes — the Perceptron **will converge** to a correct solution.
- ❌ **If the data is *not* linearly separable**, the Perceptron **cannot converge**. It will keep adjusting weights indefinitely, oscillating without ever finding a stable decision boundary.

### Classic Example: XOR Problem

The most famous illustration of this limitation is the **XOR (exclusive OR) function**:

| Input A | Input B | XOR Output |
|:-------:|:-------:|:----------:|
|    0    |    0    |     0      |
|    0    |    1    |     1      |
|    1    |    0    |     1      |
|    1    |    1    |     0      |

No single straight line can separate the `0`s from the `1`s in this case — the Perceptron fundamentally fails here.

### The Fix: Multi-Layer Networks

This limitation is why **Multi-Layer Perceptrons (MLPs)** — networks with one or more hidden layers and non-linear activation functions — were introduced. By stacking layers and applying non-linear transformations, MLPs can learn **non-linear decision boundaries**, solving problems like XOR that a single-layer Perceptron never could.

> 💡 **Key takeaway:** Linear separability is the make-or-break condition for a single-layer Perceptron. Everything more complex requires depth (more layers) and non-linearity.
