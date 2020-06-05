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
