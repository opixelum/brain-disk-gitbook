# Deep Learning Markdown Cheat Sheet

## Introduction

Deep Learning is a subset of machine learning, focusing on neural networks with many layers.

## Neural Networks Basics

**Feedforward Neural Network (FNN)**: The simplest type of neural network where information travels in one direction, from input to output.

**Backpropagation**: The main algorithm for weight updating in neural networks.

## Activation Functions

- **Sigmoid**;
- **ReLU (Rectified Linear Unit)**;
- **Tanh**.

## Training

**Loss Functions**:

- **Mean Squared Error (MSE)**: For regression problems.
- **Cross-Entropy Loss**: For classification problems.

**Epoch**: One forward and backward pass of all training samples.

**Batch Size**: The number of training samples in one forward and backward pass.

**Iterations**: Number of passes, each pass using `[batch size]` number of samples.

## Regularization

- **Dropout**: Randomly sets a fraction of the input units to 0 at each update during training.
- **L1 & L2 Regularization**: Adds a penalty to the loss function. L1 penalizes the absolute values of weights and L2 penalizes squared values.

## Optimizers

- **Gradient Descent**: Updates weights in the negative direction of the gradient.
- **Stochastic Gradient Descent (SGD)**: Same as gradient descent but updates are made after each training sample.
- **Adam**: Combines the advantages of AdaGrad and RMSProp algorithms to provide an optimization algorithm that can handle sparse gradients.

## Architectures

- **Convolutional Neural Networks (CNNs)**: Especially powerful for tasks like image recognition.
- **Recurrent Neural Networks (RNNs)**: Suitable for sequential data like time series or natural language.
- **Long Short-Term Memory (LSTM)**: A type of RNN that can remember long-term dependencies.

## Frameworks

- **TensorFlow**: Open-source software library for high-performance numerical computations.
- **Keras**: High-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano.
- **PyTorch**: Open source machine learning library based on Torch, used for applications such as computer vision and NLP.
