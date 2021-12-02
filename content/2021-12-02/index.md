+++
title="2021-12-02"
date=2021-12-02
+++

{% block() %} 

Today's morning read is a wonderful essay that hit the top of
[HN](https://news.ycombinator.com/item?id=29416606) titled [100 years of
whatever this will be](https://apenwarr.ca/log/20211201). The key thing that
[Avery Pennarun](https://www.linkedin.com/in/apenwarr/) talks about is the
importance of centralized regulation in distributed systems. He also talks
about just how hard it is to build a reliable distributed system from his
perspective of being the co-founder of [TailScale](https://tailscale.com/). He
also evokes (with lots of examples) the observation that decentralized markets
trend towards chaos over time and why it's important to centrally regulate
them.

> The job of regulation is to stop distributed systems from going awry.
> Because distributed systems always go awry.

He references another essay [The Tyranny of
Structurelessness](https://www.jofreeman.com/joreen/tyranny.htm) that says
"if you don't have an explicit hierarchy you have an implicit one" and then
brilliantly applies it to look at why your distributed system can fail.

The rant about technology at the start is awesome as well, an example:

> IT security has become literally impossible: if you install all the patches,
> you get SolarWinds-style supply chain malware delivered to you
> automatically.  If you don't install the patches, well, that's worse. Either
> way, enjoy your ransomware. 

Worth noting that this is a thinly veiled takedown of the DeFi and crypto
movements in general and he accuses them of making handwavy arguments around
the reliability of those systems ("it's decentralized so it can't fail!")

Go read it. I'll wait.
{% end %}

{% block() %}
I'm really happy with rebooting this blog using Cloudflare Pages. In an
attempt to build a more interesting site with interactive content (e.g.,
embedded YouTube videos, Twitter and Linked in blocks etc.) I've found that
the size of the site (and the bloated-ness) of the site has increased
dramatically. It's 100% due to how I'm using JavaScript to embed those
external services. This is a
[report](https://tools.pingdom.com/#5f5f1784e7c00000) that I just ran this
morning:

TODO: paste the image

I think that in the future, I need to teach `vscode-zola` how to embed
an image of, say the YouTube video, the Twitter post or the Instagram post
with a link to the original instead of doing these crazy embeddings. The 
fact that my web page is 6.4MB is _inconceivable_.
{% end %}