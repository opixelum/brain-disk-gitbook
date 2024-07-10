# Backpropagation

## Definition

- Learning algorithm for neural networks;
- Updates the weights for better predictions.

## Loss Function

- Metric telling how the model performs by showing difference between the
  predicted and the actual output;
- A high value means the model is not performing well.

### Loss derivative (gradient)

- Used in backpropagation at the output layer level (first step of the
  backpropagation):

```python
# Backward pass
error = compute_loss_gradient(y, output)
for layer in reversed(self.layers):
    error = layer.backward(error, learning_rate, self.optimizer, epoch + 1)
```

- Don't confuse the "normal" loss, which is for the model metrics, and the loss
  derivative, used in backpropagation.

### Mean Squared Error (MSE)

### Cross Entropy

## Optimization Algorithms

- Minimize the loss function by updating the weights of the network.

### Gradient Descent

### RMSProp

### Adam

Snippet from a backpropagation method in a model class:

```python
beta1, beta2, epsilon = 0.9, 0.999, 1e-8

# Momentum
self.m_w = beta1 * self.m_w + (1 - beta1) * weights_error
self.m_b = beta1 * self.m_b + (1 - beta1) * bias_error

# RMSprop
self.v_w = beta2 * self.v_w + (1 - beta2) * (weights_error**2)
self.v_b = beta2 * self.v_b + (1 - beta2) * (bias_error**2)

# Bias correction
m_w_hat = self.m_w / (1 - beta1**t)
m_b_hat = self.m_b / (1 - beta1**t)
v_w_hat = self.v_w / (1 - beta2**t)
v_b_hat = self.v_b / (1 - beta2**t)

# Update weights and biases
self.weights -= learning_rate * m_w_hat / (np.sqrt(v_w_hat) + epsilon)
self.bias -= learning_rate * m_b_hat / (np.sqrt(v_b_hat) + epsilon)
```

## References

- [Brilliant—Backpropagation](https://brilliant.org/wiki/backpropagation/)

```

```
