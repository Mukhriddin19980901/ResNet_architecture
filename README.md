# ResNet_architecture

I have implemented a ResNet model in TensorFlow using a combination of convolutional blocks and identity blocks. This is a deep convolutional neural network architecture often used for image classification tasks. My code defines the ResNet model with 50 layers, which is a common variant known as ResNet-50.

<img src="https://github.com/Mukhriddin19980901/ResNet_architecture/blob/main/r50.png" width="500" height="400" />

Here's an explanation of my code:

1.***'convolution_block'*** and ***'identity_block'*** functions:

-convolution_block: Defines a convolutional block that consists of three convolutional layers and a shortcut connection. This block is used to increase the depth of the network.
-identity_block: Defines an identity block with three convolutional layers and a shortcut connection that skips one or more layers. This block helps maintain the same depth of the network.

2.ResNet class:

-The constructor **__init__** defines the ResNet model architecture. It takes *'input_shape'* (the shape of input images) and *'classes'* (the number of output classes) as arguments.
-The model begins with initial **convolution**, **batch normalization**, and **activation layers**, followed by **max-pooling**.
-It then constructs different stages of the ResNet architecture using ***convolution_block*** and ***identity_block*** functions.
-The final stage involves average pooling, flattening, and a dense layer for classification.
-The model is constructed using TensorFlow's Functional API.
-The ***call*** method simply calls the underlying **ResNet** model.

3.Instantiating and building the model:

-The input_size and classes variables are defined to specify the input size and the number of output classes.
-The ResNet class is instantiated as resnet_model, and then the model is built with a sample input shape.
4.Summarizing the model:

-The **resnet_model.summary()** command prints a summary of the model's architecture, showing layer names, output shapes, and the number of parameters.
  One thing to note is that you seem to be using labels as a variable without defining it. Make sure you have a list or array of class labels to use for your specific classification task.

-As my model is **functional** I have build training and testing sessions by creating function with decoration ***@tf.funtion**.This allows us to train the model.First we create objects
from **loss function** and **optimizer**.The data labels we are using is **'uint16'** so we use **"SparseCategoricalCrossEntropy"** loss function and **"Adam"** optimizer.

  5.I have train my model with 10 **epochs** to save time. But you can change the number **epochs** to decrease loss and increse accuracy.Here you can see a sudden change of loss and validation 
loss at initial phases of the training session .But then we can't see huge difference. Both accuracies on the other hand gradually increased after second epoch.

<img src="https://github.com/Mukhriddin19980901/ResNet_architecture/blob/main/acc.png" width="500" height="400" />


<img src="https://github.com/Mukhriddin19980901/ResNet_architecture/blob/main/loss.png" width="500" height="400" />
 
