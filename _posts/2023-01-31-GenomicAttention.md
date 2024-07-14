---
layout: post
title: Genomic Attention
subtitle: Transformers for genomic prediction
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
cover-img: /assets/img/robotbreed.jfif
tags: [maize,language models]
comments: true
---

This post covers work related to a recent GEM maize competition where users were provided SNP data, weather data, and additional data to predict the yields in an unseen year.

## I. Overview of the Problem

### i. Genomic Prediction

Plant breeding relies on predicting the breeding value of individuals. The ability to do so allows a breeder to sift through hundreds of thousands of individuals versus thousands. Breeders primarily care about additive variation (which is linear and independent) because this variation is most likely to be passed on from parents to offspring. On the other hand, non-additive variation (from epistasie( g * g ) and environment (g * e) can technically be used to improve the accuracy of prediction.

gBLUP has been the traditional methodology for predicting breeding values, since it captures linear effects. However, in the past two years, new approaches have bled into the plant breeding space, namely from the deep learning tool, transformers.


### ii. Transformers

Transformers have swept the entire field of machine learning, gradually since their inception in 2017. Ever since, increasingly, they have been adapted to virtually every domain and data type, originally from text then from images to biological sequence.

The major improvement over previous models, is that the transformer leverages 'attention'. Attention allows the model to find interactions across a given sequence (like a gene or genome). The interactions can be discovered across a sequence, allowing elements (like a nucleotide at a given position) to capture interactions with other distant elements.

In short, the transformer takes in a sequence, and returns a new sequence which represents a more useful representation for the task at hand.

### iii. Transformers for Genomic Prediction

There are several important considerations for using transformers for the use-case of genomic prediction.

DNA Compression: First, transformers may be powerful, but they are also computationally hungry. With modern breeding programs, the number of SNPs or genes used as input may vary from 500 to 500,000. Historically, the maximum number of input sequences is limited to 1024 or so tokens. Therefore we must compress the genotype input to the transformer.
- Solutions in previous models, like the Enformer model (citation) use convolutional layers to reduce the input size.




## II. Real Application
#### The Machine Learning Model
#### Discussion

This project was developed with pytorch and nbdev. See the documentation here: https://cjgo.github.io/hybridpredictmaize22/

I successfully replicated the performance of the model a recent paper by replicating their architecture.

Thanks to http://www.genomes2fields.org/

