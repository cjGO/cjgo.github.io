---
layout: post
title: Synthetic Arabidopsis
subtitle: Procedural Machine Learning
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
tags: [test]
comments: true
---

This blog post presents an overview of a brief experiment about synthetic data for agriculture. It is an end-to-end project; meaning that it will cover the creation of data to the results of a model which uses said data. This field is a burgeoning field. I will briefly outline what this field is all about before going into the details. 


![image](https://user-images.githubusercontent.com/12351695/120893459-75a80500-c624-11eb-908c-827e8b302d55.png)


## I. Overview of the Problem

### i. MACHINE LEARNING

Machine Learning is pattern recognition. These patterns can be buying patterns, peak traffic prediction, or signs of disease in a patients X-ray scans. Once models are trained , they can approximate what an expert may say. Imagine a world with 100 experts in an important subject which is in such high demand that the number of requests for the experts’ opinion could never be met. If these 100 experts labeled data, a model could approximate their analysis enabling the entire world to benefit from their expertise.

However, in the present day, successful Machine Learning models rely on vast amounts of data. In more complex scenarios, like the medical setting, patient records/X-ray scans must be labeled by a human. Simply put, there is not enough of this medical data to have as significant an impact as Amazon performing product recommendations. That is the bottleneck to improving the quality of life globally with these tools.

This is the problem that Synthetic Data seeks to improve.

### ii. Computer Vision

Imagine creating a model to count the number of apples an orchard. This model will inform the growers of the progress of their crop, allow them to plan expensive labor, and monitor potential diseases or stresses they may need to manage. Ideally, this model would scan their orchard each day providing counts of apples and their stage (small apple to ripe apple). This could potentially lead to cost saving measures to make their business more profitable.

Images of the orchard are acquired daily for 1 year. Then a human looks at these images, and labels where the apples are in each image. These images are now “annotated images”. The annotated images are used to train a model. This in short, is how Machine Learning models are trained.

However, there are several problems
1) *NUMBER ANNOTATED IMAGES* : It would be a huge cost to pay people to click through each of these images and wouldn’t result in a very high number of images.
2) *BIAS IN AVAILABLE IMAGES* : e.g. The weather from this year was generally sunny, there were very few cloudy days

Ignoring these problems and creating a model from the available years images will result in a model that works very well, only some of the time, when the conditions were very similar to the year the images were acquired. Maybe the following year there were more cloudy days, greater humidity, all of which affect how the plant looks, grows, or changes the quality of the images. This breaks the models performance, meaning it can not be used for the cost-saving measures as desired.

### iii. Synthetic Data

Synthetic Data is the crossroads between modern video games and Machine Learning. Thanks to “Procedural Generation” we can create an infinite number of unique 3D objects. In the context of an orchard, you can imagine growing a seed into a tree which in turn grows apples. The “procedural” part means that this tree grows according to rules which have subtelties. You can now grow an ENTIRE orchard of UNIQUE trees with UNIQUE apples! It is as if you grew years of orchards in real life. Every tree is different. This is in essence what synthetic data is; with one additional feature. This feature is “automatic annotations”. Since a computer program was used to grow these unique trees, the program also knows which pixel belongs to the tree’s trunk, leaves, or individual apples. This is incredibly intriguing for training machine learning models. Because not only do we have variable data, it is completely annotated. This saves humans the troubles of taking images, and labeling images. Not to mention planting an apple seed, tending an orchard for severals of years! 


NUMBER OF ANNOTATED IMAGES : Now with our synthetic orchards, we can generate thousands, or even millions of trees to train our model with the push of a button. 

BIAS: On top of this, we can also simulate tornadoes, hurricanes, fires, clouds, air pollution, and every possible type of stress ( from insect damage, to hail damage, to heat stress, to frost ). We can now address the issue of bias we would have from only acquiring 1 years worth of images from a single orchard. With enough knowledge about plant physiology, we can make the leaves bend, curl, or discolor as we please. In theory, this will make the apple counting model much more reliable and we can base our management decisions from the model with greater confidence ; reducing our risk and maximizing our profits.



## II. Real Application

Arabidopsis is the “model” organism of plant biology, typically all innovation begins with the model organisms of science. We will continue this tradition with our explorations of synthetic data for machine learning and computer vision. 

We start simple; we want to track the growth of arabidopsis plants. This means counting the number of leaves, and recording the size of each leaf. This tells us how well the plant is growing. Some arabidopsis plants from different backgrounds may grow faster/slower depending on the conditions and their genetics. Our model will track this, taking a measurement (potentially) every minute/second/hour/day.

Introducing SideFX’s Houdini; You have definitely witnessed the fruit from this software program if you’ve watched major movies or tv series in the past decade. This program is ideal for creating synthetic data because it’s foundation is set in the proceduralism which helps us produce unique plants with the click of a button. Below is an image of an arabidopsis plant created in Houdini. The other image is how it is constructed in houdini ( a graph of nodes which define the rules and variations for each plant ). 

With this setup in Houdini, we can create many unique plants and we know which pixel belongs to each individual leaf.






