+++
title="2021-11-26"
date=2021-11-26
+++

{% block() %}
I'm journaling the start of a new blog that I'm writing using VS Code as my
editor, some extensions and the `zola` markdown engine. The idea is to build
something that looks like Dave Winer's Scripting.com to let me easily write
stream of consciousness [Beer
Mode](https://perell.com/note/open-mode-and-closed-mode/) observations.

To commemorate this, I've captured a screenshot of the VS Code project that
contains this first post:

{{ image(src="2021-11-26/2021-11-26-20-01-27.png" width=200)}}

The only thing that's annoying about how this works today is that I need to
use raw HTML if the captured image needs to be resized for aesthetics. Below
is an example of what I need to type in the raw HTML format. I think I'm going
to need to write a VS Code extension to streamline this process to let me more
easily fine-tune the appearance of images.

```html
<img src="2021-11-26/2021-11-26-20-01-27.png" width=200>
```
{% end %}

{% block() %}
I'm using the [Paste Image](https://marketplace.visualstudio.com/items?itemName=mushan.vscode-paste-image)
VS Code extension to make it easier to insert images into each post.

I tried GitHub pages and Jekyll, but forcing images into a global `/assets`
directory is a non-starter. 

After some research, I decided to use use
[zora](https://github.com/getzola/zola) which is a much better choice as it
gives me the flexibility to include content in simple directory structures,
i.e., pasted images can be in the same directory as the markdown option.

Next, I need to figure out how to include `zola` in a custom 

Another image:

![](2021-11-26/2021-11-26-23-24-30.png)
{% end %}

{% block() %}
This is quite possibly the best YouTube video that explains how F1 Cars work.
He builds a [Blender](https://www.blender.org/) model of the car and proceeds
to show airflow dynamics, suspension operation, motor details (and how the
turbocharger works), how the hybrid MGU-K and MGU-H systems work and much
more. Easily the best video explainer for F1 cars that I've seen!

{{ youtube(id="V7707zEX9X4")}}
{% end %}

{% block() %}
Today more scary information was being published about the new omicron
(&omicron;) variant. There are 15 mutations in the receptor binding domain of
the spike protein.

{{ twitter(id="1464452102382448643")}}
{% end %}

{% block() %}
:bulb: There's probably a `zola` VS Code extension waiting to be written that
will do things like take a copied YouTube or Twitter URI and turn it into
one of the shortcodes in this repository. I think that the extension should
also start a background `zola` process that will render the preview in place
of the existing VS Code markdown preview. Finally, it should have a feature
that will generate the appropriate GitHub Actions to publish to GitHub pages
after pushing to the remote.
{% end %}