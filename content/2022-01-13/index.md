+++
title="2022-01-13"
date=2022-01-13
+++

## Multi-Agent Hide and Seek

This is a great _visual_ demonstration of the progress of learning in self-
supervised learning via reinforcement learning. Adding human-like behaviors
to the simulation make it far more engaging to me!

{{ youtube(id="kopoLzvh5jY")}}

The accompanying [Open AI blog
post](https://openai.com/blog/emergent-tool-use/) does a great job of 
annotating the different skills learned along the way. The reward function is
simple: 

> Agents are given a team-based reward; hiders are given a reward of +1 if all
> hiders are hidden and -1 if any hider is seen by a seeker. Seekers are given
> the opposite reward, -1 if all hiders are hidden and +1 otherwise. 

From this simple reward function, many strategies emerge and many surprising
"hacks" where the agents exploit loopholes in the simulation. The section on
Surprising Behaviors shows these clearly.

But given the extremely large number of episodes that lead to the behaviors,
I wonder how they were able to see these behaviors?