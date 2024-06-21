# Fitting

- Minibatch (or just "batch"): group of training data sample for an
  iteration (before measuring the loss & optimize);
- Epoch: an iteration through the whole training dataset. The number of epochs
  is how many times the network will see each training example;
- Gradient: vector telling in which direction the weights need to go for
  minimizing the loss;
- Smaller batch size leads to noisier weights updates and loss curves, but in
  some case, it can have an "averaging" effect which can be beneficial;
- Smaller learning rates makes the training process longer but with more
  chance to hit the global minimum of the loss function.
  Bigger learning rates take less time to converge, but can't find the global
  minimum as good as with a smaller learning rate.
