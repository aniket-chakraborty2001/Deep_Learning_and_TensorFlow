# Deep_Learning_and_TensorFlow
<br>
This project covers the topic of Deep Learning and to achieve models in Deep Learning using TensorFlow library in python. For some parts I am using the numpy library of Python. This project is done by defining class, an instance of object oriented programming. The contents of this project are dicussed briefly in this Readme file.
<hr>
<h2>1. Zero Hidden Layer Neural Network Architecture:</h2>
In case of Zero Hidden Layer Neural Network, there are 1 input layer and 1 output layer. The input layer contains the feature set. For ease of discussion, here I am considering only one sample. The output layer itself contains two sub layers. They are Dense layer and SoftMax Activation layer. <br>
* <b>Dense Layer</b> owns a set of weights that are specific to features and output class labels. The input of Dense layer are the features. The output of Dense layer is the Raw Score, denoted by <b>Z</b>. Suppose, <b>W</b> is the weights matrix and <b>X</b> is the feature set. Then the raw score Z is given as Z = <b>WX</b> + b , where b is the bias term. <br>
* <b>SoftMax Activation Layer</b> is the second sub-layer of the output layer. The input of this layer are the raw scores vector (<b>Z</b>) that comes from previous layer; the output of the layer is the SoftMax activated raw scores, denoted as <b>a</b> , where <b>a<b> = SoftMax(<b>Z</b>). The SoftMax function is achieved by raising the entries of <b>Z</b> to the power of e(exponential power) to eliminate negative values and then normalize it to decrese the magnitude of the values. <br>

<h4>Zero Hidden Layer Neural Network Architecture Diagram:</h4>

Suppose we have 5 output features x<sub>1</sub>, x<sub>2</sub>, x<sub>3</sub>, x<sub>4</sub>, x<sub>5</sub> respectively and consider the bias term b in the input layer. Then a zero hidden layer neural network architecture can be given as
<p align="center">
  <img width="500" height="400" src="https://github.com/aniket-chakraborty2001/Deep_Learning_and_TensorFlow/blob/main/Images/ZeroHLNN.png">
</p>
<p>
  * The Weights Matrix <b>W</b> that is owned by the Dense Layer is of shape (3&times6) <br>
  * The Raw Scores Vector <b>Z</b> is of shape (3&times1), elements of which are z<sub>1</sub>, z<sub>2</sub>, z<sub>3</sub> respectively <br>
  * The Activated Raw Scores Vector <b>a</b> is of shape (3&times1), elements of which are a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub> respectively <br>
  * Finally, Loss L is calculated, which is a scaler quantity
</p> 
<hr>
<h2>2. Zero Hidden Layer Neural Network Categorical Cross Entropy Loss (CCE):</h2>



