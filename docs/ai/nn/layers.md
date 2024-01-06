# Layers

## Convolutional Layer

- Extracts attributes from the input data;
- The number of neurons is equal to the number of filters (kernels);
- Each neuron has a different kernel;
- Each neuron processes a part of the input data (receptive field) at the time.
  When it is done with a receptive field, it moves to the next one;
- After a neuron has processed the whole input data, it results in a feature
  map.

## Pooling Layer

- Reduces the spatial dimension of the input data;
- Helps reduce the number of parameters and computational complexity in the
  network;
- Common methods are average and max pooling.

## Dropout Layer

- Used to prevent overfitting;
- Randomly drops out (by setting the activation to 0) neurons during training.

## Flatten Layer

- Converts the input into a 1D array.

## Dense (Fully Connected) Layer

- Used to classify the extracted features;
- Each neuron is connected to all the neurons in the previous layer;
- Needs a flattened input (1D array).


## References

- [TensorFlow—Image classification](https://www.tensorflow.org/tutorials/images/classification)