---
layout: default
title: "How I got started again"
---
This is supposed to be a Hello, World post. I'm going to write down all of the
things that I had to do to get this blog up and running again on Github. There
are a lot of small missteps that I made along the way, and this is my give back
to the community to help document the trail for folks that come after me.

Someday I'll even get my old posts back up and running again. Having complete
control of my content, and how it's published, with no black magic, is really
appealing to me.

## Posts live in the _posts directory, and have a unique front matter

You'll need to create a file using the naming convention `yyyy-mm-dd-post-name`.
Once you have the file created, you'll need to add some front matter to your
post that will be used by Jekyll to ensure that it gets the correct formatting.
In the case of a `post`, you'll need to ensure that you add the following
front-matter to your post. I had added `layout: post` by mistake, which
incidentally is what the [Jekyll documentation](http://jekyllrb.com/docs/posts/)
tells you to do, and you will **get no formatting** for your blog post if you do
this.

I haven't investigated whether this is a problem with the way Github Pages
implements Jekyll yet. This is my suspicion, because of the *magic* that is used
by the [Github Theme
Chooser](https://help.github.com/articles/creating-a-github-pages-site-with-the-jekyll-theme-chooser/)
where all of the theme details are abstracted away from your Github Pages
repository.

```{md}
---
layout: default
title: "Title of your post"
---
```

## You won't get SSL if you use a custom domain

This isn't surprising at all, since you *really* don't want to mess with the
pain that is creating your own real-signed SSL certificate, and installing it.
You _will_ get SSL if you don't mind serving from the Github domain for your
pages, which is `your-github-username.github.io`. 

In the future, I may decide to have a separate SSL landing page for my own
custom domain, and then use that as a _who are you?_ page with a link to my blog
on Github Pages default domain name, which is `https://jflam.github.io`. Note
that this will always redirect to your custom domain if you have the custom
domains feature enabled.