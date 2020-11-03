---
title: "Beach Platform on Unity"
date: 2020-10-21T17:39:43+02:00
draft: fale
featuring_image: "https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/BeachPlatform.gif?raw=true"
---

Hello everyone! 


For the Unity class, I made my own Platformer Game, following Lea's lessons and some youtube tutorials. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/BeachPlatform.gif?raw=true "GAME")


## Moving Platforms

First, I learn how to create a moving platform. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MovingPlatform.gif?raw=true "Moving Platform GIF")


I created a platform, with a RigidBody and a Box Collider. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MovingPlatform.JPG?raw=true "Moving Platform")


In order to make it move, I first used an animator, and defined its movement. 
However, even with a velocity script, my character could not move once he was on the platform.


I found another technique with a script, that I find easier to modify.
Asyou can see below, I define how many points I want the platform to go to, then I enter their location and I define the speed, and the delay to go there.
I found it is easier to modify the movement with this technique.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MovementPlatformParameters.JPG?raw=true "Moving Platform")

Once that the platform was moving, the issue was that my player was not moving with it.
So I added a Triggered Box Collider to the platform. I made it a little taller than the platform, in order to be touched by the character on it. 
And Ta Da my character moves with the platform !

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MovingPlatform.gif?raw=true "Moving Platform Gif")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MovingPlatformScript1.JPG?raw=true "Moving Platform")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MovingPlatformScript2.JPG?raw=true "Moving Platform")



## Slippering Floor and Bouncing Balls


Then, I made a slippery floor, using a physic material. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/SlipperyFloor.gif?raw=true "Slippery Floor Gif")

I lowered all its friction, and added it to my floor.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/SlipperyFloor.JPG?raw=true "Slippery Floor")
![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/Slippery.JPG?raw=true "Slippery")

With the same technique, I created my bouncy balls. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/BouncyBalls2.gif?raw=true "Bouncy Ball Gif ")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/BouncyBall.JPG?raw=true "Bouncy Ball")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/SuperBouncy.JPG?raw=true "Super Bouncy")


## Falling Chairs

Moreover, I added falling platforms, represented as chairs. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/FallingChairs.gif?raw=true "Falling Chairs Gif")

To do so, I created the plateforms, added them 2 box collider with one Triggered to interact with the player.
I used the script below to make them fall (by being sensitive to gravity) if the player went on them, and added a delay, to make them only fall after 1 second. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/FallingChairs.JPG?raw=true "Falling Chairs")
![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/FallingPlatform.JPG?raw=true "Falling Platform")


The most difficult part was to respawn them after falling on the Death Wall.

I had to change the script of the Death Wall, and use a prefab to make it appear again. 
To make the prefab appear, I used "Instantiate" and a respawnPoint to define its position.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/DeathWallScript1.JPG?raw=true "Death Wall Script 1")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/DeathWallScript1.JPG?raw=true "Death Wall Script 2")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/DeathWall.JPG?raw=true "Death Wall")

As you can see, for each falling chair there is a respawn point slot, but also a prefab ! 
Because to diferenciate them in the code, I gave each one a tab : "Chair1", "Chair2" and "Chair3".
This way I can make them reapear in different locations, with always the same tab (that is why I needed three prefabs).


## Collectibles : Umbrellas

Furthemore, I added collectibles, represented as umbrellas.
Once the player goes on them, they disappear. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/Collectible.gif?raw=true "Collectible Gif ")
![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/CollectScript.JPG?raw=true "CollectScript")


The player also has to collect a fixed number of umbrellas to win.
Therefore, the number of umbrellas collected is used for the wining platform and the win text.
To do so, I created the empty object "Scene Manager" with the following script we saw in class :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/PlatformerSceneManager.JPG?raw=true "PlatformerSceneManager")

In the script associated to the wining platform, I used the Platformer Scene Manager to verify the number of umbrellas collected :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/FinalScript.JPG?raw=true "FinalScript")

And I used another script on the final platform to detect the player presence, and make the platform change its colors :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/TriggerScript.JPG?raw=true "Trigger Script")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/VictoryPlatform.gif?raw=true "Victory Platform Gif")

## The Menu

Moreover, I added a Quit and Restart Button.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/Menu.JPG?raw=true "Menu")

To do so, I created the two buttons.
Their OnClick() functions are directed by the empty game object Menu and its script.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/QuitButton.JPG?raw=true "Quit Button")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/MenuScript.JPG?raw=true "Menu Script")


## Timer

As you have seen, I added a Timer by creating a Timer Text, and controlling it from the Timer Script of the UI Game Object :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/UI.JPG?raw=true "UI")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/TimerScript.JPG?raw=true "Timer Script")

As you can see, the timer shows the time thanks to the parameter Time.deltaTime, and stops when the game is finished, so when the Victory Text is set to congratulations :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/VictoryPlatform.gif?raw=true "Victory Platform Gif")



## The Character's Animation

Finally, I animated the character I made on Blender.

I used Mixamo to download 4 animations of my character : idle, walking, running, and jumping.
I created an animator on my character, and used the Animator window to create my animation.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/Character.JPG?raw=true "Character ")


A blend tree is really usefull, we need less code, and variables to animate the character. 
Indeed, I only needed at the end the speed and the direction variable.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/AnimatorIdle.JPG?raw=true "Animator ")
![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/BlendTree.JPG?raw=true "BlendTree ")

Each rectangle represents a state.
On the left, I defined the necessary parameters for the transitions. (Some are not used because they come from previous tests)

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/Animator.JPG?raw=true "Animator ")

Of course, I still needed to modify my CharacterController. 

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/CharacterController1.JPG?raw=true "Character Controller")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/CharacterController2.JPG?raw=true "Character Controller")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/CharacterController3.JPG?raw=true "Character Controller")


The traps I fell in were to forget to activate the loop on my animations (in the downloaded animations), to modify the entries of my character controller, and to only activate the Exit Time after the jumps. 
(Because it is the only animations that needs to be finished, before starting another.)

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/LoopTime.JPG?raw=true "Loop Time")


I also put the camera in the hierarchy of my character, in order to follow the player when it moves.
There is also the empty object Player, present in the hierarchy of the character in order to follow it.
Since the camera is pointing the Player, we can easily controll what we will see with the camera by moving the relative location of the Player.

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/Camera.JPG?raw=true "Camera Controller")

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Unity/CameraScript.JPG?raw=true "Camera Controller")


Bonus :

To add a little life to my game, I used assets from free3d : beach balls, beach chairs, umbrellas, surfboards, Plamtrees, sand material, and even a waterfall !