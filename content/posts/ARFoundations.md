---
title: "AR Foundation on Unity"
date: 2020-11-05T11:42:24+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/TestAR.gif?raw=true"
---

Hi !

In this post I describe how I made a simple AR application with image recognition.


I started by looking at tutorials on how to use AR on Unity.
First, I followed the tutorial on Unity learn, to set up my project for AR :
https://learn.unity.com/tutorial/configuring-unity-for-ar-development-2019-3?language=en#5e623ad9edbc2a0020cf8224
And then this video, because it talked about Image recognition an aspect we will need for our project :
https://www.youtube.com/watch?v=9qErhhxoEVY


Si I started to put in place all the components needed for an AR project shown on Unity Learn.
I switched my project to Android, and modified the Player Settings -> Other Settings :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ProjectSettings.png?raw=true "ProjSettings")
 

Then, with the Package Manager I installed the AR Packages : AR Foundation, AR Core XR Plugin, and ARKit XR Plugin for face tracking as shown in the video.
 ![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ProjectSettings2.png?raw=true "ProjSettings2")



Then, I switched to the tutorial video.
I deleted the main camera, and I added AR Session Origin and AR Session :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ARSession.png?raw=true "ARSession")



I added a Script to AR Session Origin, and created in the assets the ImageTarget of AR Session Origin : Create -> XR -> Image Reference

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ARSession2.png?raw=true "ARSession2")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/Target.png?raw=true "Target")


Then, I filled the slots of AR Session Origin :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ARSessionOrigin.png?raw=true "ARSessionOrigin")


I created a Sphere of size 0.2, and added to it a directional light oriented in order to light it up :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/Sphere.png?raw=true "Sphere")


Then, I saved it as a prefab, deleted the object, and put the prefab as the Tracked Image Prefab of AR Session Origin :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ARSphere.png?raw=true "ARSphere")


Finally, in the Player settings I had some modifications to make.
I removed Vulkan because it is not supported by AR Core.
I unchecked Multithread rendering, and verified I at least selected Android 8.0 to make AR Core work.
In Configuration, I put Install Location to Automatic, and Filter Touches to unchecked :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/ProjectSettings3.png?raw=true "ProjectSettings3")



I tested it on my Android !

To do so, I build the apk, put it on my phone, and installed it.

I could also have connected my phone to my computer, selected it as the running device, enabled the debugging on my phone, and built it. But since my project will be about Street Art, it is better to have an application.
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/Build.png?raw=true "Build")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/AR/ARFoundations/TestAR.gif?raw=true "Video")



The next step is to replace the sphere with an animated AR object ! 





