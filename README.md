# CS-330 Final Project: 3D Desk Scene

This repo holds my final project from CS-330 (Computational Graphics and Visualization) at SNHU. The scene is a desk built in C++ and OpenGL. It's a desktop on two U-shaped leg frames, with an iMac monitor, keyboard, and mouse on top, all sitting on a textured ground plane and lit by three point lights tuned for a warm, late-evening mood.

Inside this repo you'll find:
- **`3DScene.zip`**: the full Visual Studio 2022 project (source files, headers, `.sln`, `.vcxproj`, the built EXE, and `glew32.dll`)
- **`DesignDecisions.docx`**: the 2-page APA design document covering the choices I made on geometry, textures, lighting, and camera controls

## Reflection

### 1. How do I approach designing software?

Before this project I'd never really thought about software design as a *spatial* problem. Most of what I'd written was logic (inputs, conditions, outputs). Building a 3D scene forced me to think in a different way, because the order things happen in actually changes what shows up on screen. The biggest design skill I picked up was getting the transformation pipeline right: scale, then rotate, then translate, every single time. Once that clicked, I stopped fighting the math and started using it on purpose.

My design process for the project was pretty top-down. I started from the rubric and the reference photo and broke the scene into the simplest primitives I could get away with. Boxes for the desk, a plane for the ground, then later cylinders and other shapes for the iMac, keyboard, and mouse. I'd plan a piece on paper-ish (in my head, mostly), build it, compile, look at it, and then decide what to fix. UV scaling was a whole separate design problem on top of geometry. I had to think about each surface's proportions individually so the textures didn't stretch or tile weird, and that taught me that "design" isn't just shape, it's how everything reads visually once it's all together.

The tactic I'll carry forward is **building in passes**. I didn't try to make the whole scene perfect on the first attempt. I got it standing up, then textured, then lit, then tuned. That same idea, getting a rough version working end-to-end before polishing any one piece, is something I think applies to basically any project I'll work on, in any domain.

### 2. How do I approach developing programs?

The biggest development strategy I leaned on was incremental compiles. I'd add one object, build, run, look. Add a texture, build, run, look. It sounds obvious but coming in as a beginner with OpenGL it saved me a ton of pain. When something broke, I always knew exactly what had broken it because I'd only changed one thing. The other strategy was being deliberate about commenting the *why*, not just the *what*. After the milestone four feedback I started writing comments that explained why I picked a specific UV scale or a specific light intensity, which helped me later when I came back and needed to remember what I'd been thinking.

Iteration was honestly the whole project. Lighting in particular: the warm amber point light got dialed in over at least two passes after it initially blew out the desktop textures. UV scales got revisited every time I added a new object. Mouse sensitivity for the camera got tuned by feel. Even the leg frames got redone after I realized the Z-axis orientation was wrong. None of that stuff was right the first try, and I think accepting that early made the whole project less stressful.

The clearest way my approach evolved is that I got a lot more comfortable with bugs. Early on, something not rendering felt like a disaster. By the end, when I caught the `FindMaterial` bug returning `true` unconditionally and just fixed it with `return(bFound)`, debugging felt like a normal part of the work instead of a sign something was wrong with me. That's probably the biggest shift over the seven weeks: going from "I hope this works" to "let me figure out why it doesn't."

### 3. How can computer science help me in reaching my goals?

My career path is in cybersecurity, so I want to be honest: I'm not heading into computational graphics professionally. But game dev and graphics are hobbies I take seriously and want to grow into something more down the road, and this course gave me real foundation for that. I now actually understand what's happening when a 3D engine renders a frame, instead of treating it like magic.

On the educational side, the math and structural thinking from this course aren't graphics-specific. Matrix transformations, coordinate spaces, and the discipline of building a complex system out of small verified pieces all translate to plenty of other CS coursework. The systematic debugging mindset especially carries over to security work, where you're constantly trying to figure out why a system is doing something it shouldn't.

Professionally, even in cybersecurity, knowing how graphics pipelines and rendering work isn't useless. Game engines, GPU compute, and visualization tools all show up in security research at some point, and being someone who isn't intimidated by that side of the stack is an advantage. And on the hobby side, this is the first project where I've built something visual from scratch in C++ and had it actually work the way I intended. That's the kind of thing that makes me want to keep going on my own time, and eventually take the hobby further.
