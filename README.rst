===================
Flocking algorithms
===================
Exploring and implementing flocking algorithms

.. contents:: **Contents**
   :depth: 5
   :local:
   :backlinks: top

Algorithms
==========
In JavaScript: a port of Paul Roberts' C# implementation of flocking
--------------------------------------------------------------------
.. raw:: html

   <div align="center">
    <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
      <img src="./images/fullscreen.png">
    </a>
  </div>

Description
"""""""""""
`:information_source:` 

 I ported the flocking C# (+ Unity) code from Paul Roberts' book `Artificial Intelligence in Games <https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228>`_ to JavaScript using the ``phase.js`` 2D game development library.

**JavaScript port:** you can run the JavaScript code (which uses ``phaser.js``) through your browser via codepen.io

- `codepen.io <https://codepen.io/raul23/full/rNZwZVB>`_ (fullscreen)
- `codepen.io <https://codepen.io/raul23/pen/rNZwZVB>`_ (source code)
- I choose JavaScript because it makes it easy to share code with anyone on the Internet. They can test it live within their 
  browser without having to install software that might not support all kinds of systems.
  
  Also, it is quick and easy to add extra inputs if we want to be able to experiment with AI algorithms
  by testing different combinations of parameter values and see their output right away in the browser.
  
  Finally, `phaser.js <https://github.com/photonstorm/phaser>`_ is a stable and popular 2D gaming framework 
  that has lots of interesting features (e.g. collision detection, WebGL renderer) for developing browser-based games and hence ideal 
  for experimenting with AI for video games.

**Description:**

- The author Paul Roberts implemented the flocking algorithm in C# using the Unity game engine. The flocking algorithm consists of
  three parts: Separation, Alignment and Cohesion.
- Flocking is part of many other kinds of steering behaviors (e.g. wandering or evading) and hence has a weigth associated
  with it (0.25, the lowest value). However, for the sake of this flocking project, I didn't 
  take into account the other behaviors but I will eventually port them all in JavaScript.
- The author used zombies invading a shopping center in search of fresh brains as a backdrop for a simple game where you will
  implement and test different steering behaviors exhibited by the horde of zombies. 
  
  In the C# game, each zombie is represented as a green dot
  on the screen and can be spawned at specific places and at a certain rate during the game. The user controls a 
  black dot that can shoot at the zombies with the spacebar.
  
  .. raw:: html

      <div align="center">
       <a href="https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228" target="_blank">
         <img src="./images/book_project.png">
       </a>
       <p align="center">From Paul Roberts' book <i>Artificial Intelligence in Games</i>, p.56</p>
      </div>
  
  `:information_source:` 
  
   In the JavaScript port, green balls serve as a substitute for zombies and the user controls a
   red "zombie" which is actually a red ball. The user can control the red "zombie" with the arrow keys, can affect other
   green "zombies" but can't be affected by them. 
  
   The red "zombie" serves as a way of testing how the flocking algorithm works live while the code is running within your browser since
   you can position the red "zombie" anywhere close enough to a green "zombie" (within its flocking distance). Plus, you can
   easily change different parameter values (e.g. flocking distance, speed) and re-run the simulation.
  
  `:warning:` 
   
   I didn't implement yet the field of view (fov) as in the book. Thus, right now the "zombies" have 360 degrees
   fov as if they have extra eyes behind their heads. I will eventually add this property as soon as I investigate
   more how rotation (Quaternion, Euler) is done in ``phaser.js``.

Instructions
""""""""""""
- All green "zombies" (i.e. green balls) influence each other and hence exhibit group behaviors (flocking).
  The only red "zombie" (i.e. red ball) in the screen is controlled by the user (arrow keys) and is therefore not affected
  by the other zombies. However, the red zombie can affect other green zombies by moving it
  within their flocking distance.
  
  .. raw:: html

      <div align="center">
       <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
         <img src="./images/green_and_red.png">
       </a>
      </div>
- Click on the bottom right button '*Open options*' to modify some of the important settings:

  .. raw:: html

      <div align="center">
       <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
         <img src="./images/open_options.png">
       </a>
      </div>

  - **Number of "green zombies"** (i.e. green balls) with 50 as the default
  - **Flocking distance** (the radius of zombies' circle of influence) with 100 as the default 
  - **Max speed** with 500 as the default
  - **Mass** with 1 as the default
  
  .. raw:: html

      <div align="center">
       <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
         <img src="./images/options.png">
       </a>
      </div>
- You can **pause** the program by clicking anywhere on the canvas. Then to resume, just click again.

Notes
"""""
- **Unfinished business**

  - I didn't completely ported the whole flocking C# code to JavaScript:
 
    - I didn't take into account the zombies' field of view (fov) as in the book. Hence, the zombies
      in the JavaScript port can be considered as having a 360 field of view (you could imagine
      these creatures as being a superior type of zombie with extra eyes behind their heads :)
      
      However, I will eventually incorporate the fov. I just need to investigate more on the use of Euler and Quaternion
      in ``phaser.js`` since the fov involves some rotations.
    - Debug lines that are drawn on each zombie in order to indicate where they are going. This is definitely something
      I will add soon since it will greatly help me when implementing other AI algorithms as an important debugging tool.

References
""""""""""
- Roberts, Paul. `Artificial Intelligence in Games <https://www.amazon.com/Artificial-Intelligence-Games-Paul-Roberts/dp/1032033223/>`_. 
  CRC Press, 2022.
  
  See the `Books <#roberts-paul-artificial-intelligence-in-games-crc-press-2022>`_ section to know the specific pages
  from the book that discuss flocking and where to get the book's C# code.

Articles
========
- Reynolds, C. W. (1987). `Flocks, Herds, and Schools: A Distributed Behavioral Model 
  <https://team.inria.fr/imagine/files/2014/10/flocks-hers-and-schools.pdf>`_, in 
  *Computer Graphics*, 21(4) (SIGGRAPH ‘87 Conference Proceedings) pp. 25–34.

Books
=====
Roberts, Paul. *Artificial Intelligence in Games.* CRC Press, 2022
------------------------------------------------------------------
- `Book website <https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228>`_ (routledge.com)
- `amazon.com <https://www.amazon.com/Artificial-Intelligence-Games-Paul-Roberts/dp/1032033223/>`_  
- C# (+Unity) code for all projects from the book @ 
  `routledge.com <https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228>`_ (ZIP 66.3MB)
- **Pages referring to flocking:**

  - **Chapter 3: Steering Behaviours**

    - GROUP BEHAVIOURS (pp.50-54)

       There are three parts to achieving good flocking, and these are Separation, Alignment and Cohesion.     
    - STEERING BEHAVIOURS – PRACTICAL (pp.56-71)

      Flocking C# code (for Separation, Alignment and Cohesion) @ pp.59, 68-71
