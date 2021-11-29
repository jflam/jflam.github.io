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

Specialized Tarmac vs. Epic showdown:

{{ instagram(id="CW1lrUvvSry")}}