+++
title="2022-01-06"
date=2022-01-06
+++

## Optimizing Docker image size

There's a nice [blog on optimizing Docker image
size](https://contains.dev/blog/optimizing-docker-image-size). I learned about
tools that I haven't known about before, especially
[dive](https://github.com/wagoodman/dive). This lets you troubleshoot your 
Docker images and even tells you when you have files duplicated in different
layers in your image. It's a great way to discover waste in your images.

![Animated gif showing
dive](https://github.com/wagoodman/dive/blob/master/.data/demo.gif?raw=true)

The [HN thread](https://news.ycombinator.com/item?id=29828386) also has a
bunch of useful tips for managing layers:

You can use `--squash` to remove all intermediate layers

The [Docker BuildKit tool supports
heredocs!](https://www.docker.com/blog/introduction-to-heredocs-in-dockerfiles/)

```bash
RUN <<EOF
apt-get update
apt-get upgrade -y
apt-get install -y ...
EOF
```

There's a tool called `stargz` (seekable tar.gz format) which greatly improves
startup time in container images by lazy loading files [stargz
snapshotter](https://github.com/containerd/stargz-snapshotter)

Look at how it improves startup time for python-3.7 image:

![](2022-01-06/2022-01-06-19-02-52.png)

This [FOSDEM 2021 presentation is a good overview of
stargz](https://archive.fosdem.org/2021/schedule/event/containers_lazy_pull/attachments/slides/4687/export/events/attachments/containers_lazy_pull/slides/4687/stargz_snapshotter.pdf)

This is built on top of the [Google CRFS](https://github.com/google/crfs)
(Container Registry Filesystem) project which is a FUSE filesystem that lets
you mount a container image served directly from a container registry without
pulling it locally first. The linked repo has a fantastic README that explains
how it all works.