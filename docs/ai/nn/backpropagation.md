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

## References

- [Brilliant—Backpropagation](https://brilliant.org/wiki/backpropagation/)

```

```
