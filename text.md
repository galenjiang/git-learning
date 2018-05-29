# 用于测试

Learning Pixi
=============

A step-by-step introduction to making games and interactive media with
the [Pixi rendering engine](https://github.com/pixijs/pixi.js). **[Updated for Pixi v4.5.5](https://github.com/pixijs/pixi.js/releases/tag/v4.5.5)**. [Chinese version here: Pixi官方教程中文版](https://github.com/Zainking/learningPixi). If you like this
tutorial, [you'll love the book, which contains 80% more content!](http://www.springer.com/us/book/9781484210956).

catalog

### Table of contents:
1. [Introduction](#introduction)
2. [Setting up](#settingup)
  1. [Installing Pixi](#installingpixi)
3. [Creating the stage and renderer](#application)
4. [Pixi sprites](#sprites)
5. [Loading images into the texture cache](#loading)
6. [Displaying sprites](#displaying)
  1. [Using Aliases](#usingaliases)
  2. [A little more about loading things](#alittlemoreaboutloadingthings)
    1. [Make a sprite from an ordinary JavaScript Image object or Canvas](#makeaspritefromanordinaryjavascriptimageobject)
    2. [Assigning a name to a loaded file](#assigninganametoaloadingfile)
    3. [Monitoring load progress](#monitoringloadprogress)
    4. [More about Pixi's loader](#moreaboutpixisloader)
7. [Positioning sprites](#positioning)
8. [Size and scale](#sizenscale)
9. [Rotation](#rotation)
10. [Make a sprite from a tileset sub-image](#tileset)
11. [Using a texture atlas](#textureatlas)
12. [Loading the texture atlas](#loadingatlas)
13. [Creating sprites from a loaded texture atlas](#creating-sprites-from-a-loaded-texture-atlas)
14. [Moving Sprites](#movingsprites)
15. [Using velocity properties](#velocity)
16. [Game states](#gamestates)
17. [Keyboard Movement](#keyboard)
18. [Grouping Sprites](#grouping)
  1. [Local and global positions](#localnglobal)
  2. [Using a ParticleContainer to group sprites](#spritebatch)
19. [Pixi's Graphic Primitives](#graphic)
  1. [Rectangle](#rectangles)
  2. [Circles](#circles)
  3. [Ellipses](#ellipses)
  4. [Rounded rectangles](#rounded-rectangles)
  5. [Lines](#lines)
  6. [Polygons](#polygons)
20. [Displaying text](#text)
21. [Collision detection](#collision)
  1. [The hitTestRectangle function](#the-hittestrectangle-function)
22. [Case study: Treasure Hunter](#casestudy)
  1. [Initialize the game in the setup function](#initialize)
    1. [Creating the game scenes](#gamescene)
    2. [Making the dungeon, door, explorer and treasure](#makingdungon)
    3. [Making the blob monsters](#makingblob)
    4. [Making health bar](#healthbar)
    5. [Making message text](#message)
  2. [Playing the game](#playing)
  3. [Moving the explorer](#movingexplorer)
    1. [Containing movement](#containingmovement)
  4. [Moving the monsters](#movingmonsters)
  5. [Checking for collisions](#checkingcollisions)
  6. [Reaching the exit door and ending game](#reachingexit)
23. [More about sprites](#spriteproperties)
24. [Taking it further](#takingitfurther)</br>
  i.[Hexi](#hexi)</br>
  ii.[BabylonJS](#babylonjs)</br>
25. [Supporting this project](#supportingthisproject)

<a id='introduction'></a>
Introduction
------------

Pixi is an extremely fast 2D sprite rendering engine. What does that
mean? It means that it helps you to display, animate and manage
interactive graphics so that it's easy for you to make games and
applications using
JavaScript and other HTML5 technologies. It has a sensible,
uncluttered API and includes many useful features, like supporting
texture atlases and providing a streamlined system for animating
sprites (interactive images). It also gives you a complete scene graph so that you can
create hierarchies of nested sprites (sprites inside sprites), as well
as letting you attach mouse and touch events directly to sprites. And,
most
importantly, Pixi gets out of your way so that you can use as much or
as little of it as you want to, adapt it to your personal coding
style, and integrate it seamlessly with other useful frameworks.

Pixi’s API is actually a refinement of a well-worn and battle-tested
API pioneered by Macromedia/Adobe Flash. Old-skool Flash developers
will feel right at home. Other current sprite rendering frameworks use
a similar API: CreateJS, Starling, Sparrow and Apple’s SpriteKit. The
strength of Pixi’s API is that it’s general-purpose: it’s not a game
engine. That’s good because it gives you total expressive freedom to make anything you like, and wrap your own custom game engine around it.

In this tutorial you’re going to find out how to combine Pixi’s
powerful image rendering features and scene graph to start making
games. But Pixi isn't just for games - you can use these same
techniques to create any interactive media applications. That means
apps for phones!

What do you need to know before you get started with this tutorial?

You should have a reasonable understanding of HTML and
JavaScript. You don't have to be an expert, just an ambitious beginner
with an eagerness to learn. If you don't know HTML and JavaScript, the
best place to start learning it is this book:

[Foundation Game Design with HTML5 and JavaScript](http://www.apress.com/9781430247166)

I know for a fact that it's the best book, because I wrote it!

There are also some good internet resources to help get you started:

[Khan Academy: Computer
Programming](http://www.khanacademy.org/computing/cs)

[Code Academy:
JavaScript](http://www.codecademy.com/tracks/javascript)

Choose whichever best suits your learning style.

Ok, got it?
Do you know what JavaScript variables, functions, arrays and objects are and how to
use them? Do you know what [JSON data
files](http://www.copterlabs.com/blog/json-what-it-is-how-it-works-how-to-use-it/)
are? Have you used the [Canvas Drawing API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Drawing_graphics_with_canvas)?

To use Pixi, you'll also need to run a webserver in your root project
directory. Do you know what a webserver is and
how to launch one in your project folder? The best way is to use
[node.js](http://nodejs.org) and then to install the extremely easy to use
[http-server](https://github.com/nodeapps/http-server). However, you need to be comfortable working with the Unix
command line if you want to do that. You can learn how to use
Unix [in this
video](https://www.youtube.com/watch?feature=player_embedded&v=cX9ASUE3YAQ)
and, when you're finished, follow it with [this
video](https://www.youtube.com/watch?v=INk0ATBbclc). You should learn
how to use Unix - it only takes a couple of hours to learn and is a
really fun and easy way to interact with your computer.

But if you don't want to mess around with the command line just yet, try the Mongoose
webserver:

[Mongoose](http://cesanta.com/mongoose.shtml)

Or, just write your all your code using the excellent [Brackets text
editor](http://brackets.io). Brackets automatically launches a webserver
and browser for you when you click the lightning bolt button in its
main workspace.

Now if you think you're ready, read on!

(Request to readers: this is a *living document*. If you have any
questions about specific details or need any of the content clarified, please
create an **issue** in this GitHub repository and I'll update the text
with more information.)

<a id='settingup'></a>
Setting up
----------

Before you start writing any code, create a folder for your project, and launch a
webserver in the project's root directory. If you aren't running a
webserver, Pixi won't work.

Next, you need to install Pixi. 

<a id='installingpixi'></a>
### Installing Pixi

The version used for this introduction is **v4.5.5**
and you can find the `pixi.min.js`  file either in this repository's `pixi` folder or on [Pixi's release page for v4.5.5](https://github.com/pixijs/pixi.js/releases/tag/v4.5.5).
Or, you can get the latest version from [Pixi's main release page](https://github.com/pixijs/pixi.js/releases).

This one file is all you need to use Pixi. You can ignore all the
other files in the repository: **you don't need them.**

Next, create a basic HTML page, and use a
`<script>` tag to link the
`pixi.min.js` file that you've just downloaded. The `<script>` tag's `src`
should be relative to your root directory where your webserver is
running. Your `<script>` tag might look something like this:
```html
<script src="pixi.min.js"></script>
```
Here's a basic HTML page that you could use to link Pixi and test that
it's working. (This assumes that the `pixi.min.js` is in a subfolder called `pixi`):

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Hello World</title>
</head>
  <script src="pixi/pixi.min.js"></script>
<body>
  <script type="text/javascript">
    let type = "WebGL"
    if(!PIXI.utils.isWebGLSupported()){
      type = "canvas"
    }

    PIXI.utils.sayHello(type)
  </script>
</body>
</html>
```

If Pixi is linking correctly,
something like this will be displayed in your web browser's JavaScript console by default:
```
      PixiJS 4.4.5 - * canvas * http://www.pixijs.com/  ♥♥♥ 
```


<a id='application'></a>
Creating the Pixi Application and `stage`
-------------------------------
