**Task 5**

**Comparing overfitting levels with Dropout**

No Dropout (5 epochs): Training loss: 0.0436 - val_loss: 0.0778

0.1 Dropout (5 epochs): Training loss: 0.0603 - val_loss: 0.0738

0.3 Dropout (5 epochs): Training loss: 0.0926 - val_loss: 0.0730

Comment:

No Dropout shows the most overfitting, 0.1 Dropout reduces it, and 0.3 Dropout removes the overfitting signal (validation loss is even lower than training loss) but may be leaning toward underfitting.

A simple overfitting indicator is the generalization gap = val_loss − training_loss

| Dropout | Training loss | Val loss | generalization gap (val−train) |
| ------- | ------------- | -------- | -------------------- |
| 0.0     | 0.0436        | 0.0778   | +0.0342              |
| 0.1     | 0.0603        | 0.0738   | +0.0135              |
| 0.3     | 0.0926        | 0.0730   | −0.0196              |

- Most overfitting: No Dropout, because it achieves the lowest training loss but the highest validation loss and the largest positive gap.

- Better regularization: 0.1 Dropout cuts the gap substantially while also improving validation loss vs no dropout.


**Why val_loss < train_loss**

In Keras/TensorFlow, the Dropout layer only applies when training=True and does nothing during inference (no units are dropped).​
During model.fit, training batches run with dropout active, while validation is evaluated in inference mode, so training loss can be higher than validation loss even when generalization is fine.​


**how Dropout encourages robust representations by preventing neuron co-adaptation**

In standard neural networks trained on limited data, complex patterns emerge where feature detectors rely on specific other neurons being present to correct their mistakes. For example, one neuron might learn to activate only when two other specific neurons are simultaneously active. This creates a brittle system: the learned features work well together on the training set but fail to generalize to test data because those exact neuron combinations won't recur reliably.
The core issue is that these co-adapted features are tuned to work well together on training data but not on the test data because the feature detectors have been tuned to work well together on the training data but not on the test data. Each weight vector that fits the training set perfectly makes different predictions on held-out data, and almost all perform worse on the test set.
