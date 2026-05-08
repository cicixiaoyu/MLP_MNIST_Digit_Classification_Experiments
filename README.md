# MLP_MNIST_Digit_Classification_Experiments

This project was developed as part of the Programming for FinTech course at the Shanghai Advanced Institute of Finance (SJTU).

Tools & libraries:
- Python
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Assignment instructions

- Use more neurons in hidden layer, or add one more hidden layer, what is the testing accuracy?
- Use more iterations, what is the training precision, what is the test precision?
- Play with other selections such as learning rate, regularization parameter, activation function, etc. what do you observe?

## Requirements
```bash
pip install numpy matplotlib scikit-learn jupyter
```

Run:
```bash
jupyter notebook mnist_mlp.ipynb
```

## Report 

We aim to demonstrate how different neural network configurations and hyperparameter settings affect
model performance on the MNIST dataset. Through testing various numbers of neurons and hidden
layers and different training parameters, we will identify optimal configurations that balance learning
capacity with generalization ability, while analyzing the trade-offs between training accuracy and testing
performance across different experimental conditions.

### I/ Architectural modifications

**Increasing neurons in hidden layers**

Expanding the hidden layers from 512 to 2048 neurons improved testing accuracy from 98.32% to
98.47%. This enhancement in generalization performance demonstrates that increased model capacity
better captures the underlying patterns in the MNIST dataset without memorizing noise. The higher
testing accuracy confirms that the additional neurons enable the network to learn more robust features
that translate effectively to unseen data, though the modest gain suggests the original architecture was
already well-suited to this classification task.

**Adding additional hidden layers**

Adding an extra hidden layer with 512 neurons reduced testing accuracy from 98.32% to 98.23%. This
decline in generalization performance indicates that increased depth introduced optimization difficulties
rather than meaningful feature extraction for this dataset. The lower testing accuracy suggests that the
additional layer created unnecessary complexity without providing substantial benefits for recognizing
handwritten digits, confirming that deeper networks don't automatically improve performance on the
MNIST classification task.

### II/ Training duration analysis

Extending the training epochs from 10 to 25 allowed the training accuracy to reach 100%, indicating
complete memorization of the training dataset. However, the testing accuracy improved to 98.74%,
representing the highest generalization performance observed across all experiments. This outcome
demonstrates that additional training iterations allow the model to better learn relevant features while
maintaining good generalization, though the perfect training score suggests careful monitoring is needed
to prevent overfitting with further iterations.

### III/ Hyperparameter optimization

**Learning rate variations**

The learning rate experiments showed that a high learning rate of 0.01 resulted in suboptimal
performance with 98.29% training accuracy and 96.94% testing accuracy, indicating unstable
convergence. The default learning rate of 0.001 achieved excellent results with 99.77% training accuracy
and 98.05% testing accuracy. A lower learning rate of 0.0001 produced 98.76% training accuracy and
97.68% testing accuracy, showing that excessively conservative learning rates can slow convergence
and limit final performance.

**Regularization effects**

Implementing L1-L2 regularization had the most dramatic impact on model behavior. Both training and
testing accuracies dropped significantly to 93.24% and 93.44% respectively. This substantial reduction
indicates that the regularization strength was likely too aggressive for this dataset, overly constraining
the model's capacity to learn relevant patterns. The nearly identical training and testing scores suggest
the model was underfitting, emphasizing the need for careful regularization tuning.

**Activation function comparison**

The Tanh activation achieved training accuracy of 99.96% with testing accuracy of 98.16%,
demonstrating excellent learning capability with good generalization. In contrast, Sigmoid activation
yielded lower performance with 98.47% training accuracy and 97.56% testing accuracy. The original
ReLU activation provided a balanced performance, making it a reliable default choice.

### IV/ Conclusion

The experiments reveal several key insights for MNIST classification. Additional neurons provide
consistent benefits, while added layers may introduce unnecessary complexity. Extended training
significantly improves generalization despite perfect training accuracy. Learning rate requires careful
tuning within an optimal range, and aggressive regularization can severely impact performance. Among
activation functions, Tanh demonstrates superior learning capability while maintaining good
generalization.
