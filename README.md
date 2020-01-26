# Visualizing CNN Layers


Project to visualize the kernels and the outputs of the individual layers of a CNN built in pytorch. 

## Visualizing CNN Layers.ipynb

This was my first attempt at visualizing the features learnt by the layers of a neural net. 

In this notebook, I trained a simple neural network on the MNIST dataset. My architecture consisting of 2 Convolutional layers and one linear layer. 

I then registered a forward *hook* for each of the convolutional layer, using which I was able to obtain the output produced by that layer in response to an image-input to the network. This was based on [this](https://discuss.pytorch.org/t/visualize-feature-map/29597) discussion. We can now analyse this output to see what parts of the input image activate the layer the most.

I then show a method to access the output of any layer in the network without the using any hooks. This was done by directly accessing the layers through the *_modules* variable of the *nn.Module* class.

An advantage of the second method is that it allows us direct access to the individual layers in the neural network which then also enables us to see the weights learned by the kernels of any channel that layer. This too has been demostrated in the last section of the this notebook. 

## Feature Visualization by Optimization.ipynb

In this notebook I try to visualize the features learnt the layer in a pretrained GoogLeNet by implementing the *activation maximization* technique proposed in [this](http://www.image-net.org/papers/imagenet_cvpr09.pdf) paper.


Based on the discussion in [this](https://distill.pub/2017/feature-visualization/) post. 

This is work in progress. 