Task 3 

Identify signs of overfitting.

Overfitting happens when the training loss decrease at the same time of validation loss increases. Vice versa in training accuracy and validation accuracy.

Explain how the optimizer (Adam) influenced the speed and stability of convergence.

Adam calculates a unique, adaptive learning rate for each individual parameter (weight and bias) in the network. This allows it to take larger steps for features that are under-adjusted and smaller steps for sensitive features. This adaptive nature generally results in faster convergence. Adam incorporates an element of momentum by tracking the exponentially decaying averages of both the gradients (like classic momentum) and the squared gradients (like RMSProp). This averaging provides greater stability in the descent towards the global minimum of the loss function.
