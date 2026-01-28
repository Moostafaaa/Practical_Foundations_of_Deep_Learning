**Task 1**

How the forward pass transforms inputs through layers?

The forward pass is the process where an input single image goes through all the layers of the network until it produces an output prediction,the input layer takes single 28x28 grayscale image and then it is flattened into a one-dimensional vector of 28x28=784 pixels values. After this, input goes to the hidden layer of 128 neurons and each neuron does a transformation by Z = W dot X + b and those transformations leads to learn to detect simple edges or corners. The output of the first layer becomes the input for the next layer(hidden), and the process repeats. Each subsequent layer builds the features extracted by the previous layer, developing increasing complex features forming loops, lines, and curves until the output layer which results in logits with probabilities for each value from 0 to 9.

**The role of activation functions (ReLU, Softmax)**

Activation functions are critical because they introduce non-linearity into the NN models, allowing the network to learn complex relationships and features.

**Rectified Linear Unit (ReLU)** is typically used in hidden layer neurons and it defines as Z=max(0,X), it sets all negative inputs to zero. This makes the resulting output sparse and computationally efficient, helping the model to focus on the positive, important features.

**Softmax** is used in the final output layer. It takes the raw scores (logits) from the final layer and turn them into a probability distribution over the N classes (where N=10 for digits 0-9). The output is a vector of 10 values, where each value is between 0 and 1, and all 10 values sum to 1.

**How the optimizer (Adam) may have shaped weight updates during training?**

The optimizer is the algorithm used during the back propagation (training) to adjust the model's weights and biases (the W and B parameters) to minimize the prediction error (loss). Adam (short for Adaptive Moment Estimation) doesn't use a single, fixed learning rate. Instead, it calculates a learning rate for each weight in the model.
Parameters (weights) that need to be changed drastically are adjusted with a larger step, while other parameters are adjusted with a smaller step. This leads to faster convergence and better performance than non-adaptive optimizers.
Adam uses a concept similar to Momentum, which tracks the past weight updates, this helps the optimizer gain speed in the direction of the minimum loss and overshoot local minima in the loss curve.
