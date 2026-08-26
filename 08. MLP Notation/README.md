>1.  Multi Layer Perceptron Notation refers to the symbolic representation used to illustrate the architecture and connections within a neural networks.
>
>2. In MLP, nodes(neurons) are organised into layers, including an input layer, hidden layer, and an output layer
>
>3. The notation visually represents the flow of information between layers through weights and activation functions.




## Neural Network Architecture

A fully-connected feedforward neural network with backpropagation support.

### Architecture Overview

```html
<svg width="100%" viewBox="0 0 680 600" role="img">
  <title>Neural Network Architecture</title>
  <desc>A multi-layer feedforward neural network showing input layer, three hidden layers, and output layer with forward propagation (green connections) and backward propagation (red connections)</desc>
  
  <defs>
    <marker id="arrow-green" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
      <path d="M2 1L8 5L2 9" fill="none" stroke="#639922" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/>
    </marker>
    <marker id="arrow-red" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
      <path d="M2 1L8 5L2 9" fill="none" stroke="#E24B4A" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/>
    </marker>
  </defs>

  <!-- Title -->
  <text class="th" x="340" y="30" text-anchor="middle" style="font-size:18px">Neural Network Architecture</text>

  <!-- Layer Labels -->
  <text class="ts" x="40" y="80" style="fill:var(--text-secondary)">Input</text>
  <text class="ts" x="40" y="220" style="fill:var(--text-secondary)">Hidden 1</text>
  <text class="ts" x="40" y="340" style="fill:var(--text-secondary)">Hidden 2</text>
  <text class="ts" x="40" y="430" style="fill:var(--text-secondary)">Hidden 3</text>
  <text class="ts" x="40" y="530" style="fill:var(--text-secondary)">Output</text>

  <!-- INPUT LAYER -->
  <circle cx="120" cy="70" r="20" style="fill:#E6F1FB;stroke:#185FA5;stroke-width:0.5"/>
  <text x="120" y="75" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#0C447C;font-weight:500">b₀</text>
  
  <circle cx="200" cy="70" r="20" style="fill:#E6F1FB;stroke:#185FA5;stroke-width:0.5"/>
  <text x="200" y="75" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#0C447C;font-weight:500">b₁</text>
  
  <circle cx="280" cy="70" r="20" style="fill:#E6F1FB;stroke:#185FA5;stroke-width:0.5"/>
  <text x="280" y="75" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#0C447C;font-weight:500">b₂</text>
  
  <circle cx="360" cy="70" r="20" style="fill:#E6F1FB;stroke:#185FA5;stroke-width:0.5"/>
  <text x="360" y="75" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#0C447C;font-weight:500">b₃</text>

  <!-- HIDDEN LAYER 1 -->
  <circle cx="150" cy="200" r="20" style="fill:#E1F5EE;stroke:#0F6E56;stroke-width:0.5"/>
  <text x="150" y="205" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#085041;font-weight:500">h₁</text>
  
  <circle cx="250" cy="200" r="20" style="fill:#E1F5EE;stroke:#0F6E56;stroke-width:0.5"/>
  <text x="250" y="205" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#085041;font-weight:500">h₂</text>
  
  <circle cx="350" cy="200" r="20" style="fill:#E1F5EE;stroke:#0F6E56;stroke-width:0.5"/>
  <text x="350" y="205" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#085041;font-weight:500">h₃</text>

  <!-- HIDDEN LAYER 2 -->
  <circle cx="190" cy="320" r="20" style="fill:#EEEDFE;stroke:#534AB7;stroke-width:0.5"/>
  <text x="190" y="325" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#3C3489;font-weight:500">a₁</text>
  
  <circle cx="310" cy="320" r="20" style="fill:#EEEDFE;stroke:#534AB7;stroke-width:0.5"/>
  <text x="310" y="325" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#3C3489;font-weight:500">a₂</text>

  <!-- HIDDEN LAYER 3 -->
  <circle cx="250" cy="410" r="20" style="fill:#FAECE7;stroke:#993C1D;stroke-width:0.5"/>
  <text x="250" y="415" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#712B13;font-weight:500">z</text>

  <!-- OUTPUT LAYER -->
  <circle cx="250" cy="520" r="20" style="fill:#FAEEDA;stroke:#854F0B;stroke-width:0.5"/>
  <text x="250" y="525" text-anchor="middle" dominant-baseline="central" style="font-size:12px;fill:#633806;font-weight:500">ŷ</text>

  <!-- FORWARD PASS CONNECTIONS (Green) -->
  <line x1="135" y1="88" x2="140" y2="182" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  <line x1="195" y1="88" x2="240" y2="182" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  <line x1="265" y1="88" x2="260" y2="182" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  <line x1="345" y1="88" x2="360" y2="182" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  
  <line x1="155" y1="218" x2="185" y2="302" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  <line x1="250" y1="218" x2="250" y2="302" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  <line x1="345" y1="218" x2="315" y2="302" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  
  <line x1="200" y1="338" x2="240" y2="392" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  <line x1="300" y1="338" x2="260" y2="392" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>
  
  <line x1="250" y1="428" x2="250" y2="502" stroke="#639922" stroke-width="1.2" opacity="0.6" fill="none" marker-end="url(#arrow-green)"/>

  <!-- BACKWARD PASS CONNECTIONS (Red) -->
  <line x1="250" y1="502" x2="250" y2="428" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  
  <line x1="240" y1="392" x2="200" y2="338" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  <line x1="260" y1="392" x2="300" y2="338" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  
  <line x1="185" y1="302" x2="155" y2="218" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  <line x1="250" y1="302" x2="250" y2="218" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  <line x1="315" y1="302" x2="345" y2="218" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  
  <line x1="140" y1="182" x2="135" y2="88" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  <line x1="240" y1="182" x2="195" y2="88" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  <line x1="260" y1="182" x2="265" y2="88" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>
  <line x1="360" y1="182" x2="345" y2="88" stroke="#E24B4A" stroke-width="1" opacity="0.5" fill="none" marker-end="url(#arrow-red)" stroke-dasharray="3,2"/>

  <!-- Legend -->
  <rect x="400" y="50" width="260" height="80" rx="8" style="fill:#F1EFE8;stroke:#73726C;stroke-width:0.5"/>
  <text x="530" y="75" text-anchor="middle" style="font-size:13px;fill:#2C2C2A;font-weight:500">Forward & Backward Pass</text>
  
  <line x1="420" y1="95" x2="450" y2="95" stroke="#639922" stroke-width="2.5" marker-end="url(#arrow-green)"/>
  <text x="460" y="98" style="font-size:12px;fill:#3d3d3a">Forward pass</text>
  
  <line x1="420" y1="115" x2="450" y2="115" stroke="#E24B4A" stroke-width="1.5" stroke-dasharray="3,2" marker-end="url(#arrow-red)"/>
  <text x="460" y="118" style="font-size:12px;fill:#3d3d3a">Backward pass</text>
</svg>
```

### Network Components

| Layer | Nodes | Purpose |
|-------|-------|---------|
| **Input** | 4 | Initial data features (b₀, b₁, b₂, b₃) |
| **Hidden 1** | 3 | First level feature transformation (h₁, h₂, h₃) |
| **Hidden 2** | 2 | Intermediate representation (a₁, a₂) |
| **Hidden 3** | 1 | Pre-output transformation (z) |
| **Output** | 1 | Final prediction (ŷ) |

### Forward & Backward Propagation

- **Forward Pass** (Solid green arrows): Data flows from input through all hidden layers to produce output prediction
- **Backward Pass** (Dashed red arrows): Gradients flow backward for parameter updates during training

### Key Equations

```
Forward:  z^(l) = W^(l) * a^(l-1) + b^(l)
          a^(l) = σ(z^(l))

Backward: dW^(l) = (1/m) * dz^(l) * a^(l-1)^T
          db^(l) = (1/m) * Σ dz^(l)
          da^(l-1) = W^(l)^T * dz^(l)
```


