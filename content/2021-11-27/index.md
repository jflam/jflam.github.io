+++
title="2021-11-27"
date=2021-11-27
+++

{% block() %}
Hello [Zola](https://www.getzola.org/documentation/templates/overview/) supports the
[Tera](https://tera.netlify.app/) templating engine. Today I'm going to update
the way my blog renders by rendering in a continuous style much like how Dave
Winer's [Scripting.com](https://www.scripting.com) site works. I like the
layout, and I'm hoping to build something out that looks more like this.

I updated it to use two open source fonts from Google:
[Oswald](https://fonts.google.com/specimen/Oswald) for headings and
[Ubuntu](https://fonts.google.com/specimen/Ubuntu) for body text. 

This is what Oswald looks like:

{{ image(src="2021-11-27/2021-11-27-16-33-22.png" width=500) }}

This is what Ubuntu looks like:

{{ image(src="2021-11-27/2021-11-27-16-36-38.png" width=500) }}
{% end %}

{% block() %}
To make this really work, it's going to need tooling, as there is quite a bit
of friction today. The VS Code extension will need to preview output using
`zola`. It will also need to analyze clipboard formats and generate
appropriate markup as well. When using `zola serve` to render the page, the
browser window does an auto-refresh of the page when the contents are 
re-rendered (not quite sure how this happens, but it's cool). Ideally what 
I do is render that instead of the Markdown Preview pane that VS Code uses
today.

If there is an image on the clipboard, much like the `Paste Image` extension
that I'm currently using, it will need to generate some appropriate markup
that, roughly speaking looks like with the following escaped by the `tera`
markup charcters:

```
image(src="POST-DIRECTORY/GENERATED-NAME.PNG", width=500)
```

The extension will also examine URIs pasted to the clipboard, e.g., from 
YouTube or Twitter, and paste the appropriate shortcodes for those URIs.

So there are a few things that I need to learn:

1. How to examine the contents of the clipboard in a cross-platform way so
   that I can serialize binary data for an image into a file.
2. Have a generic extension that understands how to expand templates based
   on pattern matches for URIs and uses a template engine to generate text 
   that is pasted into the app.

{% end %}