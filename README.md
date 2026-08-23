# MLP MNIST Digit Recognition

## Project Overview

This project implements a **Multilayer Perceptron (MLP)** for handwritten digit classification using the **MNIST dataset**.

The goal was not only to train a neural network, but to understand the complete learning process:

**Input → Forward Pass → Loss → Backpropagation → Optimization → Prediction**

The project was developed using **Python and PyTorch**, with additional experimentation using an interactive digit-drawing interface.

---

## Problem

The task is to classify a handwritten digit into one of 10 classes:

**0, 1, 2, ..., 9**

Each MNIST image contains a handwritten digit represented by a **28×28 pixel image**.

The image is flattened into:

**28 × 28 = 784 input features**

---

## Dataset — MNIST

MNIST contains:

* 60,000 training images
* 10,000 test images
* Image size: 28×28 pixels
* 10 digit classes

Each image is converted into a vector of 784 input values before being passed to the neural network.

---

## MLP Architecture

The implemented network has the following architecture:

```text
784 → 128 → 10
```

### Layers

* **Input:** 784 features
* **Hidden Layer:** 128 neurons
* **Activation:** ReLU
* **Output:** 10 neurons

Each output neuron corresponds to one digit class.

The network is fully connected between consecutive layers.

---

## How the Neural Network Works

### 1. Neuron

Each neuron calculates a weighted sum of its inputs and adds a bias:

```text
z = Σ(xᵢwᵢ) + b
```

The weights and biases are learned during training.

### 2. Forward Pass

During a forward pass, the input propagates through the network:

```text
Input
  ↓
Linear Layer
  ↓
ReLU
  ↓
Linear Layer
  ↓
10 Output Scores
```

### 3. ReLU

The hidden layer uses the ReLU activation function:

```text
ReLU(x) = max(0, x)
```

ReLU introduces non-linearity, allowing the network to learn more complex relationships in the data.

---

## Loss and Learning

The model uses **Cross Entropy Loss** to measure the difference between its prediction and the true label.

The training process follows:

```text
Forward Pass
     ↓
Loss Calculation
     ↓
Backpropagation
     ↓
Gradient Calculation
     ↓
Optimizer Update
```

Backpropagation calculates the gradients of the loss with respect to the model parameters.

The optimizer then uses these gradients to update the weights and biases.

---

## Training Configuration

The implemented training process uses:

* Batch Size: **64**
* Epochs: **10**
* Optimizer: **SGD**
* Learning Rate: **0.01**
* Loss Function: **Cross Entropy**

Training is performed batch by batch, with the model parameters updated after each batch.

---

## Evaluation

After training, the model is evaluated on the MNIST test set.

The model achieved approximately:

**93% Test Accuracy**

The test set is used to evaluate how well the trained model generalizes to examples that were not used during training.

---

## Prediction and Probability

The network produces 10 output scores, one for each digit class.

These scores can be converted into probabilities using **Softmax**.

The class with the highest probability is selected as the model's prediction.

---

## Interactive Digit Drawing

To test the model beyond the original MNIST test set, an interactive digit-drawing interface was developed.

The process is:

```text
Canvas
  ↓
Image Preprocessing
  ↓
28×28 Image
  ↓
Normalization
  ↓
Flattening
  ↓
MLP
  ↓
Prediction
```

The preprocessing step includes adapting the user-drawn image to the format expected by the trained model.

---

## Real-World Testing

Testing with personally drawn digits revealed an important limitation.

Although the model achieved approximately 93% accuracy on MNIST, it showed difficulties with certain handwritten examples, particularly **7 and 9**.

Several approaches were explored:

* Fine-Tuning
* Data Augmentation
* Preprocessing

The goal was to determine whether the model could better handle handwriting that differed from the MNIST distribution.

---

## Key Lesson — Generalization

One of the main lessons from the project was that good performance on a dataset does not automatically guarantee equally good performance on different input distributions.

The MNIST test accuracy provided a useful overall metric, but testing with real handwritten input exposed cases where the model struggled.

This demonstrated the importance of evaluating not only accuracy, but also how well a model generalizes to new types of data.

---

## What I Learned

Through this project I developed a practical understanding of:

* Neural network architecture
* Neurons, weights and biases
* Forward propagation
* Activation functions
* Loss functions
* Backpropagation
* Gradients
* Gradient descent and optimization
* Batch-based training
* Model evaluation
* Generalization and error analysis

The project connected the mathematical theory of neural networks with an implemented working model.

---

## Next Step

The next stage of the project is to take the trained MLP toward an **FPGA implementation**.
