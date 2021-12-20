+++
title="2021-12-19"
date=2021-12-19
+++

Today, I'm starting to work on the 4th edition of the
[fastai](https://github.com/fastai/fastai) course, and I'll be note-taking on
this blog. At the start Jeremy shows this lovely photo of the Mark 1
perceptron at Cornell circa 1961. It does a great job at showing the
complexity of the connections in a neural network:

![](2021-12-19/2021-12-19-07-38-03.png)

Some housekeeping things that are pretty cool that intersects with my day job
at Microsoft building tools for data scientists. 

I'm using my [ez](https://github.com/jflam/ez) to run the `fastai` notebooks
locally on my Windows machine which has an RTX2080 GPU. All I need to do is
run a single command: 

```bash
$ ez env go git@github.com:jflam/fastai -n .
```

You'll notice that I'm using my own [fork](https://github.com/jflam/fastai) of
the `fastai` repo which contains only a aingle configuration file: `ez.json`
that `ez` uses to build and run the image in VS Code. 
This is the entire contents of the `ez.json` file:

```json
{
    "requires_gpu": "true",
    "base_container_image": "fastdotai/fastai:latest"
}
```

After running that command, this is what `ez` created on my machine:

![](2021-12-19/2021-12-19-07-53-47.png)

It's a fully functional running Docker container with GPU support enabled and
VS Code is bound to it using the VS Code Remote Containers extension. There's 
a fair amount of manual steps that would have been needed to get this running
and `ez` eliminates the need to do any of that - you get straight to the 
course in a running _local_ environment.

I'm also using GitHub Codespaces to view the notebooks for the book version of
the course. All you need to do is go to the
[fastbook](https://github.dev/fastai/fastbook) GitHub repo and press the `.`
key to open up Codespaces in the browser to view the contents of the notebook:

![](2021-12-19/2021-12-19-08-08-53.png)

Of course, if you are able to, please support the authors by
[purchasing](https://www.oreilly.com/library/view/deep-learning-for/9781492045519/)
a copy of the book.
{% end %}

Jerermy introduces his pedagogy for the class at the start, based on the work
of David Perkins. I love this image:

![](2021-12-19/2021-12-19-08-19-21.png)

Begin by "building state-of-the-art world-class models" as your Hello, World.

Jeremy and Sylvain wrote a paper on the [fastai
library](https://arxiv.org/abs/2002.04688) which is the layer of software on
top of PyTorch that is used in the course.

While following along in the first video of the course, I realized that 
Jeremy is running some of the cells in the notebooks from the [fastbook](https://github.com/fastai/fastbook) repo. So I forked and copied the `ez.json` file into that 
repo and was quickly able to reproduce his results using `ez`:

```bash
ez env go -g git@github.com/jflam/fastbook -n .
```

A quick note - the `-n .` parameter tells `ez` to run the repo locally. `ez`
also supports running on Azure VMs using the same command. See the docs in the
[ez](https://github.com/jflam/ez) for more details on the setup on Azure (it's
only 2 additional commands!)

This is a screenshot from my computer this morning after running the first
model in the course. You can see that I'm using the Outline feature in VS Code
notebooks to see an outline of the different sections from the first chapter
of the book:

![](2021-12-19/2021-12-19-09-42-15.png)

Terminology:
- _classification_ model predicts one of a number of discrete possibilities,
  e.g., "dog" or "cat
- _regression_ models predict a numeric (continuous?) quantity

`valid_pct=0.2` in the code means that it holds back 20% of the data to
validate the accuracy of the model. This is also the default in case you
forget to set it

a _learner_ contains your data, your architecture and also a metric to
optimize for:

```python
learn = cnn_learner(dls, resnet34, metrics=error_rate)
```

An `epoch` is looking at every item in the dataset once

`accuracy` is another function which is define as `1.0 - error_rate`

error_rate and accuracy are not good _loss functions_ which is a bit
counter-intuitive as those are the values that humans care about, but it turns
out that they are poor loss functions which are used to tune the parameters in
the model across epochs

fastai uses the validation set to determine the accuracy or error rate of a 
model

Remember that a model is parameters + architecture

Training, validation, test datasets - this is used for things like Kaggle

Actual performance is withheld from models so that you can avoid the
overfitting problem as well

In a time series you can't really create a validation dataset by random
sampling, instead you need to chop off the end, since that's really the goal -
to predict the future, not make predictions at random points in the past. We 
need to have different sampling algorithms based on the nature of the data and
the predictions desired.

Discusses a case about loss functions vs. metrics. One way to think about
overfitting is a case where your model keeps getting better at making
predictions in the training dataset, but starts getting worse against the
validation dataset. This can be an indication of overfitting. Jeremy cautions
that this is different from changes in the loss function however, and he will
get into the mathematics behind this later when he discusses loss functions in
more detail.

Definition: _transfer learning_ is using a pretrained model for a task
different from the one it was originally trained for. The `fine_tune()` method
called that because it is doing transfer learning. In the examples earlier
with resnet34, it was performing transfer learning against the model to get
the superior performance. It lets you use less data and less compute to
accomplish our goals.

Zeiler and Fergus published a paper in 2013 [Visualizing and Understanding
Convolutional Networks](https://arxiv.org/abs/1311.2901). It showed how
different layers in the network recognize initially simple patterns and then
become more specialized in later layers. I think this is done by activations
of different filters against an image, so that you can see the parts of the
image that a filter gets activated against. This paper gives a good mental
model for thinking about how filters can be generalized and how transfer
learning can take advantage of filters in earlier layers.

Sound detection can work by turning sounds into pictures and using CNNs to
classify them:

![](2021-12-19/2021-12-19-22-16-17.png)

Here's a really cool example of detecting fraudulent activity by looking at
traces of mouse movements and clicks and turning them into pictures (done by a
fastai student at Splunk - [blog that announced this
result](https://www.splunk.com/en_us/blog/security/deep-learning-with-splunk-and-tensorflow-for-security-catching-the-fraudster-in-neural-networks-with-behavioral-biometrics.html)


![](2021-12-19/2021-12-19-22-15-22.png)

What happens when you fine tune an existing model - does it perform worse on
detecting things that it used to do before the fine tuning dataset? In the
literature this is called [catastrophic forgetting or catastrophic
interference](https://en.wikipedia.org/wiki/Catastrophic_interference). To
mitigate this problem you need to continue to provide data for other
categories that you want detected during the fine tuning (transfer learning)
stage.

When looking for pretrained model, you can search for `model zoo` or
`pretrained models`.

He has a number of different categories: vision, text, tabular, recommendation
systems.

Recommendation systems == collaborative filtering

Recommendation != Prediction


