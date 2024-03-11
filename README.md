# Deep_Learning_and_TensorFlow
<br>
This project covers the topic of Deep Learning and to achieve models in Deep Learning using TensorFlow library in python. For some parts I am using the numpy library of Python. This project is done by defining class, an instance of object oriented programming. The contents of this project are dicussed briefly in this Readme file.
<hr>

<h2>1. Zero Hidden Layer Neural Network Architecture:</h2>

In case of Zero Hidden Layer Neural Network, there are 1 input layer and 1 output layer. The input layer contains the feature set. For ease of discussion, here I am considering only one sample. The output layer itself contains two sub layers. They are Dense layer and SoftMax Activation layer. <br>
<ul>
  <li><b>Dense Layer</b> owns a set of weights that are specific to features and output class labels. The input of Dense layer are the features. The output of Dense layer is the Raw Score, denoted by <b>Z</b>. Suppose, <b>W</b> is the weights matrix and <b>X</b> is the feature set. Then the raw score Z is given as Z = <b>WX</b> + b , where b is the bias term.</li>
  <li><b>SoftMax Activation Layer</b> is the second sub-layer of the output layer. The input of this layer are the raw scores vector (<b>Z</b>) that comes from previous layer; the output of the layer is the SoftMax activated raw scores, denoted as <b>a</b> , where <b>a<b> = SoftMax(<b>Z</b>). The SoftMax function is achieved by raising the entries of <b>Z</b> to the power of e(exponential power) to eliminate negative values and then normalize it to decrese the magnitude of the values.</li>
</ul> <br>
<p align="center">
  <img width="500" height="400" src="https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/ZeroHLNN.png">
</p>
<p>
  Suppose we have 5 output features x<sub>1</sub>, x<sub>2</sub>, x<sub>3</sub>, x<sub>4</sub>, x<sub>5</sub> respectively and consider the bias term b in the input layer. Then a zero hidden layer neural network 
  architecture can be given as
  <ul>
    <li>The Weights Matrix <b>W</b> that is owned by the Dense Layer is of shape (3&times6)</li>
    <li>The Raw Scores Vector <b>Z</b> is of shape (3&times1), elements of which are z<sub>1</sub>, z<sub>2</sub>, z<sub>3</sub> respectively</li>
    <li>The Activated Raw Scores Vector <b>a</b> is of shape (3&times1), elements of which are a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub> respectively</li>
    <li>Finally, Loss L is calculated, which is a scaler quantity</li>
  </ul>
</p> 
<hr>
    
<h2>2. Zero Hidden Layer Neural Network Categorical Cross Entropy Loss (CCE):</h2>
    
In case of hidden layer neural networks, we have a output class labels that are denoted by the vector <b>y</b>. Suppose, in this case, I have three output class labels Mild, Medium and High. Also suppose that, they all are denited by numbers such as Mild as 1, Medium as 2 and High as 3. Now, for 5 samples, I have the actual class label <b>y</b> = [1,2,3,2,1] (Say). Now, after the activation of the raw scores, I get the predicted probabilities vector, denoted as <b>&#375</b>. The Categorical Croos Entropy Loss (CCE) is given by
<p align = "center">
  <img width = "900" height = "200" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/CCELosszeroHLNN.png"> <br>
  Here, the term [a]<sub>y</sub> is the predicted probability when the correct output class label is y
</p>
<hr>

<h2>3. Backward Propagation and Gradient Calculation In Zero Hidden Layer Neural Network:</h2>

In case of a neural network, the weights matrix and bias are to be iteratively updated. In order to achieve optimal weights matrix <b>W</b>,in general a method called as <u>Gradient Descent</u> is used. In this method, the gradient of the Loss L is calculated w.r.t the weights matrix <b>W</b>. In general, the weights are updated in the opposite direction of the gradient calculated. The formula for gradient descent is given as
<p align = "center">
  <img width = "450" height = "150" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/graddes.png" >
</p>
So, inorder to apply the gradient descent method, the derivative of Loss w.r.t the weight matrix <b>W</b> muust be calculated. Now this whole process of gradient calculation is achioeved by using a Mathematical concept called Chain Rule that is used to calculate derivative of complex functions. This is given as
<p align = "center">
  <img width = "500" height = "200" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/zeroHLNNgradCalculation.png">
</p>
<ol>
  <li>
    <b>Gradient of Loss Function:</b> <br>
    The gradient of the Loss L is calculated w.r.t the predicted probabilities vector <b>&#375  = a</b>. One thing to remember that the Loss is a scalar quantity and the Predicted probabilities vector is a (3&times1) matrix. So, the gradient will be of shape (3&times1). This is given as
    <p align = "center">
      <img width = "600" height = "250" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/zeroHLccegrad.png">
    </p>
  </li>
  <li>
    <b>Gradient of SoftMax Activation Layer:</b> <br>
    The gradient of the SoftMax Activation Layer <b>&#375  = a</b> is calculated w.r.t the Raw Scores Vector <b>Z</b>. In this case, the Activation Layer vector <b>a</b> is a (3&times1) vector and <b>Z</b> is also a (3&times1) vector. So, the shape of the resulting gradient will be (3&times3). This is given as
    <p align = "center">
      <img weidth = "600" height = "250" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/zeroHLsftmaxgrad.png">
    </p>
  </li>
  <li>
   <b>Gradient of the Raw Scores Vector:</b> <br>
    The gradient of the Raw Scores Vector <b>Z</b> is calculated w.r.t the Weight matrix <b>W</b>. The Raw Scores Vector is a (3&times1) vector and the weights matrix <b>W</b> is of shape (3&times6). In short, the gradient of the final gradient is of shape (3&times6&times3). It is an example of a 3D Tensor. In plain english, it is a (6&times3) matrix that is repeating 3 times. This is given as
    <p align = "center">
      <img width = "600" height = "250" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/zeroHLrawscoregrad.png"
    </p>
  </li>
  <li>
    <b>Total Gradient Calculation In Backward Step of Zero Hidden Layer Neural Network: </b> <br>
    Thus combining all these three calculated gradient, I finally calculate the total gradient that flows backwards through these layers. This is given as
    <p align = "center">
      <img width = "600" height = "250" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/zeroHLtotalgrad1.png">
      <img width = "600" height = "250" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/zeroHLtotalgrad2.png">
    </p>
  </li>
</ol>
<hr>

<h2>4. Architecture of One Hidden Layer Neural Network:</h2>

In case of single hidden layer neural network, there is a hidden layer and output layer. The hidden layer contains a dense layer that receives input from the feature set corresponding to one sample. The Dense layer of Hidden LAayer has its own set of Weights and its own activation function (Sigmoid, tanh, ReLu, LEAKY ReLU). One thing to note that the Raw Scores vector <b>Z</b> is pointwise activated in any hidden layer. The architecture is given as
<p align = "center">
  <img width = "700" height = "250" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/oneHLNN.png"
</p>
<p>
  <ul>
    <li>The Dense Layer-1 is represented by the notation <b>Z<sup>[1]</sup></b>and it owns a set of weights; weight matrix <b>W<sup>[1]</sup></b>; of shape (4&times6) {Bias Added}</li>
    <li>The Raw Scores Vector <b>Z<sup>[1]</sup></b> is of shape (4&times1) whose elements are Z<sub>1</sub><sup>[1]</sup>, Z<sub>2</sub><sup>[1]</sup>, Z<sub>3</sub><sup>[1]</sup>, Z<sub>4</sub><sup>[1]</sup> respectively</li>
    <li>This Raw Score vector is pointwise activated to get the Activated Raw Scores Vectors, denoted as <b>a<sup>[1]</sup></b>, is of shape (4&times1), same as <b>Z<sup>[1]</sup></b></li>
    <li>Then the Whole NN move to the output layer that has its own Dense layer <b>Z<sup>[2]</sup> and SoftMax Activation Layer <b>a<sup>[2]</sup></b></li>
    <li>The Weights Matrix <b>W<sup>[2]</sup></b> is of shape (3&times5), shape of <b>Z<sup>[2]</sup></b> is (3&times1) which is same as shape of <b>a<sup>[2]</sup></b></li>
    <li>Then The CCE Loss is calculated which is a scalar quantity</li>
  </ul>
</p>
<hr>

<h2>5. Different Types of Activation Functions in Deep Learning:</h2>

In case of Hidden Layer, there are 4 mostly used Activation Functions that activates the Raw scores vectors pointwise. Among them Leaky ReLU is the most sufficient one as it ommits the problem of vanishing gradient. The other functions Sigmoid, Tanh and ReLU also works good, but it has vanishing gradient problem. These functions are given in the following picture
<p align = "center">
  <img width = "700" height = "300" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/ActivationFnc.png">
</p>
The gradient of these Acivation functions are also helpful in determining the optimal weights that is calculated by using the Gradient Descent Method. By looking at the gradients it can be observed there are some limitations with the first three Activation Functions. They are given in the following picture.
<p align = "center">
  <img width = "700" height = "300" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/gradActivationFnc.png">
</p>
<hr>

<h2>6. Backward Propagation In Single Hidden Layer Neural Network:</h2>

Just like zero hidden layer neural network, backward propagation works similarly in case of one hidden layer neural network. The only difference is in one hidden layer neural network the gradient calculation is slightly complex that a simple 0 hidden layer neural network. The backward flow of gradient is given as
<p align = "center">
  <img width = "700" height = "300" src = "https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/oneHLgradCalculation.png">
</p>
<hr>

<h2>7. Deep L-Layered Neural Network Architecture:</h2>

Suppose, we consider that there are 2 hidden layers in a neural network. The architecture can be enumerated similarly if there are l numbers of hidden layers. For a 3-layered neural network(2 Hidden layers) the neural network architecture is given as



