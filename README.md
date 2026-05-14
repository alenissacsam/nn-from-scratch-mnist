# NN From Scratch for MNIST

A neural network built **from scratch with NumPy** for handwritten digit recognition on the MNIST-style Kaggle Digit Recognizer dataset. 

## Overview

This project implements a fully connected neural network without using high-level deep learning frameworks such as TensorFlow or PyTorch.  The notebook loads `train.csv` and `test.csv`, normalizes pixel values, performs forward and backward propagation manually, trains with gradient descent, evaluates on a held-out dev split, and generates a Kaggle submission file. 

## Model architecture

The network uses a 3-layer dense architecture with input size 784, two hidden layers of 256 and 128 neurons, and an output layer of 10 classes.  ReLU is used in the hidden layers, softmax is used in the output layer, He initialization is applied to the first two weight matrices, and Xavier-style scaling is used for the final layer. 

```text
784 -> 256 -> 128 -> 10
```

## Dataset

The notebook reads:

- `digit-recognizer/train.csv` for training data.
- `digit-recognizer/test.csv` for test data.

The training data has 42,000 rows and 785 columns, where the first column is the label and the remaining 784 columns are pixel values.

## Training setup

The notebook shuffles the dataset, keeps the first 1,000 examples as a dev set, and uses the remaining data for training. Pixel values are scaled by dividing by 255, and labels are converted to one-hot vectors during backpropagation.

Training runs for 5,000 iterations with an initial learning rate of 1.0, then switches to 0.25 once training accuracy exceeds 0.95.  During training, the notebook prints accuracy every 10 iterations to track progress.

## Results

The final reported dev accuracy is `0.9720`.  The notebook also creates a confusion matrix, displays wrongly predicted dev examples, and saves predictions for the 28,000-row test set into `digit-recognizer/submission.csv`.
## Features

- Neural network implemented from scratch with NumPy only for the core learning logic. 
- Manual forward propagation, backpropagation, and parameter updates. 
- ReLU + softmax classification pipeline. 
- Dynamic learning-rate switch after crossing 95 percent accuracy. 
- Dev-set evaluation, confusion matrix, and wrong-prediction visualization. 
- Kaggle-ready submission generation. 

## Project structure

```text
.
├── NN_for_MNIST.ipynb
├── digit-recognizer/
│   ├── train.csv
│   ├── test.csv
│   └── submission.csv
└── README.md
```

## Run locally

1. Clone the repository.
2. Download the Kaggle Digit Recognizer dataset and place `train.csv` and `test.csv` inside `digit-recognizer/`. 
3. Open `NN_for_MNIST.ipynb` in Jupyter Notebook or VS Code. 
4. Run the notebook cells in order to train the model and generate predictions. 

## Example output

After training, the notebook evaluates on the dev split, visualizes mistakes, and exports a CSV submission in this format: 

```csv
ImageId,Label
1,2
2,0
3,9
```

## Why this repo exists

This project is a learning-first implementation focused on understanding how neural networks work internally: initialization, activations, gradients, parameter updates, and multiclass prediction.  It is useful for building intuition before moving to deep learning frameworks. 

## Repo name ideas

If you keep the current name, `nn-from-scratch-mnist` is accurate and easy to understand. A slightly cleaner public-facing title is **NN From Scratch for MNIST**.
