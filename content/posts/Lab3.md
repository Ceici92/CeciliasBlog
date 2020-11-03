---
title: "Lab 3"
date: 2020-10-06T16:10:15+02:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/121064455_633550003949458_2545566836504823763_n.jpg?raw=true"
---

Hello everyone !


Today I build my Roll a Ball game on my Android phone.


## Part 1 : Set up

To build on Android I had to start with installing the Android Build Support :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/Capture.JPG?raw=true "SDK")

Then, I had to define the new build settings, starting with the player settings : the orientation, the graphic APIs, the identification and the publishing key.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/1.png?raw=true "Phone screen")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/2.png?raw=true "Phone screen")

After setting up my unity project, I had to set up my phone. I activated the developer mode, and enabled the debugging. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/120959576_3379234365523327_2511240152500799826_n.jpg?raw=true "Phone settings")

I connected my phone to my computer, and selected it in the building settings.
At this part I was able to start the game on my phone, but I still had to change the game play. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/121064455_633550003949458_2545566836504823763_n.jpg?raw=true "Phone screen")


## Part 2 : Implementation of the mobile application

To setup my player for my mobile, I had to use the gyroscope of my phone. 
For this I put the camera, the walls, the light, and the pick-ups as children of the ground.

![alt Text](https://user-images.githubusercontent.com/71452847/95097521-db5a8f00-072d-11eb-9514-3abf26c6085a.png "Parent")
 
Then code the Tinltig script for the ground :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/3.png?raw=true "Phone screen")

I build again, and my ball literally ended out of my arena. So I lowered the speed of my player, and augmented its gravity. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab3/Lab3.gif?raw=true "Gif")


## Bonus

I gaved an IP Paris tuch to the game, by moving the pickups to form IPP instead of 2020 :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Lab2/IPP.JPG?raw=true "IPParis")
