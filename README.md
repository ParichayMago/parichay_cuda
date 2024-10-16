<div>
<h1>Cuda for Noobs</h1>
</div>

This project is for my [hacktober event](https://github.com/GDG-GTBIT/Hacktoberfest-2024-AIML)
for this problem i will be building NN to solve house pricing problem using nn from scratch. 

### Collecting data:
For this step i will make use of pandas liberary
-I will use [kaggle dataset](https://www.kaggle.com/code/stpeteishii/titanic-fastai) by fastAi.
-Using pandas liberary i will filter out the data, handle missing values, and mormalise the standard values..
-then i will split the data into training, validation and testing dataset. (The given kaggle repo already have a testing dataset)

## Designing the Neural Network Architecture:
-No externals machine learning liberary will be used from this point. All the code will be written from scratch.
-All the backend kernels will be written by hand using cuda and trition.
-Which will include matrix_mul, matrix_transpose, Parallel prefix sum of arr.

### Steps to Design the Neural Network Architecture: 

** INPUT LAYER: Define the input layer(customisable depending upon the feature of the dataset)
** HIDDEN LAYER: Defineing the numebr of hidden layers(generation random weights for the loss funciton to work)
** OUTPUT LAYER: Defining the output layer based upon the possible outcomes.

((((Input) * weights) +bias) Activation function)

### Applying Activation function: 
Actvation functions is to determine the firing of a neuron depending upon the prev input
Using Sigmoid activatin function for binary classification. 

writing cuda kernel for activation function: 
Sigmoid: S(x) = {1}//{1+e^{-x}}

### Loss function
important to define it in a way to calculate total loss of layer and save the gradiants for the backpropagtion
using mse: (y(real)^2 -y(predi)^).root 

### Forward propagation##
Y(preds) = X(inp) * Weights + bias

### Backpropagtion##
--Calculating the gradiants of the loss function with respect to the weights
--((((Input) * weights) +bias) Activation function) Applying chain rule on this
to update weights and biases to minimise the lose.

### Training Loop
Defining the number epochs to run and batch and mini-batch



## Cuda Kernels to writ for the function to work:
-Feed Forwward kerenel
Applying matrix transpose, matrix multiplication of weights and inputs and adding the biases parellely. 
Applying the activation function on the outputs to normalise the value of neuron (seprate kernel needed)

-Backpropagtion kernel
Applying to compute the loss with respect to weights and biases using chain rule.

-Loss function kerenel:
This cuda kernel will apply the mse to compute the loss wrt to outputs.

-Actication function kernel(Sigmoid);
To parellely apply in the activation function on the neurons. 
