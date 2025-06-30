# Facial_Recognition

This project implements a Siamese Neural Network using a convolutional architecture for one-shot facial recognition. Inspired by the paper "Siamese Neural Networks for One-shot Image Recognition", the goal is to determine whether two facial images belong to the same person.
For a detailed explanation of the model architecture, training process, experiments, and results, please refer to the report file.


### Network Architecture

| Layer                             | Input Dimension | Filter Size | Output Dimension |
|----------------------------------|------------------|-------------|------------------|
| Conv1 + ReLU + BatchNorm         | 105×105×1        | 10×10×64    | 96×96×64         |
| Max Pooling 1                    | 96×96×64         | 2×2×64      | 48×48×64         |
| Conv2 + ReLU + BatchNorm         | 48×48×64         | 7×7×128     | 42×42×128        |
| Max Pooling 2                    | 42×42×128        | 2×2×64      | 21×21×128        |
| Conv3 + ReLU + BatchNorm         | 21×21×128        | 4×4×128     | 18×18×128        |
| Max Pooling 3                    | 18×18×128        | 2×2×64      | 9×9×128          |
| Conv4 + ReLU + BatchNorm         | 9×9×128          | 4×4×256     | 6×6×256          |
| Flatten                          | 6×6×256          | —           | 9216             |
| Fully Connected + Sigmoid + BN  | 9216             | —           | 4096             |

### Hyperparameter Tuning
We performed a grid search to optimize the Siamese Network's performance by evaluating multiple combinations of key hyperparameters:
| Hyperparameter     | Values Explored                  | Best Value |    
|--------------------|----------------------------------|------------|
| **Batch Size**     | 8, 16                            | 16         | 
| **Learning Rate**  | 0.001, 0.0001, 0.00001           | 0.0001     | 
| **Optimizer**      | Adam, SGD with Momentum          | Adam       | 
| **Loss Function**  | BCELoss, MSELoss                 | BCELoss    | 
| **Epochs**         | Up to 30 (with early stopping)   | -     | 
| **BatchNorm**      | Enabled, Disabled                | Enabled    | 
| **Dropout**        | Enabled, Disabled                | Disabled   | 


