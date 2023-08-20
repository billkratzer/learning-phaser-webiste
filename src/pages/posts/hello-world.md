---
layout: '../../layouts/PostLayout.astro'
title: 'Hello World!'
pubDate: 2023-08-06
description: 'Lets build the simplest phaser program!'
author: 'Bill Kratzer'
image:
  url: '/images/blog/macbook_pro_and_coffee.png'
  alt: 'Laptop Cafe image created by Midjourney'
tags: [ "Basics" ]
---

# Overview

In this article, we'll get a simple Phaser project up and running.  

We'll learn how to:  
+ Create a simple HTML page.
+ Include the Phaser libraries.
+ Initialize (and display) a Phaser component on our web page.

# Code

This example simply initializes Phaser and creates a scene that displays the text *Hello World!* in red.

You can run the code by clicking [here](http://examples.learningphaser.com/examples/basic/getting-started).

The source code for this example can be found [here](https://github.com/billkratzer/learning-phaser-examples/tree/main/src/examples/basics/hello-world).

If you cloned the *learning-phaser-examples* project, you can find the source code under **src/examples/getting-started/hello-world**

# A Place for Game

First, we need to create an HTML file for our game.

```html
<html>
    <body>
        <h1>Hello World!</h1>
        
        <div>Our first Phaser game is below!</div>
        <div id="game"></div>
        <div>Thanks for checking this out!</div>
    </body>
</html>
```

This HTML is simple and is not going to win any awards!

The most interesting thing may be the empty `<div>` tag:

```html
<div id="game"></div>
```

This tag is going to be a placeholder for our game.  We will instruct Phaser to place our game into this tag (note the `id="game"` identifier).


# Including Phaser 

Phaser is a web-based gaming framework.  There are several ways to include Phaser in your own project,
but the easiest way to get started is to include it from a website that is dedicated to hosting it, like a Content
Delivery Network (CDN).

Let's include Phaser into our page by loading it directly from a CDN:

```html
<head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/phaser/3.60.0/phaser.min.js" integrity="sha512-YQL0GVx/Too3vZjBl9plePRIYsRnd1s8N6QOvXPdZ+JMH2mtRTLQXGUDGjNW6zr1HUgcOIury67IvWe91oeEwQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
</head>
```

# Initializing Phaser

Once the Phaser library has been included in on the page, we can start writing some Javascript to initialize Phaser!

At the end of the page *body*, we will include the script:

```javascript
<script>
    // Phaser code goes here...
</script>
```

The first thing we must do is configure the Phaser game object.  This object is the root object in Phaser and is the
first thing we must instantiate:

```javascript
let game = new Phaser.Game(config)
```

Note that we initialize phaser and based in a configuration object.

There are a lot of configuration options available, here a few simple ones:

```javascript
var config = {
    type: Phaser.AUTO,
    width: 640,
    height: 480,
    parent: "game",
    scene: {
        create: mainScene
    }
}

let game = new Phaser.Game(config)
```

+ The **width** and **height** parameters define the size of the Phaser Game area, in pixels.
+ The **parent** option designates where the game will be inserted into the page.  Here, we specify *game*.  This happens to be the id of the main game `<div>` tag that we specified earlier.

Every Phaser Game must have at least one scene (we'll explain scenes later).  Our starting scene will be created by a function named `mainScene`.

This function contains the code to initialize the content on the game screen.  In this case, we are going to start pretty simple
ane simply add some red text that says *Hello World!*.

```javascript
function mainScene() {
    let text = this.add.text(320, 240, "Hello World!", {
        color: "#f55",
        fontFamily: "sans-serif",
        fontSize: "32px",
        fontStyle: "bold"
    })
    text.setOrigin(0.5, 0.5)
}
```