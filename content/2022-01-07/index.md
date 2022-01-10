+++
title="2022-01-07"
date=2022-01-07
+++

## GPT-3 and long form question answer by OpenAI

Note to myself: today Dickie Bush reminded me of the Pixar Storytelling
framework. I'm going to try rewriting this post that way to see if it's
any better at telling the story.

{{ twitter(id="1479450845087518721")}}

Today's paper is [WebGPT: Browser-assisted question-answering with human
feedbac](https://arxiv.org/pdf/2112.09332.pdf). When I think about thow we can
build a [bicycle for the
mind](https://medium.learningbyshipping.com/bicycle-121262546097), I've been
wondering how machine learning can help and mused about as much while
wondering if it is possible to create a
[Tim (Urban)-In-A-Box](https://www.iunknown.com/2022-01-02/). More important
than summarizing or finding information is _getting you to read that summary_.

There are a number of things that I learned in this paper. First is that there
is a high quality dataset, [ELI5](https://facebookresearch.github.io/ELI5/)
sourced from the popular
[sub-reddit](https://www.reddit.com/r/explainlikeimfive/) that contains a list
of questions and answers "explained like I am 5 years old".

![](2022-01-07/2022-01-07-08-20-57.png)

I learned about [crows](http://archives.wbur.org/thewildlife/2015/03/12/the-secrets-of-gift-giving-crows/)

## Pixar version

Once upon a time, the Internet was a place where I would __manually__ do
research, often times on the toilet. Every day I would click on links, often
times on social media, and read post after post after post, slowly building up
a mental model of the __things__ I am researching. 

But if I rely on [beer
mode](https://perell.com/note/open-mode-and-closed-mode/) activities to drive
my research, it's going to be pretty random. And since there isn't anything
that tries to tie together the things that I have seen on a particular topic,
my poor brain is left to fend for itself. So it sees input that looks
something like:

- GPT-3 paper
- GPT-3 funny meme
- Picture of cat
- Shitpost from friend on Twitter
- OMG COVID will kill us all
- Spiderman spoiler
- Introduction to Transformers
- Transformers: Dark side of the mooon trailer
- Attention is all you need paper

But one day, I thought: why don't I get my machines to go do the heavy beer
mode activity of sifting through the Internet and return me something that I
could read without distractions, preferrably written in a [Tim
Urban](https://waitbutwhy.com/) style? Just how far-fetched is this idea?
Turns out, we're getting closer by the day.

On December 16, [OpenAI announced
WebGPT](https://openai.com/blog/improving-factual-accuracy/), which is a 
fine-tuned version of GPT-3 that answers open-ended questions by searching
for and summarizing what it finds online. Unlike GPT-3, WebGPT augments what
is already known in its language model with results obtained by searching
the web using the Bing search API.

The results from the model are pretty interesting. When posed the question:
"How do neural networks work?", WebGPT responded with:

> In its most basic form, a neural network has two layers: an input layer and
> an output layer[3]. The output layer is the component of the neural network
> that makes predictions[3]. In a feedforward network, information flows
> through the network in the following way: patterns of information are fed
> into the network via the input units, which trigger the layers of hidden
> units, and these in turn arrive at the output units[1]. The network learns
> by a feedback process called backpropagation, which involves comparing the
> output a network produces with the output it was meant to produce, and using
> the difference between them to modify the weights of the connections between
> the units in the network, working from the output units through the hidden
> units to the input units, going backward[2][4]. Over time, backpropagation
> causes the network to learn, reducing the difference between actual and
> intended output to the point where the two exactly coincide, so the network
> figures things out exactly as it should[2].

This is pretty reasonable! It even generated references:

1. How neural networks work - A simple introduction (www.explainthatstuff.com) 
2. How neural networks work - A simple introduction (www.explainthatstuff.com) 
3. How Do Neural Networks Really Work? | Nick McCullum (nickmccullum.com) 
4. How Do Neural Networks Really Work? | Nick McCullum (nickmccullum.com) 

The linked [paper](https://arxiv.org/pdf/2112.09332.pdf) provides a lot of
additional details. First, the experimental environment (used by humans
recruited via UpWork) is a text-based web browser. Here's a screenshot of what
it looks like:

![text based browser used by webgpt humans](2022-01-07/2022-01-07-08-20-57.png)

The text based browser was designed to be used by human participants, and did
a lot that a conventional browser does not typically do to make it easier to
work with the text. It uses a number of existing libraries, including:

- [readability.js](https://github.com/mozilla/readability)
- [html2text](https://github.com/aaronsw/html2text)
- [pdfminer.six](https://github.com/pdfminer/pdfminer.six)

to transform the text into a format that was suitable to feed into the model.
The browser was used to collect two additional pieces of data from the study
participants: 1) demonstrations of humans using search to answer questions,
and 2) comparisons between two model-generated answers to the same question.

The model itself was trained to answer questions from the
[ELI5](https://facebookresearch.github.io/ELI5/) dataset that was gathered
from questions and answers in the "Explain Like I'm Five" subreddit. 

The results from this study are encouraging - the model's answers are
preferred 56% of the time. When comparing answers to the highest-voted 
answer from the ELI5 dataset, the model's answers were preferred 69% of the
time. This is not human-level performance yet, but it's getting there.

Because of this, 
Because of this,

Until finally the glorious day arrives when I can ask a question like: 

> Have Tim Urban write an explainer for What is Neuralink and why do we need
> it?

And I get an answer like [this amazing 38,000 word explainer for my
question](https://waitbutwhy.com/2017/04/neuralink.html). Or if I'm more in
the mood for something more succinct:

> Give me a Wikipedia summary for What is Neuralink and why do we need it?

But will it make any difference? Will it actually make people smarter? Think
better? Will this insulate us from the endless distraction that is the
internet? 

Maybe what we need is an assistant that filters the web for us but in a way
that doesn't reinforce existing biases? I should write about that some other
time.

## Brian Kernighan's memoir

TIL that [UNIX: A History and a
Memoir](https://www.amazon.com/UNIX-History-Memoir-Brian-Kernighan-ebook/dp/B07ZQHX3R1)
was written by [Brian Kernighan](https://www.cs.princeton.edu/~bwk/) and
available on Kindle as an e-book.