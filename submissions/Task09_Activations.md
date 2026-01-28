**Task 9**

1. Gradient Flow and the Vanishing Gradient Risk

Gradient flow refers to how well the "error signal" travels back through the layers during backpropagation.
Tanh and Softsign (High Risk): Both are saturating functions. As inputs get very large (positive or negative), the slope (derivative) of the curve becomes nearly flat (zero).Vanishing Gradient: In deep networks, multiplying many small derivatives (near 0) together makes the gradient vanish, meaning the early layers stop learning. Tanh is more prone to this because it saturates faster than Softsign.
GELU and ReLU (Low Risk): These do not saturate for positive values. The gradient remains $1$ (for ReLU) or near $1$ (for GELU) as $x$ increases, allowing the signal to flow freely across many layers.

2. Why GELU performs well in Transformers

GELU (Gaussian Error Linear Unit) is essentially a "smarter" ReLU. While ReLU strictly cuts off all negative values at zero, GELU weights inputs by their magnitude based on a probability distribution (the Gaussian CDF).
Smoothness: GELU is differentiable at all points, unlike ReLU which has a sharp "kink" at zero. This smoothness helps optimizers like Adam find better minima in complex Transformer architectures.
Stochasticity: It acts as a bridge between a regular activation and stochastic dropout. By allowing a small amount of negative information to pass through, it helps preserve more complex patterns in large datasets.

3. Why ReLU remains the "Standard" for MLP and CNNs

Despite newer functions like GELU, ReLU (f(x) = max(0, x)) is still the go-to for most standard models for several practical reasons:Computational Efficiency: ReLU is incredibly "cheap" to calculate—it's just a simple threshold at zero. Tanh, Softsign, and GELU involve exponents or divisions, which are more taxing during millions of training iterations.Sparsity: ReLU produces "true zeros." This makes the network sparse (not every neuron is active), which can improve generalization and act as a natural form of regularization.Convergence Speed: In most standard CNNs or MLPs, ReLU converges much faster than saturating functions (like Tanh) because it doesn't suffer from the "flat slope" problem on the positive side.
