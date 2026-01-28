**TASK 4**

*At which epoch did training stop?*

for 10 epochs, it stopped at 9.
for 20 epochs, it stopped at 12.

*Why does the validation loss control this decision?*

When the training loss continues to decrease but the validation loss begins to increase, it is the obvious sign that the model has started to overfit.
EarlyStopping monitors the validation loss and terminates training before the overfitting becomes extreme.


*What happens if you increase patience (e.g., to 5)?*

If patience were set to 5, the model would only stop if the validation loss failed to improve for five consecutive epochs.

Would a different optimizer (e.g., SGD) change the EarlyStopping pattern?
Yes, an optimizer like SGD (Stochastic Gradient Descent), would significantly change the loss curve and, consequently, the EarlyStopping pattern. When using an optimizer like SGD, you need to increase the patience value to allow the optimizer to smooth out its path to the minimum.

Explain how EarlyStopping acts as an indirect form of regularization.
Regularization is any technique used to reduce overfitting and improve a model's generalization ability. EarlyStopping achieves the same goal, making it an indirect form of regularization.
