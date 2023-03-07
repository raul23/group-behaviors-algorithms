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
JavaScript: a port of Paul Roberts' C# implementation of flocking
-----------------------------------------------------------------
Description
"""""""""""
`:information_source:` 

 I ported the flocking C# (+ Unity) code from Paul Roberts' book `Artificial Intelligence in Games <https://www.amazon.com/Artificial-Intelligence-Games-Paul-Roberts/dp/1032033223/>`_ to JavaScript using the ``phase.js`` 2D game development library.

**JavaScript port:** you can run the JavaScript code (which uses ``phaser.js``) through you browser via codepen.io

- `codepen.io <https://codepen.io/raul23/full/rNZwZVB>`_ (fullscreen)
- `codepen.io <https://codepen.io/raul23/pen/rNZwZVB>`_ (source code)

Instructions
""""""""""""
- All green "zombies" (i.e. green balls) influence each other and hence exhibit group behaviors (flocking).
 The only red "zombie" (i.e. red ball) in the screen is controlled by the user (arrow keys) and is therefore not affected
 by the other zombies. However, the red zombie can affect other green zombies by moving it
 within their flocking distance.
- Click on the bottom right button '*Open options*' to modify some of the important settings:

  - **Number of "green zombies"** (i.e. green balls) with 10 as the default
  - **Flocking distance** (the radius of zombies' circle of influence) with 25 as the default 
  - **Max speed** with 500 as the default
  - **Mass** with 1 as the default
  - You can pause the program by clicking anywhere on the canvas. Then to resume, just click again.

NOTES
"""""
- **Unfinished business**

  - I didn't completely ported the whole flocking C# code to JavaScript:
 
    - I didn't take into account the zombies' field of view (fov) as in the book. Hence, the zombies
      in the JavaScript port can be considered as having a 360 field of view (you could imagine
      these creatures as being a superior type of zombie with extra eyes behind their heads :)
      
      However, I will eventually incorporate the fov. I just need to investigate more on theUse of Euler and Quaternion
      in ``phaser.js`` since the fov involves some rotations.
    - Debug lines that are drawn on each zombie in order to indicate where they are going. This is definitely something
      I will add soon since it will greatly help me when implementing other AI algorithms as an important debugging tool.

References
""""""""""
- Roberts, Paul. `Artificial Intelligence in Games <https://www.amazon.com/Artificial-Intelligence-Games-Paul-Roberts/dp/1032033223/>`_. 
  CRC Press, 2022.

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
