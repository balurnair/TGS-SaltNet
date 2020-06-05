# TGS-SaltNet
Kaggle | 21st place solution for TGS Salt Identification Challenge

## General
Kaggle competition [TGS Salt Identification Challenge](https://www.kaggle.com/c/tgs-salt-identification-challenge)
 The code demonstrates usage of different important techniques using [fast.ai](http://www.fast.ai/) and [PyTorch](https://pytorch.org/).
 
1. Use ResNet model as an encoder for UNet. 
 Resnet model as backbone give better results with Unet as compared to vanilla Unet model. 

2. Add intermediate layers like [BAM](http://bmvc2018.org/contents/papers/0092.pdf),[Squeeze & Excitation](https://arxiv.org/abs/1803.02579) blocks in a ResNet34 model which can be easily replicated for other network architectures.

3. Show how to add [Deep supervision](https://www.kaggle.com/c/tgs-salt-identification-challenge/discussion/65933) to the network, and calculate loss and combine loss at different scale. 



**BAM**

“Bottleneck Attention Module” (BAM), a simple and efficient attention module that can be used in any CNNs. Given a 3D feature
map, BAM produces a 3D attention map to emphasize important elements. In BAM, we decompose the process of inferring a 3D attention map in two streams, so that the computational and parametric overhead are significantly reduced. As the channels of feature maps can be regarded as feature detectors, the two branches (spatial and channel) explicitly learn ‘what’ and ‘where’ to focus on.

**Squeeze and Excitation Blocks**

Squeeze-and-Excitation Networks (SENets) introduce a building block for CNNs that improves channel interdependencies at almost no computational cost. Main idea is add parameters to each channel of a convolutional block so that the network can adaptively adjust the weighting of each feature map.The network weights each of its channels equally when creating the output feature maps. SENets are all about changing this by adding a content aware mechanism to weight each channel adaptively. In it’s most basic form this could mean adding a single parameter to each channel and giving it a linear scalar how relevant each one is.

**Deep Supervision**

In this, we combine features from each layer using hypercolumn technique and combine multiple loss like classification loss and semantic loss to form a deeply supervised model. 
Many algorithms using features from CNNs (Convolutional Neural Networks) usually use the last FC (fully-connected) layer features in order to extract information about certain input. However, the information in the last FC layer may be too coarse spatially to allow precise localization (due to sequences of maxpooling, etc.), on the other side, the first layers may be spatially precise but will lack semantic information. To get the best of both worlds, the authors of the hypercolumn paper define the hypercolumn of a pixel as the vector of activations of all CNN units “above” that pixel.

## Main software used

1. fastai - 0.7
2. pytorch - 0.4
3. python - 3.6

## Hardware required

The code was tested with TitanX GPU/1080ti.



