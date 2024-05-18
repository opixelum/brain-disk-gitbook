# Multilayer Perceptron (MLP)

## Structure

- Multiple linear models (perceptrons);
- TanH activation in hidden layers over sigmoid (logistic);
- Linear (identity) activation for output layer for regression;
- TanH activation for output layer for binary classification;
- Small learning rate can lead to local minimum;
- The higher the dimension of the loss, the lower the chance is to fall into a
  local minimum;
- SGD will always lead to the global minimum of the loss;
- Initialize weights between -0.01 and 0.01.
  Small weights with TanH require less iterations;
- High learning rates can lead to NaN values (number greater than bit limits);
