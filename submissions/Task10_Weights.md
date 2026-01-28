1. Why is the number of parameters so large?

The output (784, 128) represents the weight matrix $W$ connecting the input layer to the first hidden layer.Dense Connectivity: In a Fully Connected (Dense) layer, every single input pixel (28x28 = 784) must have a unique weight connecting it to every single neuron in the next layer (128).The Math: $784 \times 128 = 100,352$ weights. 

If you add the 128 bias terms, you have 100,480 trainable parameters in just the first layer.Scale: Even a small image like MNIST generates over 100k variables that the optimizer must tune. In higher-resolution images (e.g., 224x224), this number would explode into the millions, which is why we usually switch to CNNs for larger tasks.

2. High Model Capacity vs. Overfitting

Model capacity is like the "memory" of your network.The Risk: When capacity is high (too many neurons/layers), the model doesn't just learn the general rules of a digit (like "a circle is a zero"); it begins to memorize the noise or specific quirks of the training images.The Result: You see a very low Training Loss but a high Validation Loss. The model becomes a "lookup table" rather than a generalized processor.

3. Mitigating Overfitting: 

- Dropout: Randomly "turns off" neurons during each training step.
- L2 Regularization:	Adds a penalty to the loss function based on the size of the weights (squared).
- Early Stopping:	Monitored the validation loss and kills the training before the model starts memorizing noise.
