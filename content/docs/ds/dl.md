---
type: "docs"
title: Deep Learning
draft: true
url: "/docs/ds/deep-learning/"
---

# Deep Learning

![Neural Network](https://www.ibm.com/blog/wp-content/uploads/2023/07/deep-neural-network.png)

[Link to machine Learning Notes](./ml-notes.md)

---

## Neural Networks

- Neural Networks take in **data as input**, **train themselves** to understand the patterns in the data and **output the useful predictions**.
- The fundamental component in a neural network is Neuron.

### Learning Process

- Two Types:
  - Forward Propagation
  - Backward Propagation

### Forward Propagation

**Forward propagation** is a technique that moves input data through a network in a forward direction to generate an output. Each hidden layer accepts the input data, processes it as per the activation function and passes to the successive layer.

**Weight** - Indicates how important a Neuron is.
**Bias** - Allows for the shifting of **activation function** to the right or left.

### Backward Propagation

Similar to **Forward Propagation**, except that information is passed from output layer to the previous hidden layer.
Back Propagation is one reason why Neural Networks are good at learning.
In **Back Propagation**, **Loss Functions** help qunatify the deviation from the expected output.

#### Loss Functions

Quantify the deviation of the **predicted** output by the neural network to the **expected** output.

Depending on the case, there are various loss functions

1. **Regression** Squared Error, Huber Loss
2. **Binary Classification** Hinge Loss, Binary Cross-Entropy
3. **Multi-Class Classification** Multi-Class Class-Entropy, Kullback Divergence

---

## Learning Algorithms

1. Initialize parameters with random values
2. Feed input data to network
3. Compare predicted value with expected value & calculate loss
4. Perform **Backpropagation** to propagate this loss back through the network
5. Update parameters based on the loss
6. Iterate previous steps till loss is minimized

---

## Activation Functions

- Introduces Non-linearity in the network.
- Decide whether a neuron can contribute to the next layer.

A. **Step Function**

```
    if value  > 0  ==> Activate
    else  ==> Do not activate
        0 is the "threshold"
```

- Fails when more than one neuron is activated.

B. **Linear Function**

$$
y = mx + c
$$

C. **Sigmoid Function**

![reference link](https://machinelearningmastery.com/wp-content/uploads/2021/08/sigmoid.png)

- Non-linear
- Analog Outputs
- Vanishing Gradient Problem. Gradient becomes less at extremes.

D. **Tanh Function**

![Tanh Function](https://in.mathworks.com/help/examples/matlab/win64/GraphHyperbolicTangentFunctionExample_01.png)

$$
tanh(x) = 2 * sigmoid(2x) - 1
$$

- Non-linear
- Derivative steeper than Sigmoid
- Has the vanishing geadient problem like Sigmoid

E. RELU Function

- **RELU Function** : Rectified Linear Unit Function

![RELU & GELU](https://upload.wikimedia.org/wikipedia/commons/thumb/4/42/ReLU_and_GELU.svg/1280px-ReLU_and_GELU.svg.png)

$$
R(z) = max(0, z)
$$

A piecewise linear function that will output the input directly if it is positive, otherwise, it will output zero.

It has become the default activation function for many types of neural networks because a model that uses it is easier to train and often achieves better performance.

- Range : 0 to ∞
- Non-linear
- Sparse Activation
- Gradient is 0 for -ve values of x. During back propagation, weights will not be adjuusted to GD and the Neurons wil stop responding to errors (**Dying RELU Problem**)
- This can be overcome by adding slope to the -ve part of the plot. Usually like `y = 0.001x` (_Leaky RELU_) or `y = ax` (_parametric RELU_). thus gradient will not be zero.

**When to use what Activation Function?**

- Choose the Activation Function that approximate the function faster, leading to faster training.
- **Binary Classification** - Sigmoid
- If unsure, RELU or Modified RELU

**Why Non-linear Functions?**

- Polynomial Functions of multiple degrees (> 1) can fit data better then monomial functions.

---

## Epochs, Batches, Batch Sizes & Iterations

Above terms are required only when the dataset is large.

These break-down the dataset into smaller chunks and feed those to the neural network one-by-one

**Epochs**

When the entire dataset is passed through the neural network once, it is said to have completed one _Epoch_

Multiple epochs helps generalizing the model better. There is no right number of epochs :skull:

**Batches & Batch Size**

Dataset is divided into smaller batches and fed to **neural network**

Batch Size is the total No. of training examples in a **Batch**

**Iterations**

Number of batches needed to complete one epoch

> No. of batches = No. of iterations per epoch

---

## Optimizers

During training, parameters are adjusted to minimize the loss functions and make the model as optimized as possible.

Optimizers update the network based on the output of the loss function. This adjusts the weights of the layer

### Gradient Descent

> Iterative algorithm that starts off at a random point on the loss function and travels down its slope in steps until it reaches the lowest point (minimum) of the function

- **Backpropagation** is essentially Gradient Descent implemented on a network.
- Gradient Descent is a popular Optimizer
- Robust, fast & flexible

**Algorithm**

1. Calculate what a small change in each individual weight would do to the loss function
2. Adjust each parameter based on its gradient (i.e. take a small step in the determined direction)
3. Repeat the steps 1 & 2 until the loss function is as low as possible

To avoid getting stuck in a local minima, _learning rate_ is used.  
**Learning Rate**

- Usually, _learning rate_ is a small value like 0.001 that is multiplied to scale the gradient.
- Ensures that any changes made to weights are small.
- Large _learning rate_ overshoots the global minimum while a too small learning rate will take forever to converge to the global minimum.

### Stochastic Gradient Descent

- Similar to GD, except that it uses a subset of training examples rather than the entire lot.
- **Stochastic Gradient Descent** uses batches on each pass.
- Uses momentum to accumulate gradients.
- Less intensive computation.

### ADAGRAD

- Adapts Learning Rates to individual features
- Some weights will have different learning rates
- Ideal for sparse datasets with many input examples missing
- Learning Rate tends to get small with time.

### RMSprop

- Specialized version of Adagrad
- Accumulates Gradients in a fixed window
- Similar to Adaprop

### Adam

- Stands for **Adaptive Moment Estimation**
- Uses the concept of Momentum
- Pretty widespread today

---

## Regularization

Overfitting can be tackled with:

1. **Dropout**
2. **Dataset Augmentation**
3. **Early Stopping**

### Dropout

![Dropout Figure](https://www.researchgate.net/publication/333159107/figure/fig7/AS:759365778825217@1558058318369/Schematic-diagram-of-Dropout-a-a-standard-neural-network-b-the-neural-network-using.png)

- Random nodes are selected and dropped alongwith their incoming and outgoing in every iteration. Thus each iteration has different set of outputs.
- Captures randomness & memorizes less training data
- Builds robust predictive model

### Dataset Augmentation

- Create _fake data_ to increase training set size.
- Apply transformations on the existing dataset to get synthesize more data
- Very good for classification models, especially **Object Recognition**
- Not recommended in case of classifying between like **6 vs 9** or **b vs d**

### Early Stopping

- Training error decreases steadily
- However, validation error increases after a certain point

---

## Neural Network Architectures

1. Fully Connected Feed Forward Neural Networks
2. Recurrent Neural Networks
3. Convolutional Neural Networks

### Fully Connected Feed Forward Neural Networks

Every Neuron is connected to every neuron in subsequent layer with no backward connections.

![Fully Connected Feed Forward Neural Network](https://upload.wikimedia.org/wikipedia/en/5/54/Feed_forward_neural_net.gif)

- Unidirectional
- More neurons translates to more computation, requiring large computational resources

### Recurrent Neural Networks

![Recurrent NN](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/Recurrent_neural_network_unfold.svg/1920px-Recurrent_neural_network_unfold.svg.png)

![Recurrent NN Types](https://www.researchgate.net/publication/317192370/figure/fig3/AS:513608797097985@1499465287220/The-four-types-of-recurrent-neural-network-architectures-a-univariate-many-to-one.png)

Vanilla NNs cannot handle sequential data

- Uses a feedback loop in the hidden layers

LSTM - Long Short Term Memory
GRNN - Gated Recurent Neural Network

These two are capable of learning long-term dependencies using _gates_

### Convolutional Neural Networks

- Inspired by the organization of neurons in the visual cortex of human brain
- Good for processing data like **images, audio and video**

Hidden Layers in Convolutional Neural Networks consist of the following :

- Convolutional Layers
- Pooling Layers
- Fully-Connected Layers
- Normalization Layers

**Convolution** is a process which allows us to extract say, visual features in **chunks**

**Pooling** reduces the neurons necessary in subsequent layers  
Two types :

**A. Max Pooling** Picks the maximum value from the region  
![Max Pooling](https://production-media.paperswithcode.com/methods/MaxpoolSample2.png)

**B. Min Pooling** Picks the minimum value from the region
![Min Pooling](https://www.researchgate.net/profile/Dr-Rajeev-Tiwari/publication/358362955/figure/fig25/AS:1128783046295570@1646134258649/Min-Pooling-Operations.png)

**CNN Architecture Algorithm**

1. Convolve the image : Use a convolutional layer with multiple filters to create a 2D feature matrix as output for each filter
2. Pool the result to produce a down-sample filter matrix for each layer
3. Repeat above steps multiple times using previous features as input
4. Add few fully connected hidden layers to help classify the image
5. Produce a classification prediction in output layer

**Applications of Convolutional Neural Networks**

1. Computer Vision
2. Image Recognition
3. Image Processing
4. Image Segmentation
5. Video Analysis

---

## Creating a Deep Learning Model

5 steps common in every DL model

### Gathering data

- Picking the right data is key. Bad dat gives bad model
- Make assumption about the data you need
- As a rule of thumb, **Amount of Data Needed = 10 x No. of Model Parameters**
- For regression, 10 examples per predictor variable
- For Image Classification, 1000 images per class
- Quality matters.
  - How common are labelling errors?
  - Are the features noisy?

### Preprocessing Data

#### Data Splitting

- Splitting data into subsets
  - Train on training sets
  - Evaluate on validation data
  - Test it on Test Data
- How data is split dependss on :
  - Number of samples in the dataset
  - Model being trained

```
Models with few hyperparameters --> Small Validation Set
Model with many hyperparameters  --> Large Validation Set
No Hyperparameters --> No validation set required
```

- Train-Validation-Split ratio is specific to each case.
- **Cross-Validation** Training set is split into different ratios of Training & Validation sets
- In **Time-Series** datasets, split must be done by time. Time-based splits work well for large datasets.

```
If in a time-series dataset, the total time is 40 days, then the training set will be on Day 1 to day 39 while testing/validation will be done on Day 40
```

#### Dealing with missing data

- Missing data is represented as **NULL** or **NaN**.
- Eliminate features with missing values.
- Input the missing values.

#### Sampling

- Uses a small sample of the dataset
- **Downsampling** is done to counter majority bias

$$
Example Weight = Original Weight \ * \  DownSampling Factor
$$

DownSampling Advantages

- Faster Convergence
- Reduces Diskspace
- Dataset is in similar ratio

#### Feature Scaling

- Crucial step in DL
- Techniques:

  - **Normalization** The goal of normalization is to change the values of numeric columns in the dataset to use a common scale, without distorting differences in the ranges of values or losing information. The data values are ranged between 0 and 1. `MinMaxScaler()` Function is typically used to achieve this.
  - **Standardization** Change the values to Standard Normal Distribution while being smilar to Normalization.

  | Standardization                                                | Normalization                                                                      |
  | -------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
  | This method scales the model using minimum and maximum values. | This method scales the model using the mean and standard deviation.                |
  | When features are on various scales, it is functional.         | When a variable's mean and standard deviation are both set to 0, it is beneficial. |
  | Values on the scale fall between [0, 1] and [-1, 1]            | Values on a scale are not constrained to a particular range                        |
  | Additionally known as scaling normalization                    | This process is called Z-score normalization                                       |
  | When the feature distribution is unclear, it is helpful        | When the feature distribution is consistent, it is helpful                         |

### Training the Model

1. Feed Data
1. Forward Propagation
1. Loss Function
1. Backpropagation

### Evaluation

Test model on the **validation** set  
Meant to be representative of the model in the real world

### Optimization of Model

#### Tuning Hyperparameters

1. Increase the number of epochs
1. Adjust Learning Rate

```
Initial conditions play important role in determing the model outcome
```

#### Addresing Model Overfitting

1. Getting more data
1. Reducing model size :point_right: Remove unncessary parameters to improve training. By reducing the capacity of the network, relevant parameters can be more weighed to learn
1. Regularization

#### Data Augmentation

Good way of increasing dataset artificially
Flipping axes, blurring and zooming (in a image classification problem)

#### Droput

Ignoring randomly chosen neurons during training. This reduces co-dependency of neurons
