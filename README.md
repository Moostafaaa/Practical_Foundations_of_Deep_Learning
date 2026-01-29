# Foundations of Deep Learning: MNIST Classification

This repository contains a comprehensive guide to building, training, and optimizing neural networks using TensorFlow/Keras. The project focuses on the MNIST dataset, moving from basic architecture to advanced model analysis.

---

## 🚀 Project Overview

The goal of this project is to demonstrate a standard Deep Learning workflow. It covers everything from raw data preprocessing to the nuances of gradient flow and regularization techniques, providing a hands-on look at how model capacity affects generalization.

---

## 📖 Notebook Sections

1. **Section 1: Building & Training** Initial setup using a `Flatten` input, a `Dense` hidden layer with **ReLU**, and a **Softmax** output. Includes compilation with the Adam optimizer and initial training.
2. **Section 2: Optimization & Activation Functions** A comparative study of different activation functions (**Tanh, Softsign, GELU**) and how they impact gradient flow and convergence speed.
3. **Section 3: Model Capacity & Regularization** Inspection of weight matrices and exploration of techniques like **Dropout, L2 Regularization, and Early Stopping** to mitigate overfitting.

---

## 🛠️ How to Run

1. **Clone the repository:**
```bash
git clone https://github.com/Moostafaaa/Practical_Foundations_of_Deep_Learning.git

```


2. **Install dependencies:**
```bash
pip install tensorflow matplotlib numpy

```


3. **Launch the notebook:**
Open `Foundations_of_Deep_Learning.ipynb` in Jupyter Notebook or Google Colab and run all cells sequentially.

---

## 📊 Sample Results

### Training Dynamics

The notebook generates loss curves to visualize how different activations (like GELU vs. Tanh) minimize error over time.

### Activation Comparison

Comparison of the non-linearities used in the hidden layers:

| Activation | Convergence Speed | Overfitting Risk |
| --- | --- | --- |
| **ReLU** | Fast | Medium |
| **Tanh** | Moderate | High (Vanishing Gradient) |
| **GELU** | Fast | Low (Smooth Gradient) |

### Weight Inspection

The model extracts weight shapes (e.g., `(784, 128)`) to illustrate how model capacity scales with input resolution.

