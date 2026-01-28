## Task 8 — Batch Size & Gradient Noise Experiment

Train the model with batch sizes:
8 , 32 , 128

Discuss:

**Why smaller batches introduce gradient noise.**

Batch 8: the loss curve "jitter" or bounce up and down more. This is because the model is making drastic weight updates based on very small groups of images (high noise).

Batch 128: The curve looks much smoother. The gradients are more stable because they are averaged over many images.

**When this noise is beneficial (escaping local minima).**
The loss landscape of a neural network isn't a smooth bowl; it's full of jagged peaks and shallow pits (local minima).

Large Batches: These are very precise. They lead the model straight into the nearest pit. If that pit is a "local minimum" (a sub-optimal solution), the model gets stuck there.

Small Batches (Noise): Because the steps are noisy, the model "jitters." This jittering acts like shaking a tray with a marble on it. The marble might fall into a small, shallow hole, but the shaking (noise) pops it back out, allowing it to continue searching until it finds a deeper, broader, and more stable "Global Minimum."

How Noise Helps: Noise makes it nearly impossible for a model to stay in a "Sharp" minimum. The fluctuations are too violent for the model to settle in a narrow hole. It can only settle down in a wide, flat area where the noise doesn't push it out easily.


**Why larger batches may converge faster but generalize worse.**

Larger batches converge faster because they allow the hardware to process more data in parallel and provide a stable, accurate gradient that leads the model directly toward a minimum in fewer steps. However, they often generalize worse because this lack of "gradient noise" prevents the model from escaping sharp, narrow local minima that are highly specific to the training data. Without the stochastic "jitter" found in smaller batches, the model fails to explore the loss landscape effectively and misses the broader, flatter minima that typically lead to better performance on unseen data.

**How batch size affects the smoothness of loss curves.**

Batch size determines the smoothness of the loss curve by controlling the amount of "gradient noise" during training. Small batches calculate updates from only a few samples, causing outliers to pull the weights in different directions and resulting in a jagged curve. Conversely, large batches average the gradient over many samples, canceling out individual noise to provide a stable, consistent direction that produces a clean, smooth decline. While large batches look more stable, the "noise" in the jagged curves of small batches often acts as a beneficial force, helping the model avoid sub-optimal solutions.
