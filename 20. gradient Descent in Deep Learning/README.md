# Gradient Descent

## What is Gradient Descent?

**Gradient Descent** is one of the most popular optimization algorithms used to **minimize an objective/cost function**.

It is also one of the most common methods used to **optimize neural networks**.

---

## Basic Idea

Suppose we have an objective function:

\[
J(\theta)
\]

where:

- `J(θ)` → Objective/Cost function
- `θ` → Model parameters (weights and biases)

Gradient Descent minimizes `J(θ)` by updating the parameters in the **opposite direction of the gradient**.

---

## Gradient Descent Formula

The parameters are updated using:

\[
\theta = \theta - \eta \nabla J(\theta)
\]

### Where:

| Symbol | Meaning |
|---|---|
| `θ` | Model parameters |
| `J(θ)` | Objective/Cost function |
| `∇J(θ)` | Gradient of the cost function |
| `η` | Learning rate |
| `−` | Move in the opposite direction of the gradient |

---

## Why Do We Move in the Opposite Direction?

The **gradient** tells us the direction of the **steepest increase** in the cost function.

But our goal is to **minimize the cost**.

Therefore, we move in the **opposite direction of the gradient**.

### Simple Intuition

Imagine standing on a hill:

- **Gradient** → Direction uphill
- **Negative gradient** → Direction downhill
- **Gradient Descent** → Keep moving downhill until reaching a minimum/valley

```text
                 Cost
                  ^
                  |
              *       *
            *           *
          *               *
        *                   *
      *          ↓          *
    *             ↓           *
  *               ↓             *
 *_______________________________*____> θ
                  |
               Minimum
```

## Learning Rate

The **learning rate (`η`)** determines the **size of the step** taken during each parameter update in Gradient Descent.

### Effect of Learning Rate

| Learning Rate | Step Size | Effect |
|---|---|---|
| **Small `η`** | Small steps | Learning is slow |
| **Large `η`** | Large steps | May overshoot the minimum |
| **Proper `η`** | Appropriate steps | Reaches the minimum efficiently |

### Simple Intuition

Imagine going downhill toward the bottom of a valley:

```text
Small learning rate:
   ↓   ↓   ↓   ↓
  \              /
   \            /
    \__________/
     Slow steps


Large learning rate:
       ↓
  \          /
   \        /
    \______/
       ↓
   May jump
   over minimum


Proper learning rate:
      ↓
     ↓
    ↓
   \________/
      Minimum
