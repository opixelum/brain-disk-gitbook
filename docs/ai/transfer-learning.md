# Transfer Learning

- Use pre-trained models or parts of models for another model;
- Uses previous learnt weights;
- If not doing fine tuning, reused models or parts of models shouldn't be
  trainable. If so, the untrained weights of the new part of the model will
  initially create large gradient updates, which propogate back into the base
  layers and destroy much of the pretraining.

## Fine Tuning

- Retrain models for improvements or better fit with the new model.
