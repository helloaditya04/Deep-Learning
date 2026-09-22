# Fine-Tuning Neural Network Hyperparameters

## 1. Fine-Tuning Neural Network Hyperparameters

Hyperparameters are settings that are chosen **before training** a neural network.

Fine-tuning means adjusting these settings to improve the model's performance.

### i. Number of Hidden Layers

A hidden layer is a layer between the input and output layers.

- More hidden layers → model can learn more complex patterns.
- Too many layers → training becomes slower and may cause overfitting.
- Too few layers → model may not learn complex relationships.

### ii. Number of Neurons per Layer

Each hidden layer contains neurons.

- More neurons → greater learning capacity.
- Too many neurons → may cause overfitting and increase training time.
- Too few neurons → may cause underfitting.

### iii. Learning Rate

The learning rate determines how large a step the model takes while updating its weights.

- Small learning rate → slow learning.
- Large learning rate → may overshoot the minimum.
- Proper learning rate → faster and stable learning.

### iv. Optimizers

An optimizer decides how the weights of the neural network are updated to reduce the loss.

Common optimizers:

- **SGD** — Stochastic Gradient Descent
- **Adam** — Adaptive Moment Estimation
- **RMSprop**

### v. Activation Function

An activation function introduces **non-linearity** into a neural network, allowing it to learn complex patterns.

Common activation functions:

| Activation Function | Common Use |
|---|---|
| ReLU | Hidden layers |
| Sigmoid | Binary classification |
| Softmax | Multi-class classification |
| Tanh | Hidden layers / sequence models |

### vi. Number of Epochs

An **epoch** means one complete pass through the entire training dataset.

- Too few epochs → underfitting.
- Too many epochs → overfitting.

**Early stopping** can be used to stop training when validation performance stops improving.

### vii. Batch Size

Batch size is the number of training samples processed before the model updates its weights.

Example:

```text
Dataset = 1000 samples
Batch size = 100

Number of batches = 1000 / 100 = 10
