---
layout: post
title: "Turtle Rosettes"
date: 2014-05-05
categories: learning python drawing
---

An introduction to Python for new programmers.

### Motivation

I was recently asked to run a programming taster session for a
friend's 7 year old son. Having been a relative latecomer to
programming myself, and entirely self-taught, I was really happy for the
opportunity to share my knowledge with someone so young.

I wanted to choose a language and project that would give us
[instant feedback](http://computinged.wordpress.com/2012/02/21/bret-victors-inventing-on-principle-and-the-trade-off-between-usability-and-learning/)
and allow me to build on simple concepts and combine them into something impressive in less than an hour.

I opted for [Python 2.7](https://docs.python.org/2/) and
[IDLE](https://docs.python.org/2/library/idle.html). Not only was this
a non-intimidating
environment for a new programmer, it also came pre-installed on
the OS X laptop we were using for the day.

### To begin

These instructions assume an Apple latop running OS X.

1. In Finder, go to the Utilites folder
2. Open Terminal
3. Type `idle` at the terminal window
4. Hit return to start idle

![Go to the Utilities folder](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/go-utilities.png)
![Open Terminal](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/utilities-terminal.png)
![Open Terminal](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/terminal-idle.png)


### Turtles all the way

Python comes bundled with the `turtle` package, a library for visualising the
results of your code as drawings on screen.

Before using any library it has to be imported. You can do this by
typing `import turtle` into the Python prompt (the flashing cursor after
the `>>>`) and hitting return.

```python
import turtle
```
![Import Turtle](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/import-turtle.png)

That's all there is to it! Now we can now refer to code in the turtle package.

### Variables

We're going to create a turtle, and we have to give our turtle a name
so we can keep track of them. The name can be anything you like:
`tim`, `zarquon`, `jamesTheGiant`, as long as you keep using the same
name in your program.

We're going to stick with Tim because it's short and easy to type.

```python
tim = turtle.Turtle()
```

This means _"create a new Turtle and assign it to the variable `tim`"_.

### Line dance

Now we have a pet, what can we do with him?

Tim the Turtle already knows how to do lots of things, but today we're
going to make him go forwards and turn right.

```python
tim.forward(100)
```

Can you see he's left behind a trail showing where he's been? If we
send tim around the screen we'll end up with a line drawing of his motion.

### Square dance

Now we have a line, can we make a square?

```python
tim.right(90)
tim.forward(100)
tim.right(90)
tim.forward(100)
tim.right(90)
tim.forward(100)
```

We can, but this is lots of typing! Let's remove the repetition.

### Loops

Loops are a way of saying that we want to run the same code a certain
number of times.

```python
for i in range(4): # Do the following 4 times
    tim.forward(100)
    tim.right(90)
```

Here the `4` means that we want to run `tim.forward(100)` and
`tim.right(90)` four times.

### Nesting

This is excellent, but what if we wanted to draw lots of squares,
rotating a little bit in between? We could nest our loops, putting one
inside the other.

```python
for n in range(8): # Draw 8 squares
    tim.rotate(45)
    for i in range(4):
        tim.forward(100)
        tim.right(90)
```

Hmm. This works but it's starting to get a little hard to read. It would be nice if we
could write code more like how we describe what we want to do: _"I want
to draw 8 squares"_.

### Functions

Functions allow programmers to wrap up code into easy to understand
units, and we can give them names that describe what they do. We've
already been using functions without realising: `forward` and `right`
are functions that are defined for turtles. If we
want to draw a square, we could define a function called `drawSquare`.

```python
def drawSquare():
    for i in range(4):
        tim.forward(100)
        tim.right(90)
```

Once we've defined a function, we can use it just by referring to its
name.

```python
for n in range(8):   # Draw 8 squares
    tim.rotate(45)
    drawSquare()     # We're using our new function!
```

### Function parameters

It's great that we can draw squares now, but what if we want to change
how big they are? Lots of squares all the same size aren't very
exciting.

Fortunately functions can take parameters that control the way they
behave. Just like the numbers we gave to `forward(100)` and
`right(90)` we can define a function parameter called `length` that specifies how
long each side is.

```python
def drawSquare(length):     # Define a parameter called length
    for i in range(4):
        tim.forward(length) # Use the parameter when we draw a side
        tim.right(90)
```

Now we can draw squares in lots of different sizes:

```python
drawSquare(100)
drawSquare(125)
drawSquare(250)
```

### Putting it all together

Download the finished code
[here](https://gist.githubusercontent.com/henrygarner/54bf76a089bcbcaf1636/raw/gistfile1.py). You
can open it in IDLE, and select 'Run Module' from the 'Run' menu to
execute the code without typing it in yourself.

![IDLE Run Module](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/idle-run-module.png)

![Python Turtle Rosette](https://s3-eu-west-1.amazonaws.com/henrygarner.com/assets/images/python-turtle-rosette.png)

Well done Tim!
