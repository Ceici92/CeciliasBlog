---
title: "Lab 4"
date: 2020-10-30T19:46:28+01:00
draft: false
featured_image: "https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/Black.jpg?raw=true"
---

Hello everyone !

Today, I created my first VR application for Occulus Quest. I modified my Roll a Ball game to work in VR.


First, I changed the project settings as followed.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR1.png?raw=true "")
![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR2.png?raw=true "")


I downloaded the VRTK project, in order to use some of its packages.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR4.png?raw=true "")


Then, in the VRTK project, I imported the Occulus Integration pagckage.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR3.png?raw=true "")


I exported my Roll a ball project assets, and imported it in my VRTK project.

Since we do not use UnityEngine.InputSystem in the VRTK project, I had to comment every part of my scripts that used it.
When the errors vanished, I set up the environment. 

I deleted the camera, created a floor, a table, and the Empty GameObject for the non-interactable objects.
I added a box collider to my Roll a Ball object, and created two new layers for this object and its children.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR5.JPG?raw=true "")


Unfortunatly, my project was to heavy for my computer. 
So, I tried to follow another guide from the VRTK website, describing the essential packages to import.
However, it did not work because the guide used an 2018 package that was missing a lot of components regarding the OVR Camera.

Finally, I tried to optimize my project by only keeping the needed elements from the VRTK initial package, for example, I deleted the sample scene, and the 2D sprite package.
Also, I only downloaded the necessary components from the Occulus Integration package, I left out the example scene, the avatar modelsn the shared assets et the Spatializer scenes.
It worked, I could continue to build game with a functional computer.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR6.png?raw=true "")


I added the OVRCameraRig to the scene and set its origin to the ground.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR6bis.png?raw=true "")

I added the component Linked Alias Association Collection (which was missing in older VRTK packages) to the OVRCameraRig.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR7.png?raw=true "Linked Alias")


The Left Hand and Right Hand Achors got the OVRControllerPrefab, with the right parameters : L and R touch controller.

I added TrackedAlias to the scene, put its size to 1 and draged the OVRCameraRig to the slot.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR7bis.png?raw=true "")

TrackedAlias got an Interactor, as a chold of Left and Right Controller Aliases.

I created an empty GameObject : LeftTriggerAxis, with the component Unity Axis 1D Action, nd the Axis Name VRTK_Axis9_LeftTrigger (found on the InputManager of the Project Settings).

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR8.png?raw=true "")

I created another GameObject : LeftTriggerPressed, and added to it the Float to Boolean and Boolean Action components.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR9.png?raw=true "")

I did the same for the right. 

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR10.png?raw=true "")


Then, in Interactor I completed the slots with the LeftTriggerPressed and the LeftControllerAlias; and repeated it for the right.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR11.png?raw=true "")


To be able to interact with my Roll a Ball as a virtual object, I added the Interactable.Primary_Grab to the scene, and placed the Roll a Ball in its Meshes.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR12.png?raw=true "")


In order to add physics to this virtual object, I set up the Velocity Tracker in the OVRCameraRig.
I copied the OVRAnchorVelocityEstimator from the VRTK github, and added it to the Linked Alias Association Collection.
I added as its components the CenterEye, the LeftHand and the RightHand Anchores, and set their references :

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR13.png?raw=true "")


I added UI :

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR14.png?raw=true "")


Finally, I build and run my project on an Occulus Quest using occulus link, but it did not work.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR15.png?raw=true "")


My scene stayed black in Virtual Reality.

![alt Text](https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab4/VR16.png?raw=true "")


Since the Occulus Application alerted me that my graphic card was not powerfull enough for a VR game, I tried to run the applicaiton on another computer, but it still did not worked.
I also tried to see if I had the same probleme with an example scene, and it was the same.



