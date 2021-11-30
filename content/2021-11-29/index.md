
+++
title="2021-11-29"
date=2021-11-29
+++

{% block() %}
This is a new post for tomorrow. Placeholder to remind me to fix the timezone
bug that let me create this on 11/28 :smile: **Update:** fixed.
{% end %}

{% block() %}
While learning about Jack Twitter's retirement on HN today, I learned about 
[Fenix](https://apps.apple.com/us/app/fenix-for-twitter/id1437821840) which 
looks like a TweetDeck clone with better aesthetics. It's available for iOS
iPadOS and MacOS.
{% end %}

{% block() %}
To implement the permalink feature in
[vscode-zola](https://github.com/jflam/vscode-zola), I'll need to implement a
stateful `tera` template as described by the
[docs](https://tera.netlify.app/docs/#data-structures). It looks pretty
straightforward.
{% end %}

{% block() %}
[Nix](https://nixos.org/) looks like an interesting tool. I just heard about
it from HN in this [post](https://blog.replit.com/nix-vs-docker) by repl.it
folks talking about Docker vs. Nix.
[Comments](https://news.ycombinator.com/item?id=29387137). The claim is that
Nix does a better job at reproducible builds. Crucially, Nix does not use 
containers, rather it does everything by isolating using environment 
variables. This might be an interesting way to avoid the whole "must install
Docker" thing that holds people back from reproducible environments. The 
repl.it team seems focused on moving from Docker to Nix, and providing 
pacakges via Nix. 

Here's an early [post](https://blog.replit.com/nix) from the repl.it team
describing how they've been migrating away from a single massive Docker image
to using Nix. They make 30,000 packages available in a single 1TB share that
is mounted into every container. Users define a `shell.nix` file that declares
dependencies that are then satisfied by the `nix-shell` tool.
{% end %}
