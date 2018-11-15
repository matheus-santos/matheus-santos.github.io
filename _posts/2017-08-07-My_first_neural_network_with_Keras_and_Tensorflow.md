---
layout: default
title: "My first neural network with Keras and Tensorflow"
date: 2017-08-07 22:25:00 -0300
categories: machine-learning
comments: true
---

Hey folks, Matt here.

Machine learning is a hot subject nowadays. Every company wants to build its own magical black box that deals with thousands of variables at the same time to give an accurate answer about a complex problem that no one knows exactly what it is. But Machine Learning is a broad area with dozens of techniques and hard math models so you need to have a good grasp of math and statistics.

Fortunately we don't need to dig deeper into mathemagical concepts. There are a lot of frameworks and libraries that will do the heavylift letting us free to think about our problem instead of having to solve how do minimize a matrix with 100 features efficiently.

In this post I am going to talk about neural networks and how to implement your first NN using some top-notch tools that will make the models simpler to understand and maintain.

Ok, so let's get the ingredients. I assume you already know a little bit of Python, but if you no bullocks about it don't worry, you will see that is easy to start and understand the code. We will use:

- [Python 3.6](https://www.python.org/downloads/release/python-360/)
- [Keras: Deep Learning library for Python](https://github.com/fchollet/keras)
- [Tensorflow: Computation using data flow graphs for scalable machine learning](https://github.com/tensorflow/tensorflow)

The first part I will explain what is a neural network and basically how to use it. The second part we will use the classic example of ["Iris Data Set"](http://archive.ics.uci.edu/ml/datasets/Iris) and build our pipeline to classify a iris plant. Third and last part we discuss some key points to improve the project and where to go next.

# What is a neural network

Artificial neural networks (ANN) are computing systems inspired by the biological neural networks that constitute animal brains and it is not a new thing. Warren McCulloch and Walter Pitts (1943) created a computational model for neural networks based on mathematics and algorithms called threshold logic. This concepts were a little frozen since because it lacks the required computational power to deal with the many calculations and backpropagation. That is why it is so popular nowadays: thanks to advance of technology and cloud services we have limitless power to work with these concepts.

Basically an ANN is a network intended to work like the brain: through stimulations that passes to a neuron to another. A neuron receives a signal, a interaction occurs and then it passes to the next neuron. In the end these interactions results in a final value (or group of values) that we use to classify complex problems.

[TODO Figure 1 - Basic ANN diagram with neurons and connections.]

That is it. We basically use ANNs to help us classify a group of features that are to complex to use simpler techniques like logistic regression.

Now that we have a basic grasp of what is a neural network, I will present you an example on how to build and interpret one using the classic example Iris Plant by UCI Machine Learning Repository [[1]](https://archive.ics.uci.edu/ml/datasets/iris).

# Classifying iris plant with Keras and TensorFlow

To help us build these complex classifiers

## Enter TensorFlow

## Enter Keras

# Next steps

# References

- [1] Fisher, 1936. [UCI Machine Learning Repository - Iris Plant](https://archive.ics.uci.edu/ml/datasets/iris).

---

- Why
  - Popularity of machine learning
  - Solve hard problems with machine learning
  - Rise of Deep Learning
- How
  - How to setup environment
  - Life cycle of a model
- What
  - What is Keras
  - What is TensorFlow
- Conclusion
  - Kaggle
  - Github repos
  - Courses
- References
- Next/Prev article

References
https://machinelearningmastery.com/multi-class-classification-tutorial-keras-deep-learning-library/
