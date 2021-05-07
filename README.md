# A simple network in Pytorch
====

In this notebook is a very simple network with 4 layers.

1. Input Layer - 2 neurons
2. Hidden Layer 1 - 5 neurons
3. Hidden Layer 2 - 4 neurons
4. Output Layer - 1 neuron

### What are neurons?
===

**Neurons** are the storage units that act as placeholders for data and results of computation. When many of them are grouped together, it is called a layer. And when many layers are stacked together, they form the neural network

How does the computation happen?
===

Computation of data is done by the multiplications of parameters called weights to the flowing data to amplify/suppress the incoming features. This is commonly known as the feed forward operation when data is processed from the input to the output layer for batches of data. The **weights** are simply floating point numbers that follow a strategy for **initialization** which depends on the activation function. 

For tanh which is used in the notebook and generally sigmoid, the best initialization is observed to be the _Xavier Initialization_ which is intiialization by using a uniform distribution. 

For the ReLU activation however, it is observed that Xavier initialization has challenges since the overall variance of a uniform distribution is less in value in comparison to variance of a Gaussian distribution. Variance being higher (closer to 1) allows more robustness towards gradient issues such as vanishing and exploding. Hence here, the _He Initialization_ is used which draws data from a Gaussian/Normal distribution. In the above notebook, we have used the **He initialization**

Do we know if the computation was correct or not?
===

After the feed forward, a **loss** is computed which is the error calculated using a pre-defined metric which compares the difference between the output of the network and ground truth. 

OKay, the computation wasn't the best. How can we make it better?
===
The loss can be used to calculate gradients. The gradients show the nature of impact of each weight on the loss which are essentially partial derivatives of the loss wrt a weight. Using loss and the **chain rule**, gradients can be backpropagated to all the weights. Chain rule states that the gradient of chained functions are simply the product of the gradients of the individual functions. Weights are now updated to  lower the loss implying a better output. 

The update
===

The weight update modifies each weight by subtracting (learning_rate * gradient of Loss wrt weight) and the new sets of weights are now used for the next epoch.

This is one epoch!
===

A cycle of feed-worward followed by backprop is one epoch. Many epochs are run to allow for the network to learn with small weight increments. The rate at which the network learns .i.e. how small/large of an update to make to each weight, is the **learning rate**. This is a parameter to the optimizer that decides the direction and amplitude of the step to take.


This process of learning is the mechanism of training a Neural Network.