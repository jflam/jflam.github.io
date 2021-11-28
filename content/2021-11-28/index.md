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

{{ youtube(id="rgHEmK2mE7Q")}}

{{ twitter(id="1462284494258405384")}}

{{ youtube(id="NTfOnGZUZDk")}}

{{ instagram(id="CW1lrUvvSry")}}