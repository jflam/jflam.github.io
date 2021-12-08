+++
title="2021-12-08"
date=2021-12-08
+++

{% block() %}
Our talk yesterday was about using Transformer models to win a [Kaggle
competition](https://www.kaggle.com/c/riiid-test-answer-prediction) at a
training cost of less than $50 on Azure. Fortunately, Alon understands what
Transformer models are, and he did a wonderful job of summarizing what a
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
are used to do _branch-free table selection_. Let that sink in for a minute:
you want to select all the "fizz" from:

```python
['fizz', 'buzz', 'fizz', 'fizz']
```

How would you do that WITHOUT COMPARISONS and BRANCHING in CONSTANT TIME?
:exploding_head: Apparently this is one of the key insights from Transformers.
{% end %}

