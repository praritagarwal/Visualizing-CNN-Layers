# Visualizing CNN Layers


Project to visualize the kernels and the outputs of the individual layers of a CNN built in pytorch. 

## Visualizing CNN Layers.ipynb

This was my first attempt at visualizing the features learnt by the layers of a neural net. 

In this notebook, I trained a simple neural network on the MNIST dataset. My architecture consisting of 2 Convolutional layers and one linear layer. 

I then registered a forward *hook* for each of the convolutional layer, using which I was able to obtain the output produced by that layer in response to an image-input to the network. This was based on [this](https://discuss.pytorch.org/t/visualize-feature-map/29597) discussion. We can now analyse this output to see what parts of the input image activate the layer the most.

I then show a method to access the output of any layer in the network without the using any hooks. This was done by directly accessing the layers through the *_modules* variable of the *nn.Module* class.

An advantage of the second method is that it allows us direct access to the individual layers in the neural network which then also enables us to see the weights learned by the kernels of any channel that layer. This too has been demostrated in the last section of the this notebook. 

## AlexNet.ipynb

In this notebook I plotted the kernels that were learnt by first layer of AlexNet. This is equivalent to Figure 3 in [this](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf) paper with the only difference being that the pretrained model available in pytorch is based on a slightly modified architecture as described in [this](https://arxiv.org/abs/1404.5997) paper. For e.g. instead of 96 convolutional neurons there are only 64 neurons in the first layer.  


## Activation Maximization.ipynb

In this notebook I try to visualize the features learnt the layer in a pretrained GoogLeNet by implementing the *activation maximization* technique proposed in [this](http://www.image-net.org/papers/imagenet_cvpr09.pdf) paper.


Based on the discussion in [this](https://distill.pub/2017/feature-visualization/) post. 

### Trial 1: Naive application of activation maximization 

 - This resulted in a high frequency image similar to Fig. 2b in [this](https://arxiv.org/pdf/1904.08939.pdf) paper. It was hard to recognize the features learnt by the layer from this image. 


### Trial 2: Activation Maximization with image rescaling 
 
 - It was suggested in [this](https://towardsdatascience.com/how-to-visualize-convolutional-features-in-40-lines-of-code-70b7d87b0030) blog and also on page 6 of [this](https://arxiv.org/pdf/1904.08939.pdf) paper that gradually upscaling th image can somewhat ameliorate the appearance of high-frequency objects in the image. I gave this a try but output image was hardly any different from what I got in Trial 1.


### Trial 3: Activation Maximization with RMS activation

 - In this trial I simply tried to use Root-Mean-Squared value of the layer/channel output as my activation. This didn't change anything significantly. 


### Trial 4: Activation Maximization with L2 reg. for pixel intensities

  - Taking cue from [this](https://arxiv.org/pdf/1312.6034.pdf) paper, I added an L2 regularizer for the pixel intensities. This leads to the introduction of hyperparameter which controls the weightage of the regularizer relative to the activation of the layer/channel. I tried various values ranging from 0 to 30 in steps of 5. However, the results didn't change much except that the regularizer caused the background of the final image to become suppressed. 



This is work in progress. 
