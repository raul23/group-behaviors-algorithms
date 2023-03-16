===================
Flocking algorithms
===================
Exploring and implementing flocking algorithms

`:information_source:` 

 I combined flocking with many other steering behaviors (e.g. arrive and flee) into one JavaScript application, 
 check `Steering behaviors <https://github.com/raul23/steering-behaviors#combining-all-steering-behaviors-including-flocking>`_

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
    <p align="center">From the <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">JavaScript port</a> of the flocking C# code</p>
  </div>

Description
"""""""""""
`:information_source:` 

 I ported the flocking C# (+ Unity) code from Paul Roberts' book `Artificial Intelligence in Games <https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228>`_ to JavaScript using the ``phaser.js`` 2D game development library.

**JavaScript port:** you can run the JavaScript code (which uses ``phaser.js``) through your browser via codepen.io

- `codepen.io <https://codepen.io/raul23/full/rNZwZVB>`_ (fullscreen; **Test it live!**)
- `codepen.io <https://codepen.io/raul23/pen/rNZwZVB>`_ (source code)
- I choose JavaScript because it makes it easy to share code with anyone on the Internet. They can test it live within their 
  browser without having to install software that might not support all kinds of systems.
  
  Also, it is quick and easy to add extra inputs if we want to be able to experiment with AI algorithms
  by testing different combinations of parameter values and see their output right away in the browser.
  
  Finally, `phaser.js <https://github.com/photonstorm/phaser>`_ is a stable and popular 2D gaming framework 
  that has lots of interesting features (e.g. collision detection, WebGL renderer) for developing browser-based games and hence good 
  for experimenting with AI for video games.
  
  `:information_source:` 
  
   I want to also port it to C++ since if you try to experiment with higher parameter values
   (e.g. number of zombies = 1000), you will see the JavaScript port lagging when rendering the different sprites on the screen
   (multiple computations need to happen almost instantly). 
  
   The JavaScript port was not done primarly with optimization in mind since it was done more as a way to test quickly 
   some interesting ideas in AI as applied to video games.

**Description:**

- The author Paul Roberts implemented the flocking algorithm in C# using the Unity game engine. The flocking algorithm consists of
  three parts: Separation, Alignment and Cohesion.
- Flocking is part of many other kinds of steering behaviors (e.g. wandering or evading) and hence has a weigth associated
  with it (0.25, the lowest value). However, for the sake of this flocking project, I didn't 
  take into account the other behaviors but I will eventually port them all in JavaScript.
- The author used zombies invading a shopping mall in search of fresh brains as a backdrop for a simple game where you will
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

Instructions
""""""""""""
- All green "zombies" (i.e. green balls) influence each other and hence exhibit group behaviors (flocking).
  The only red "zombie" (i.e. red ball) in the screen is controlled by the user (arrow keys) and is therefore not affected
  by the other zombies. However, the red zombie can affect other green zombies by moving it
  within their neighborhood as defined by their flocking distance.
  
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
- You can **pause** the program by clicking anywhere on the canvas. Then to resume the animations, just click again on the canvas.
- You can press the "D" key to enable debug mode which will draw lines representing the forward direction (i.e. the facing vector) 
  of each green zombie. Press the "D" key again to disable the debug mode.
  
  .. raw:: html

      <div align="center">
       <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
         <img src="./images/debug_lines.png">
       </a>
      </div>
  
Notes
"""""
- **Unfinished business**

  - I didn't completely ported the whole flocking C# code to JavaScript:
 
    - No collision detection between the zombies, i.e. they all overlap when occupying the same point in space. 
      There is a boundary around the canvas that the green zombies can't cross but the red zombie (controlled by the user) can.
      
      That's another **TODO**. Also add obstacles in the middle of the canvas as in the book.
      
      .. raw:: html

         <div align="center">
          <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
            <img src="./images/overlap.png">
          </a>
         </div>

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
Buckland, Mat. *Programming Game AI by Example.* Jones and Bartlett Learning, 2005
----------------------------------------------------------------------------------
- `Errata for Programming Game AI by Example <http://www.ai-junkie.com/ai_book2/errata/>`_
- `Bug Fixes for Programming Game AI by Example <http://www.ai-junkie.com/ai_book2/bugs/>`_
- `amazon.com <https://www.amazon.com/Programming-Example-Wordware-Developers-Library/dp/1556220782>`_
- **Pages referring to flocking:**
   
  **Chapter 3 : How to Create Autonomously Moving Game Agents**
   
  - Introduction (p.85)
   
      It was based on very simple rules, yet it looked so spontaneous and natural and was mesmerizing to watch. 
      The programmer who designed the behavior is named Craig Reynolds. He called the flocking birds “boids,” and the simple rules the flocking 
      behavior emerged from he called “steer- ing behaviors.”
   
  - Group Behaviors (p.113)
   
      In fact, flocking is a combination of three group behaviors — cohesion, separation, and alignment — all working together.
      
  - Flocking (pp.118-119)
   
      The lower-level entities following the rules have no idea of the bigger picture; they are only aware of 
      themselves and maybe a few of their neighbors.
      
    Flocking consists of three parts:
      
      Flocking, as originally described by Reynolds, is a combination of the three previously described group behaviors: 
      separation, alignment, and cohesion.
      
Millington, Ian. *AI For Games,* Third Edition. CRC Press, 2020
---------------------------------------------------------------
- `amazon.com <https://www.amazon.com/AI-Games-Third-Ian-Millington/dp/0367670569>`_
- **Pages referring to flocking:**

  - **Chapter 3: Movement**
  
    - Flocking and Swarming (pp.98-99)
    
        Though not the most commonly implemented in a game, flocking is the most commonly cited steering behavior. 
        It relies on a simple weighted blend of simpler behaviors.
  - **Chapter 6: Tactical and Strategic AI**
  
    - Scalability (p.562)
    
       Reynolds’s flocking algorithm, for example, can scale to hundreds of individuals with only minor tweaks to the algorithm.
  - **Chapter 15: AI-Based Game Genres**
  
    - Flocking and Herding Games (pp.965-969)
    
       The emergent nature of herding games means that it is impossible to predict the exact behavior until you can build and test it.

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

Resources
=========
- `Flocking (behavior) <https://en.wikipedia.org/wiki/Flocking_(behavior)>`_ (wikipedia.org)

  **Algorithm**
  
   Basic models of flocking behaviour are controlled by three simple rules:

   **Separation**
      
   - Avoid crowding neighbours (short range repulsion)
   **Alignment**
   
   - Steer towards average heading of neighbours
   **Cohesion**
   
   - Steer towards average position of neighbours (long range attraction)
   
   With these three simple rules, the flock moves in an extremely realistic way, creating complex motion and 
   interaction that would be extremely hard to create otherwise.
  
   A basic implementation of a flocking algorithm has complexity O(n**2) – 
   each bird searches through all other birds to find those which fall into its environment.
- `Craig Reynolds' Boids page <http://www.red3d.com/cwr/boids/>`_

   In 1986 I made a computer model of coordinated animal motion such as bird flocks and fish schools. It was based on three 
   dimensional computational geometry of the sort normally used in computer animation or computer aided design. I called the generic 
   simulated flocking creatures boids. The basic flocking model consists of three simple steering behaviors which describe how an 
   individual boid maneuvers based on the positions and velocities its nearby flockmates
- `Starling murmuration creates duck shape above West Yorkshire <https://www.bbc.com/news/av/uk-england-leeds-55221885>`_ (BBC video, 7 December 2020)

  .. raw:: html

      <div align="center">
       <a href="https://www.bbc.com/news/av/uk-england-leeds-55221885" target="_blank">
         <img src="./images/bbc.png">
       </a>
      </div>

    "A photographer from West Yorkshire has managed to capture an image of a duck composed of thousands of starlings during a murmuration.
    Peter Lau said there was "no CGI, no Photoshop...just good luck" in capturing the spectacle on camera."
