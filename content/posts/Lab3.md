---
title: "Lab 3"
date: 2020-10-05T16:10:15+02:00
draft: false
---


Hello everyone !

Today I buil my Roll a Ball game on my Android phtone.

# Lab 3

## Part 1 : Set up

To build on Android I had to start with installing the Android Build Support :

[comment]: <> (![alt Text]( "SDK"))

Then, I had to define the new build settings, starting with the player settings : the orientation, the graphic APIs, the identification and the publishing key.

![alt Text](https://user-images.githubusercontent.com/71452847/95097488-d4cc1780-072d-11eb-9aca-bdd4ee8e04fb.png "Player Settings")
![alt Text](https://user-images.githubusercontent.com/71452847/95097495-d695db00-072d-11eb-9109-cc71b5f005e1.png "Unity settings")

After setting up my unity project, I had to set up my phone. I activated the developper mode, and enabled the debugging mode. 

[comment]: <> (![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab3/120959576_3379234365523327_2511240152500799826_n.jpg?raw=true "Phone settings"))

I connected my phone to my computer, and selected it in the building settings.
At this part I was able to start the game on my phone, but I still had to change the game play. 

[comment]: <> (![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab3/121064455_633550003949458_2545566836504823763_n.jpg?raw=true "Phone screan"))


## Part 2 : Implementation of the mobile application

To setup my player for my mobile, I had to use the gyroscope of my phone. 
For this I put the camera, the walls, the light, and the pick-ups as children of the ground.

![alt Text](https://user-images.githubusercontent.com/71452847/95097521-db5a8f00-072d-11eb-9514-3abf26c6085a.png "Parent")
 
Then code the Titlig script for the ground :

![alt Text](https://user-images.githubusercontent.com/71452847/95097530-ddbce900-072d-11eb-83da-d344b60db66e.png "Script")

I build again, and my ball literally ended out of my arena. So I lowered the speed of my player, and augmented its gravity. Still a problem remained :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab3/Lab3.gif?raw=true "Gif")

The axis of the game were not good. When I tried to go up it went right, etc..
I tried rotating the player, the ground, but it did not work. The gyroscope was as if I was in the portrait mode.

[comment]: <> ([![alt Text](https://user-images.githubusercontent.com/71452847/95677903-3a565300-0bc9-11eb-86c1-480a1fae631c.JPG "Screan phone still bug")](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/video-1602087118.mp4?raw=true))
