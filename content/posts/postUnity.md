---
title: "PostUnity"
date: 2020-10-21T17:39:43+02:00
draft: true
---

Hello everyone! 


For the Unity class, I made my own Platformer Game, following Lea's lesseons and some youtube tutorials. 

First, I learn how to create a moving platform. 

I created a plateform, with a RigidBody and a Box Collider. 
In ordeer to make it move, I first used an animator. However, I found another technique with a script, tht I find easier to modify.

Once that the plateform was moving, the issue was that my player was not moving with it.
So I added a Triggered Box Collider to the platform. I made it a little taller than the platform, in order to be touched by the character on it. 
And Ta Da my character moves with the platform !


Then, I made a slippery floor, using a physic material. 

I lowered all its friction, and added it to my floor.
With the same technique I created my bouncy balls. Except that I used a box collider and not a sphere collider, because it was to complicated otherwise.

The most difficult part was to respawn falling platforms.

To do so, I created a script to make them fall (by being sensitive to gravity) if the player went on them. I added a delay, to make them only fall after 1 second. 
However, it was quite complicated to make them reappear. 
I had to change the script of the Death Wall, and use a prefab to make it appear again. To make the prefab appear, I used "Instantiate", and I used a respawnPoint to define its position.

Finally, I animated my character. 

I used Mixamo to download 4 animations of my character : idle, walking, running, and jumping.
I created an animator on my character, and used the Animator window create my animation.

A blend tree is really usefull, we need less code, and variables to animate the character. Indeed, I only needed at the end the speed and the direction variable.
Of course, I still needed to modify my CharacterController. 

The traps I fell in were to forget to activate the loop on my animations (in the downloaded animations), to modify the entries of my character controller, and to only activate the Exit Time after the julmps. 
(Because it is the only animations that needs to be finished, before starting another.)



Bonus :

To add a little life to my game, I used assets from free3d.