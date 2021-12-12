+++
title="2021-12-08"
date=2021-12-08
+++

{% block() %}
Our talk yesterday was about using Transformer models to win a [Kaggle
competition](https://www.kaggle.com/c/riiid-test-answer-prediction) at a
training cost of less than $50 on Azure. Fortunately, Alon understands what
Transformer models are, and he did a wonderful job of summarizing what 
Transformer model is in about 5 minutes.

I really wanted to learn more about Transforrmer models; I've been treating
them mostly as a black box and using pre-trained Transformer models to make
cool things like my [semantic wine review search
engine](https://github.com/jflam/wine). Coincidentally, this morning someone
from work linked this tweet:

{{ twitter(id="1468370605229547522?s=20")}}

and he subsequently found a link to this fantastic explanation of Transformer
models called [Transformers From
Scratch](https://e2eml.school/transformers.html) written by Brandon Roher (hi
Brandon!) I'm still working through the piece but one thing that I had not
understood before was how matrix multiplication and one-hot encoded vectors
are used to do _branch-free selection of rows from a table_. Let that sink in
for a minute: how would you do that WITHOUT COMPARISONS and BRANCHING?
:exploding_head: 

Apparently this is one of the key insights from Transformers. There's a whole
lot of branching and comparing in this Python list comprehension:

`[x for x in ['fizz','buzz','fizz','fizz'] if x == 'fizz']`

{% end %}

{% block() %}
Continuing to take notes on Brandon's tutorial on the flight home. There is a
concept of _selective masking_ that is in the original Transformers paper.
Here is an [annotated Attention is All You Need
paper](https://nlp.seas.harvard.edu/2018/04/03/attention.html). 

In his explanation, there are a large number of unhelpful predictions where
there is a 50:50 probability of some outcome in his highly simplified
example. Masking is a concept to drive low probability events to zero to
eliminate them from consideration, and is the central idea in Transformers.

He summarizes the first part of his explanation through three ideas:

1. Turning everything into matrix multiplication is a good idea. As I 
   observed above, being able to select rows out of a table (or matrix) by
   doing nothing more than matrix multiplication is incredibly efficient.

1. Each step during training must be differentiable, i.e., each adjustment
   to a parameter must result in a calculation of the model error / loss
   function.

1. Having _smooth gradients_ is really important, He has a nice analogy 
   between ML gradients and hills/mountains/valleys in the real world. He
   describes the art of data science in ensuring that the gradients are 
   smooth and "well-conditioned", i.e., they shouldn't quickly drop to zero
   or rise to infinity.

{% end %}