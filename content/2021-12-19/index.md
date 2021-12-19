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
