---
title: "Facial Recognition & Computer Vision"
excerpt: "The goal of this projct is to learn the fundamentals of visual machine learning, complete tutorials as well as
apply the models on my own data set."
collection: portfolio
---

# Visual Machine Learning

## Important Terms To Know
Before starting a project with visual machine learning or facial recognition it is important to understand the
basics behind how facial recognition & machine learning work.

*Histogram of Oriented Gradients (HOG):* When doing facial recongition, this feature descriptior allows for each image to be simplifed into a single variable. HOG breaks the image into sizes of (width * heigh & channel (colors)). The final vectors are used to compare histograms of images and typically ran through a SVM to produce a nonlinear classification.

*Support Vector Machine (SVM):* The classification aglorithm that the most popular image recognition library dlib uses. SVM is a supervised learning model that can be used for classification and is good for non-linear classification (which is image machine learning)

*Convolutional Neural Networks (CNN):* a classification that takes an input imge and is able to classify it into certain categories. This model will train and test each input (iamge) into different layers with filters - returning a single value between 0 and 1 to predict how an item should be classified.

### How does CNN Work?
To best understand how a CNN worked, I learned from the article Understanding of Convolutional Neural Network (CNN) - Deep Learning by Prabhu. https://medium.com/@RaghavPrabhu/understanding-ofconvolutional-neural-network-cnn-deep-learning-99760835f148


Steps for CNN Modeling This process can be repeated as many times as is necessary (or set) in the model to classify images.
1. **Input** : Provide Image Input to model
2. **Convolution**: extract the first layer of the image, but preserve the relationship between the pixels. This will create the first "feature map" for the model
3. **ReLU**: (Rectified Linear Unit for a non-linear operation) introduces non-linarity to the model. The more non0linear the function is, the more complex of a problem it will be able to complete. This activation function f(x )=max(0, x) helps to increase the speed of training by removing the negative elements and setting them


## Facial Recognition
For this project & learning Facial Recongition machine learning I utilized the tutorials available from https://github.com/ageitgey/face_recognition (https://github.com/ageitgey/face_recognition). This face_recongition library was built using the library dlib (https://github.com/davisking/dlib/blob/master/examples/dnn_metric_learning_ex.cpp (https://github.com/davisking/dlib/blob/master/examples/dnn_metric_learning_ex.cpp)) which utlitizes deep learning for facial recognition.

#### Installation
The first step is to install all neccesary dependencies and packages:
download repository https://github.com/ageitgey/face_recognition.git
(https://github.com/ageitgey/face_recognition.git)
then run: python setup.py install

#### Identifying Who is In A Photo
Utilizing a training photo to let the program know who was who in each photo.
This is done through a three-step process:
1. Load both images, the known image & the unknown image
2. Run each image through the function face_encodings. This function runs through the process explained
about encoding images into their feature files. This is done for both of the images because it is what will be
used to compare the two files.
3. Run each encoding of images through the compare_face function. This function will take both of the
encodings and compares the list of features to determine if it is a match. This will return the list of true/false
results for the matched pictures. Since this round we are only doing 1 image, we will expect only a single
true or false to be returned. Since it is not two pictures of myself I would expect to have false returned.
The Known Image in this case will be myself:
![ALLISON](/images/facialrecog/Picture1.png)

And the Unknown Image a different female who shares the same age, race and ethicnity as myself.
![UNKNOWN1](/images/facialrecog/Picture2.png)



