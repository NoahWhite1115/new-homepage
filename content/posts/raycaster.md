---
title: "Raycaster dev log"
date: 2021-06-13T16:43:39-07:00
draft: false
---

So as I've been working on my port of [Lode Vandevere's raycaster tutorial](https://lodev.org/cgtutor/index.html) into Golang, I've run into some issues. 

## SDL 1.2 to 2

One of the biggest is that Lode's tutorial was written originally in 2005, so it uses SDL 1.2. In 2021, SDL 2 is now the standard. Golang doesn't even have support for SDL 1.2. This means that I have to port this project into a language I'm unfamiliar with (the point of this project was to get a feel for how Golang compared to C++), using a graphics library that's a bit different than the original. It probably doesn't help that I'm not super well versed in graphics. I've never used OpenGL, and my SDL experience is limited to tutorials. 

Fortunately, there are a few things that make this way easier. One is the official [SDL 1.2 to 2.0 Migration Guide](https://wiki.libsdl.org/MigrationGuide). All of the SDL 1.2 functions that no longer exist in 2.0 have equivalents here. That helps a ton. On top of that, it provides explanations of WHY those changes were made, which is super helpful when it comes to understanding how the graphics world works. And it even has special shoutouts to old games of this type! 

The other thing that helps a ton is that a lot of the extra functionality provided by SDL2 isn't needed for a raycaster. These games are technically 2-D, so things like OpenGL aren't needed (Id Software popularized OpenGL with Quake, so a Wolfenstein 3D port definitely doesn't need it). Everything can be done directly with SDL, which means that roughly half of SDL2's docs aren't necessary for me to read. That's nice! (I'm still gonna read them at some point in the future.)

## Other errors

Still, there were a few things I had to figure out on my own. Go's SDL library seems to have the r and b channels flipped (or, more likely, I passed the wrong format type to the MapRGBA function). That took some trial and error to figure out. Other than that, I've had skewed perspective bugs (which Lode addresses in his tutorial, if I actually bothered to read ahead), weird distortions (from being a bit overzealous with type conversions) and I'm sure I'll encounter plenty more by the end of this project. One of the biggest things I've learned from this is how difficult it must be to debug a modern experimental game/ rendering engine. You definitely can't use a traditional debugger, because you obviously aren't going to step through every pixel for every frame. I know Unity has built in debuggers, but those cover game objects, not the rendering, which is baked into the engine itself.

## The Future of this Project

At this point in the project, I have working floor and ceiling textures. I'd like to add sprites and then I think that will meet the definition of done (for now). I know other, [similar projects](https://github.com/Owlzy/OwlRaycastEngine) have implemented multiple stories, lighting engines and used modern rendering techniques. Lode Vandevere's tutorial even suggests possible improvements in the form of thin or angled walls, enemies, weapons, portals and other game elements. I'd like to implement all of those in the future (modern rendering techniques seems particularly important), but for now I think I need to refactor this code first and maybe add some unit tests. Once I'm done with that, I might write a blog post breaking down the refactors, with any code I found interesting and screenshots to show how the renderer works.  