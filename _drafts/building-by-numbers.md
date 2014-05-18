---
layout: post
title: "Building by Numbers"
date: 2014-05-11
categories: python minecraft learning
---

Last time we looked at how we could program tim the turtle to make
shapes on screen. Today we'll use Python and some new functions to
'draw' a house in Minecraft.

### Setting up Minecraft

To begin with, you'll need to have set up Minecraft to work with
Python. This requires Minecraft: Pi Edition, designed to run on the
Raspberry Pi. If you don't have a Raspberry Pi, you can still control
Minecraft on your own computer but you need to download a special
version. The instructions for doing this on several platforms are
[here]().

### Algorithms

A [algorithm](http://computer.howstuffworks.com/question717.htm) is a
fancy way of saying 'a list of instructions'. Computer algorithms are
lists of instructions that you can tell a computer to follow
to get them to do things. Algorithms can be quite simple, such as
how to sort things in order, or very complicated such as how to
recognise handwriting.



### Making squares

Last time we got Tim to make squares by telling him to go forwards and
turn right four times. This is a very simple algorithm.

There isn't a turtle in Minecraft, so we have to express our algorithm
in a different way.

Minecraft is based around blocks, all of which have a position in
3-dimensional space.

The way blocks are represented in 3D is as as 3 numbers, which are the
coordinates in each direction.


### Connecting to Minecraft

Just as when we wanted to work with turtles, and we called `import
turtle`, we do the same for minecraft.


`from mcpi.minecraft import Minecraft`


Next we want to connect to the game that's running, so we create link
to the game server.

```python
mc = Minecraft.create()
```

### Hello Minecraft

Now that you have a reference to a Minecraft game, you can interact
with it. One of the things you can do is post a message to players of
the game.

```python
mc.postToChat("Hello Minecraft!")
```

You should see a message show up like the image below.

### Where am I?

We can also query for aspects of the game. Since
we want to build a home near to where we're currently standing, we
need to know the player's current position.

We can get this in the following way.

```python
mc = Minecraft.create()
pos = mc.player.getTilePos()
```

This returns `Vec3`, which is provided by the minecraft package and
contains 3 numbers - the coordinates of the player in each of the
three dimensions. These are labelled x, y and z.

### Coordinates

```python
while True:
	pos = mc.player.getTilePos()
	mc.postToChat(str(pos.x) + " " + str(pos.y) + " " + str(pos.z))
```
As you walk around, you should see the numbers change. They always
represent you current position. You can use these numbers when you
want to build something nearby.

Because the loop will continue forever, you have to cancel the code in
IDLE. Go to the `Shell` menu and select `Restart Shell`.

### Setting blocks

In addition to posting messages to the game, you can also edit the
landscape itself, by adding and removing blocks.

This time, rather than print the position to the game as a message, we
can use the position to convert blocks near the player to something
else.

The following code converts the block underneath the player to
gold.

```python
while True:
    pos = mc.player.getTilePos()
    mc.setBlock(pos.x, pos.y - 1, pos.z, block.GOLD_BLOCK)
```
The reason we say `pos.y - 1` is because when we remove 1 from y, we
get the position of the block underneath us.


### Creating shapes

We can create 3D shapes by changing the x, y, and z values when we set
blocks. We can do this inside nested loops, similar to how we
controlled the turtle before.

This time we can have 3 nested loops, one for each of the 3
dimensions.

```python
from mcpi.minecraft import Minecraft
import mcpi.block as block

mc = Minecraft.create()
pos = mc.player.getTilePos()

for x in range(5):
    for y in range(5):
        for z in range(5):
            mc.setBlock(pos.x + x, pos.y + y, pos.z + z, block.GOLD_BLOCK)
```

### Making a house

Now that we have a cube, the only thing we have to do to make a house
is make it hollow.

We can do this by controlling whether we set a block or not within the
loop. The only times we want to draw blocks are when we're at the
edges. Everything in the middle can be turned to air.


### Putting it all together

[Download code](https://gist.githubusercontent.com/henrygarner/7799e8176c57884b880b/raw/18aaed73900d3ef97d5be54f899daf3d8a4eb72b/building.py)


