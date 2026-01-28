### **Task 7 — Optimizer Comparison Challenge**
Train four models using identical architecture but different optimizers:
- SGD (learning_rate=0.01)  
- SGD with Momentum  
- Adam  
- AdamW

**Key Optimizer Differences**
- SGD (Stochastic Gradient Descent): Updates weights using a fixed step. It can be slow and may get stuck in "plateaus" or local minima.

- SGD with Momentum: Adds a "velocity" component. Like a ball rolling down a hill, it gains speed in consistent directions, helping it push through noisy gradients and small local minima.

- Adam (Adaptive Moment Estimation): Calculates individual learning rates for every parameter. It is generally the "go-to" because it handles sparse gradients and noisy data exceptionally well.

- AdamW: Fixes a specific mathematical flaw in how Adam handles L2 regularization (weight decay). In standard Adam, the L2 penalty gets blurred by the adaptive learning rate; AdamW applies the decay directly to the weights, often leading to better generalization.

**For each optimizer**:
* Compare convergence speed and stability.

**Convergence Speed:**

- Adam/AdamW (Fastest): These reached $>91\%$ accuracy in the very first epoch. By epoch 2, they were already at ~95% validation accuracy.
- SGD with Momentum (Fast): Started strong at 90% and caught up to Adam quickly, eventually achieving the highest validation accuracy (97.7%).
- SGD (Slowest): Started at only 81% and required all 8 epochs just to reach the level Adam hit in epoch 2.

**Stability:**
- SGD & SGD Momentum: Showed very stable, steadily decreasing loss. SGD Momentum is particularly impressive here; it didn't suffer from the slight validation loss fluctuations seen in Adam.
- Adam/AdamW: Notice that Adam's validation loss actually increased slightly between Epoch 3 ($0.240$) and Epoch 4 ($0.250$). This "jitter" or instability is common with Adam as it aggressively adjusts learning rates for every parameter.

3. Discuss how each optimizer navigates the loss landscape differently.

The "loss landscape" is a 3D map of all possible weight values and their resulting error.

- SGD: Navigates like a person taking cautious, equal-sized steps. On flat surfaces (plateaus), it barely moves. In steep ravines, it might oscillate slowly.

- SGD with Momentum: Navigates like a heavy ball. It accumulates "velocity" from previous steps. This allows it to roll straight through small local pits and cross flat plateaus much faster than basic SGD.

- Adam: Navigates like a scout with a different speed for every coordinate. It looks at the history of gradients (moments). If a certain weight needs to change a lot, Adam gives it a larger individual learning rate; if a weight is already vibrating too much, Adam slows it down.


4. Explain why Adam often outperforms classical optimizers.

Adam and AdamW reached high performance much earlier than basic SGD. Here is why:

- Adaptive Learning Rates: Basic SGD uses one learning_rate for every single weight in your model. In a Dense layer of 128 neurons, some weights might need to change quickly while others need fine-tuning. Adam handles this automatically.

- Bias Correction: Adam includes a mathematical "warm-up" (bias correction) that prevents the initial steps from being too erratic, allowing it to start training aggressively from Epoch 1.

- Handling Sparse Data: If some pixels in your input images are usually zero (like the corners of the MNIST digits), Adam scales the updates for those specific features so they still contribute to learning, whereas SGD might ignore them.
