+++
title="2021-11-28"
date=2021-11-28
+++

Writing a VS Code extension requires understanding how activation works and
where state is stored. The [Activation
Events](https://code.visualstudio.com/api/references/activation-events) page
in the documentation has a good explanation of how it works. The default
sample uses only the `onCommand` event binding which is not what I need for my
extension (and actually caused me quite a lot of confusion).

Instead, I really need to have it activate when a workspace contains a zola
blog. the `workspaceContains` event uses a glob pattern to look for a file of
interest. I think that `**/*.config.toml` is probably good enough for now, and
I could even not activate the extension if I find that it doesn't have the
right parameters inside the file.

`vscode-zola` now supports emitting shortcodes based on URIs copied from the
clipboard. For most cases where I copy a URI for YouTube, Twitter, or 
Instagram content, the extension will emit the proper `zola` shortcodes and 
embed the content within the page, giving a much nicer rendering experience
for the reader.

Here's a This Triathlon Life YouTube video that I watched earlier today. 
Eric and Laura are like characters in a TV show that I watch regularly, usually 
when I'm riding my bike on the trainer:

{{ youtube(id="rgHEmK2mE7Q")}}

Charlie's moved on from Redmond and he's got a temporary home for his cars:

{{ twitter(id="1462284494258405384")}}

I didn't know this history of grep before - these kinds of stories are what
make YouTube great:

{{ youtube(id="NTfOnGZUZDk")}}

Paula vs. Eric in a Specialized Tarmac vs. Epic showdown:

{{ instagram(id="CW1lrUvvSry")}}

After running this blog on GitHub pages over the weekend, I decided to try
something new and created a [CloudFlare](https://cloudflare.com) account.
While I was having some troubles with GitHub pages occassionally not rendering
correctly (something with the DNS entries not being happy with GitHub), I was
more curious about CloudFlare and wanted to try being a customer. So I signed
up for the free plan.

There's an interesting gateway drug effect with CloudFlare. After getting a
free account and using it to protect this blog on GitHub pages, I learned that
I could transfer my domain over to CloudFlare from GoDaddy, the registrar that
I've been using for the past decade or so. I was attracted by the wholesale
cost pricing of CloudFlare which worked out to less than $9/year to continue
to manage my `iunknown.com` domain (which is now 24 years old!) So I went and
initiated the transfer process tonight.

I was also curious about JamStack and [CloudFlare
Pages](https://blog.cloudflare.com/cloudflare-pages-is-lightning-fast/). It
turns out that there's also [built-in support for
Zola](https://developers.cloudflare.com/pages/framework-guides/deploy-a-zola-site)
as well. After some misadventures with version numbers (as of this writing,
the only supported version is 0.14.0), I finally got builds up and running.

The experience is identical to GitHub Actions and GitHub Pages - I push to my
`main` branch, and the installed CloudFlare Pages GitHub app handles the build
and deployment process into the CloudFlare network. The only thing I noticed
is that the container(?) that is used to build takes a long time to initialize
compared to GitHub Actions. When I look at the logs, it seems like this
container is used not just by `zola` but it installs other static web site
generators like `Hugo` as well. 

I've got a working version of my first VS Code extension,
[vscode-zola](https://github.com/jflam/vscode-zola). I'm using it to write
this post now. So far, it supports:

* Creating a new post
* Pasting social media URIs and embedding them in the generated page
* A sort-of working Preview Blog service

I'm a bit torn about how the Preview Blog service should behave - right now
I'm imagining that it will work like the way VS Code Markdown Preview works - 
creating a new pane to the right of the editor that shows the preview with a 
hot-reload function that refreshes every time you save the markdown file. The
existing `zola serve` command works and does auto-refresh in an external 
browser window too, and it already supports hot reloading. 

Some future features that I want to add include:

* Paste image functionality similar to how the [Paste
  Image](https://marketplace.visualstudio.com/items?itemName=mushan.vscode-paste-image)
  extension works today, but tailored to how my `zola` blog's needs (specially
  formed URIs and using the image shortcode).
* Section permalink - another command that inserts some markdown into the post
  that generates a # (typically at the end of a logical section) which is also
  a permalink that users can use to link directly to that part of the post.
  This is how `Scripting News` works and I want to make it easy to do so using
  nothing more than plain-vanilla markdown.