---
layout: post
title:  "Blockbuster: Minecraft Movies"
date:   2014-07-01
categories: clojure minecraft graphics
---

Taking the current obsession for 3D film to its illogical
conclusion. I demonstrate the Redstone Clojure interface to Minecraft
via pixels, voxels, obsolete image formats and coloured wool.

![Blockbuster: Minecraft Movies](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/blockbuster.jpg)

### Blockbuster Presentation

I
[gave a talk](https://skillsmatter.com/skillscasts/5406-blockbuster-minecraft-movies)
at the [London Clojurians](http://londonclojurians.org/) July 2014
meetup about the work I'd been doing on
[Blockbuster](https://github.com/henrygarner/blockbuster), a
command-line  tool for rendering images and movies in Minecraft using coloured
wool blocks. This was also an opportunity to introduce
[Redstone](https://github.com/henrygarner/redstone), the library that
handles communication with the Minecraft server.


A
[video of the talk](https://skillsmatter.com/skillscasts/5406-blockbuster-minecraft-movies)
was recorded, or you can
[read the slides](https://github.com/henrygarner/ldnclj-talk-july-2014/blob/master/talk.org)
as an .org file. 

### Prerequisites

You will need to have [imageMagick and ffmpeg](http://brew.sh)
installed, and you will need to be running a
[Craftbukkit server with the RaspberryJuice plugin](http://blog.lostbearlabs.com/2013/04/25/using-the-minecraft-api-without-a-raspberry-pi-craftbukkit-and-raspberryjuice/).

On OS X `imageMagick` and `ffmpeg` can be installed through
[homebrew](http://brew.sh) in the following way:

```sh
brew install imagemagick
brew install ffmpeg
```

### Download

You'll need to have [Leiningen](http://leiningen.org/) installed to compile the code. Download [Blockbuster](https://github.com/henrygarner/blockbuster) and run
`lein compile` in the project directory.


### Usage

The following will draw movie.mov on a screen 50 blocks wide. The
height will be determined by the aspect ratio of the file.

```sh
bin/blockbuster -f [path/to/movie.mov] -w 50
```

### Options

The application accepts the following arguments:

```sh
-f "The movie file to play"
-w "The width of the screen"
-p "The x,y,z coordinates of the screen"
-n "Draw every n frames"
-m "The number of milliseconds to wait between frames"
-c "Whether space should be cleared for the screen"
```

### How does it work?

The application uses `ffmpeg` to separate movie files into sequences of
still images. Each image is then resized and interpreted as a .ppm
file using imageMagick's `convert` utility. A .ppm file is a
text-based format that's easy to parse into a stream of r,g,b pixel
values. Each of these pixels is compared against the 16 available wool block
colours to find the closest match and then drawn in the
specified location using the
[redstone](http://github.com/henrygarner/redstone) library.
