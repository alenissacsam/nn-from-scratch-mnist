# NN From Scratch for MNIST

A neural network built **from scratch with NumPy** for handwritten digit recognition on the MNIST-style Kaggle Digit Recognizer dataset.[file:19]

## Overview

This project implements a fully connected neural network without using high-level deep learning frameworks such as TensorFlow or PyTorch.[file:19] The notebook loads `train.csv` and `test.csv`, normalizes pixel values, performs forward and backward propagation manually, trains with gradient descent, evaluates on a held-out dev split, and generates a Kaggle submission file.[file:19]

## Model architecture

The network uses a 3-layer dense architecture with input size 784, two hidden layers of 256 and 128 neurons, and an output layer of 10 classes.[file:19] ReLU is used in the hidden layers, softmax is used in the output layer, He initialization is applied to the first two weight matrices, and Xavier-style scaling is used for the final layer.[file:19]

```text
784 -> 256 -> 128 -> 10
```

## Dataset

The notebook reads:

- `digit-recognizer/train.csv` for training data.[file:19]
- `digit-recognizer/test.csv` for test data.[file:19]

The training data has 42,000 rows and 785 columns, where the first column is the label and the remaining 784 columns are pixel values.[file:19]

## Training setup

The notebook shuffles the dataset, keeps the first 1,000 examples as a dev set, and uses the remaining data for training.[file:19] Pixel values are scaled by dividing by 255, and labels are converted to one-hot vectors during backpropagation.[file:19]

Training runs for 5,000 iterations with an initial learning rate of 1.0, then switches to 0.25 once training accuracy exceeds 0.95.[file:19] During training, the notebook prints accuracy every 10 iterations to track progress.[file:19]

## Results

The final reported dev accuracy is `0.9720`.[file:19] The notebook also creates a confusion matrix, displays wrongly predicted dev examples, and saves predictions for the 28,000-row test set into `digit-recognizer/submission.csv`.[file:19]

## Features

- Neural network implemented from scratch with NumPy only for the core learning logic.[file:19]
- Manual forward propagation, backpropagation, and parameter updates.[file:19]
- ReLU + softmax classification pipeline.[file:19]
- Dynamic learning-rate switch after crossing 95 percent accuracy.[file:19]
- Dev-set evaluation, confusion matrix, and wrong-prediction visualization.[file:19]
- Kaggle-ready submission generation.[file:19]

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
2. Download the Kaggle Digit Recognizer dataset and place `train.csv` and `test.csv` inside `digit-recognizer/`.[file:19]
3. Open `NN_for_MNIST.ipynb` in Jupyter Notebook or VS Code.[file:19]
4. Run the notebook cells in order to train the model and generate predictions.[file:19]

## Example output

After training, the notebook evaluates on the dev split, visualizes mistakes, and exports a CSV submission in this format:[file:19]

```csv
ImageId,Label
1,2
2,0
3,9
```

## Why this repo exists

This project is a learning-first implementation focused on understanding how neural networks work internally: initialization, activations, gradients, parameter updates, and multiclass prediction.[file:19] It is useful for building intuition before moving to deep learning frameworks.[file:19]

## Repo name ideas

If you keep the current name, `nn-from-scratch-mnist` is accurate and easy to understand. A slightly cleaner public-facing title is **NN From Scratch for MNIST**.
