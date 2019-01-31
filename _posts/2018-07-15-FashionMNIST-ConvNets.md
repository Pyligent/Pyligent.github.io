---
layout: post
title: FashionMNIST ConvNets
subtitle: Keras Deep Learning R
bigimg: /img/path.jpg
image: /img/fn.png
tags: [Machine Learning, Deep Learning,Keras,R]
---

#### Use two Deep learning models to Classify the image from Fashion-MNIST dataset

- Basic Model (fully connected layer model)

- Convolutional neural networks (ConvNets)

All model will use the Keras framework with R implementation 

#### [Data Set](https://www.kaggle.com/zalando-research/fashionmnist/data)

- 60000 images for training and 10000 images for testing
- Each example is a 28x28 gray-scale image, associated with a label from 
   + 0 T-shirt/top
   + 1 Trouser
   + 2 Pullover
   + 3 Dress
   + 4 Coat
   + 5 Sandal
   + 6 Shirt
   + 7 Sneaker
   + 8 Bag
   + 9 Ankle boot 
   + 10 classes 

- The dataset is CSV format. The detailed format is label, pixel1, pixel2, pixel3, ... pixel784. Each image is 28 pixels in height and 28 pixels in width, for a total of 784 pixels in total 

#### Problem  
     - Train the 60000 images and test 10000 images to classify the image’s label
#### Problem Type
    -  Multi-Class and single-label classification
#### Model Configuration
    - the softmax as the last-layer’s activation and the loss function will use the categorical_crossentropy. 
#### Hyper-parameters setting
    - use the dropout and L2 regularization to reduce over-fitting effects.
#### Assembling Data Set   
    - Using the dataset_fashion_mnist() function from Keras to download the dataset (simple model)
    - Downloaded from the Kaggle.com, then use the read_csv() to manipulate the data (ConvNets Model)
    
#### Simple Model Result
    - Simple deep learning model achieves an accuracy of 88.11% and loss of 34.15%.

![sim0](/img/plot_image/sim_0.png)
![sim1](/img/plot_image/sim1.png)
    
#### ConvNets Model Result  
    - ConvNets model achieves an accuracy of 91.85% and loss is 20%, up from the previous model’s accuracy of 88.11% and   loss of 34.15%. 

![con](/img/plot_image/simple_res.png)
![con1](/img/plot_image/simple_res2.png)

#### Summary
- Our ConvNets model achieved an accuracy of 91.85%. It turns out our classifier does better than the Kaggle’s best baseline reported [here](https://www.kaggle.com/zalando-research/fashionmnist/data) , which is an SVM classifier with mean accuracy of 89.7%.
   - Comparing the simple model, ConvNets is the best model for the attacking the image classification problems.  
   - Tuning the model and hyper-parameters is very important to improve the accuracy.


     

