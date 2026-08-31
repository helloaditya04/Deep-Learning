# 🧠 Perceptron vs Neuron — Notes

Notes on Perceptrons, Neurons, and Geometric Intuition behind linear classifiers.

---

## 📌 Table of Contents

- [What is a Perceptron?](#what-is-a-perceptron)
- [Perceptron vs Neuron](#perceptron-vs-neuron)
- [The Perceptron Equation](#the-perceptron-equation)
- [Why Neurons? Biological Inspiration](#why-neurons-biological-inspiration)
- [Geometric Intuition](#geometric-intuition)
- [Limitations of a Perceptron](#limitations-of-a-perceptron)
- [Example Dataset](#example-dataset)
- [Code](#code)

--- 

## What is a Perceptron?

> A **perceptron** is a simple type of artificial neuron / the basic algorithm of a neural network, developed by **Frank Rosenblatt in 1957**. It's the basic unit of a neural network — taking multiple binary inputs and producing a single binary output.

It computes a **weighted sum** of its inputs, applies an **activation function**, and produces an output.

```
Inputs (x₁, x₂, ..., xₙ) → Weighted Sum (Σ) → Activation Function (f) → Output
```

---

## Perceptron vs Neuron

| Term | Meaning |
|------|---------|
| **Perceptron** | Refers specifically to the algorithm developed by Rosenblatt — typically uses a **step function** as its activation. |
| **Neuron** | A more general term used in the context of biological *and* artificial neural networks. It encompasses various activation functions **beyond** the step function. |

---

## The Perceptron Equation

The weighted sum (pre-activation) is given by:

```
z = w₁x₁ + w₂x₂ + b
```

Where:
- `x₁, x₂` → inputs
- `w₁, w₂` → weights (**connection strength / importance factor**)
- `b` → bias

**How weights & bias are learned:**
With the help of inputs `x₁, x₂`, we calculate `w₁, w₂, b` through **training data**, and then use them to make **predictions** on **testing data**.

### Activation Function

The output is passed through an activation function `f`:

```
y = f(z) = 1   if z ≥ 0
y = f(z) = 0   if z < 0
```

Depending on the use case, the range of `z` can be bounded, e.g.:
- `[-1, 1]`
- `[0, 1]`

---

## Why Neurons? Biological Inspiration

1. **Complex** — processing happens via a function.
2. **Processing by nucleus** — (unplanned / electrochemical).
3. **Neuroplasticity** — the brain grows new connections over time; signals may or may not pass through, depending on the strength of the connection (like scar/skin healing over a wound — some connections weaken/block, some grow stronger).

---

## Geometric Intuition

The weighted sum equation:

```
z = w₁x₁ + w₂x₂ + b
```

...is really the general equation of a hyperplane:

```
z = Ax + By + C
```

| Dimension | Geometric Shape |
|-----------|-----------------|
| 2D | Line |
| 3D | Plane |
| 4D+ | Hyperplane |

A perceptron essentially **draws a decision boundary** (line/plane/hyperplane) to separate classes.

```
      x x x            ✓ ✓ ✓
    x x   x  x       ✓   ✓  ✓
  x x x x        ✓ ✓ ✓  ✓
    x x    ___________  ✓ ✓
              ↑
        decision boundary (z)
```

---

## Limitations of a Perceptron

- A perceptron **can only classify linearly separable data** — data that can be separated using a straight line, plane, or hyperplane.
- If the classes overlap or are **non-linearly separable** (e.g., some red points fall in the green region and vice versa), a **single perceptron will fail** to classify the data completely.

> ⚠️ If we have completely non-linear data, a perceptron will fail. This is why **multi-layer neural networks** (with non-linear activation functions) are needed to model complex, non-linear relationships.

---

## Example Dataset

Sample toy dataset — predicting **placement** based on **CGPA**:

| CGPA | Placement |
|------|-----------|
| 7.9  | 1         |
| 7.8  | 1         |
| 6.9  | 0         |
| 5.4  | 0         |

---

## Code

Simple perceptron implementation trained on the toy CGPA/placement dataset above, with a decision boundary plot.

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt


# ---------------------------
# 1. Toy Dataset
# ---------------------------
data = {
    "cgpa": [7.9, 7.8, 6.9, 5.4],
    "profile_score": [1, 1, 5.4, 0],   # 2nd feature (placeholder)
    "placement": [1, 1, 0, 0]
}
df = pd.DataFrame(data)

X = df[["cgpa", "profile_score"]].values
y = df["placement"].values


# ---------------------------
# 2. Step Activation Function
# ---------------------------
def step_function(z):
    return 1 if z >= 0 else 0


# ---------------------------
# 3. Perceptron Class
# ---------------------------
class Perceptron:
    def __init__(self, n_features, learning_rate=0.01, epochs=1000):
        self.weights = np.zeros(n_features)
        self.bias = 0.0
        self.lr = learning_rate
        self.epochs = epochs

    def predict(self, x):
        z = np.dot(self.weights, x) + self.bias   # z = w1*x1 + w2*x2 + b
        return step_function(z)

    def fit(self, X, y):
        for epoch in range(self.epochs):
            for xi, target in zip(X, y):
                y_pred = self.predict(xi)
                error = target - y_pred

                # weight update rule
                self.weights += self.lr * error * xi
                self.bias += self.lr * error

        return self.weights, self.bias


# ---------------------------
# 4. Train the Perceptron
# ---------------------------
model = Perceptron(n_features=X.shape[1], learning_rate=0.01, epochs=1000)
weights, bias = model.fit(X, y)

print("Trained weights:", weights)
print("Trained bias:", bias)


# ---------------------------
# 5. Plot Decision Boundary
# ---------------------------
def plot_decision_boundary(X, y, weights, bias):
    sns.scatterplot(x=X[:, 0], y=X[:, 1], hue=y, palette=["red", "green"], s=100)

    # decision boundary: w1*x1 + w2*x2 + b = 0  ->  x2 = -(w1*x1 + b) / w2
    x1_vals = np.linspace(X[:, 0].min() - 1, X[:, 0].max() + 1, 100)
    if weights[1] != 0:
        x2_vals = -(weights[0] * x1_vals + bias) / weights[1]
        plt.plot(x1_vals, x2_vals, color="blue", label="Decision Boundary")

    plt.xlabel("CGPA")
    plt.ylabel("Profile Score")
    plt.title("Perceptron Decision Boundary")
    plt.legend()
    plt.show()


plot_decision_boundary(X, y, weights, bias)


# ---------------------------
# 6. Test Predictions
# ---------------------------
for xi in X:
    print(f"Input: {xi} -> Predicted: {model.predict(xi)}")
```

---

### 🔑 Key Takeaways

- **Perceptron** = simplest artificial neuron, uses a **step activation function**.
- **Neuron** = generalized concept, supports many activation functions.
- Perceptrons draw **linear decision boundaries** — they fail on non-linearly separable data.
- Modern **neural networks** stack multiple neurons/layers with non-linear activations to overcome this limitation.




