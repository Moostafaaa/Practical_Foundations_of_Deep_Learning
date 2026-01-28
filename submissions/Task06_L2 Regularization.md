## Task 6 — L2 Regularization Experiment

Add L2 regularization:

kernel_regularizer=keras.regularizers.l2(0.001)

Test values:
- 0.0001
- 0.001
- 0.01

Analyze:

 **How L2 reduces weight magnitude:**

L2 regularization adds a penalty term to the loss function that is proportional to the square of the weights.
- The Penalty: During backpropagation, the gradient of the L2 term $w^2$ is $2w$.
- Weight Decay: When the optimizer updates the weights, it doesn't just move in the direction that minimizes the classification error; it also subtracts a portion of the weight itself.
- The Result: Weights are constantly being "pulled" toward zero. Large weights are penalized more heavily than small ones, ensuring no single connection in your Dense(128) layer becomes excessively dominant.

 **Why smaller weights often improve generalization**

as reg_value increases, the gap between training accuracy and validation accuracy generally stabilizes. Smaller weights help because:

- Reduced Sensitivity: If a weight is very large, a tiny change in the input (like random noise in an image) causes a massive change in the output. Small weights make the model "stiff" against noise.

- Simpler Decision Boundaries: High weights allow the model to create highly complex, "wiggly" decision boundaries that fit every outlier in your training set. Smaller weights force the model to learn smoother, more general patterns that represent the dataset as a whole rather than specific training examples.

**How L2 changes the validation loss trend**

Val Loss (End):
- At L2 = 0.0001, val_loss = 0.1168	: Sharpest fit; lowest overall error.
- At L2 = 0.001, val_loss = 0.2403	: Loss is higher, but Val Loss < Training Loss (Very stable).
- At L2 = 0.01, val_loss = 0.6540	: Penalty is too high; model is struggling to learn (Underfitting).
