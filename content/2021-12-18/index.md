+++
title="2021-12-18"
date=2021-12-18
+++

{% block() %} Tim O'Reilly, one of our elder statesmen of the web, has written
a great [analysis article on
Web3](https://www.oreilly.com/radar/why-its-too-early-to-get-excited-about-web3/).
It is well worth reading the post in its entirety, as he does a really good
job at constructing arguments without being confrontational in his reasoning.
he does this by asking questions without presuming what the answers are. This
is probably the most balanced account of Web3 that I've read so far and well
worth your time. {% end %}

{% block() %}
I've been thinking a lot about the parallels between liquid chromatography and
espresso making. I found this [article that delves into both the chemistry and
physics of espresso
brewing](https://www.chemistryviews.org/details/ezine/694285/Espresso__A_Three-Step_Preparation.html).

{% end %}

{% block() %}
While looking around for a project for the holidays, I've started thinking
about continuing to build my personal semantic search engine. The core idea is
to make a tool that makes it easier to remember and recall things that are
interesting to me. Part of that is searching my private data for things that
are interesting. I've already made pretty good progress in August on this. The
other part is building a browser extension that makes it easy to tag and take
notes on things that I'm reading and add those things to the index that my
search engine operates over. That feels like a good task for the holidays.
{% end %}

{% block() %}
I've also been interested in autonomous agents for helping to manage 
beer mode information. My gut tells me that these things likely won't help
in the long run, but they are nevertheless interesting to me. There are two
tools that I came across tonight:

1. [mailbrew](https://mailbrew.com/) which is a service for delivering news
   culled by agents that you configure into an email that shows up in your
   inbox. This is pretty interesting as a tool as it lets you aggregate
   different pieces of information into a personal newsletter. It's $5/month
   which is also pretty reasonable.
1. [huginn](https://github.com/huginn/huginn) which is named after the crows
   Huginn and Muninn who sat on Odin's shoulders and told him the news of the
   world. This is kind of like a DIY mailbrew where all the information sits
   on a server that you get to run it on. It's a DAG of agents (all written in
   Ruby) that you can configure to do virtually anything. It also runs as a 
   Docker container to save you the trouble of setup. This feels like a lot of
   work compared to mailbrew.

{% end %}

{% block() %}
I found a way to split an MP3 into smaller files automatically using ffmpeg.
This is also the first time that I've ever used `ffmpeg` before and it did 
a fantastic job on this task.

`$ ffmpeg -i somefile.mp3 -f segment -segment_time 3 -c copy out%03d.mp3`

[source](https://unix.stackexchange.com/questions/280767/how-do-i-split-an-audio-file-into-multiple)
{% end %}