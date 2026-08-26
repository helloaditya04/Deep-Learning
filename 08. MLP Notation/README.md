>1.  Multi Layer Perceptron Notation refers to the symbolic representation used to illustrate the architecture and connections within a neural networks.
>
>3. In MLP, nodes(neurons) are organised into layers, including an input layer, hidden layer, and an output layer
>
>5. The notation visually represents the flow of information between layers through weights and activation functions.




## Neural Network Architecture

### Overview
This diagram illustrates a multi-layer neural network with forward and backward propagation paths.

### Network Structure

#### Input Layer
- **b₀, b₁, b₂, b₃** (input nodes)

#### Hidden Layers
- Layer 1: h₁, h₂, h₃, h₄ (with connections from inputs)
- Layer 2: b₀₁, b₀₂, b₀₃ (middle layer nodes)
- Layer 3: b₀₄, b₀₅ (output preparation layer)

#### Output Layer
- **b₀** (final output)

### Connections

**Forward Pass** (Green lines)
- Input nodes connect to all hidden layer nodes
- Each layer fully connected to the next layer

**Backward Pass** (Red lines)
- Gradient flow from output back through the network
- Used for backpropagation during training

### Mathematical Operations

| Layer | Operation | Description |
|-------|-----------|-------------|
| Forward | `h = f(wx + b)` | Activation of hidden layers |
| Output | `ŷ = g(h)` | Final prediction |
| Loss | `L(y, ŷ)` | Compute loss |
| Gradient | `∂L/∂w` | Parameter gradients |

### Key Equations

- **Forward propagation**: `z = Wx + b`
- **Activation**: `a = σ(z)`
- **Backward pass**: Compute gradients using chain rule
- **Gradient updates**: `w ← w - α∇L`

### Notes
- Fully connected feedforward architecture
- Bidirectional flow for training (forward + backward)
- Supports supervised learning tasks
