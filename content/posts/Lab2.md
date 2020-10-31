---
title: "Lab 2"
date: 2020-10-05T14:16:03+02:00
draft: false
featured_image: "https://github.com/Ceici92/HugoBlog/blob/master/docs/images/Lab2/RollABallComputer.gif?raw=true"
---

Hello everyone !


Today, I built the 3D Unity Application : Roll A Ball. I followed the Unity learn steps to create it.
I started by creating the ground :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080658-b576bf80-0718-11eb-93fe-14e78926e891.png "The ground")


Then my player :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080666-b9a2dd00-0718-11eb-874e-35661702338d.png "The player")


I changed the light to have a better direction :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080678-bdcefa80-0718-11eb-9b59-dfa2ccc1e58c.png "The light")


I changed the Input System Package :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080680-c0c9eb00-0718-11eb-8f31-1f7cd9110534.png "Input System")


I changed the Build Settings of my project. I had no errors, because I already had Visual Studio and Windows 10 SDK :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080691-c45d7200-0718-11eb-970c-8f4af24a457d.png "Build Settings")


I added the Rigidbody to my player, in order to subject it to gravity :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080701-c7586280-0718-11eb-88fc-049bce9a7403.png "Rigidbody")


I added the Player Input to the player and the input actions, in order to use the pre-defined moving commands :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080707-cb848000-0718-11eb-91a0-65558b2b4372.png "Player Input")


I already had Visual Studio opened by Unity by default, because we had to do it for Lea's course. 
To really understand the PlayerController Script, I followed the unity learn videos :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080721-d0493400-0718-11eb-93e9-d44f6e5655de.png "Player Controller")

![alt Text](https://user-images.githubusercontent.com/71452847/95080729-d3dcbb00-0718-11eb-8e41-cf8d8f0b9de8.png "Player Controller")


I wrote the Camera Controller Script, with the player associated :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080748-da6b3280-0718-11eb-86f5-280bf66f7447.png "Camera Controller")


Then, I created the walls with a hierarchy, in order to easily move them at once :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080748-da6b3280-0718-11eb-86f5-280bf66f7447.png "Pickups")


I created the pick ups and their material. I put them specifically to form 2020 :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080783-e5be5e00-0718-11eb-99fb-cfc4e3651b94.png "Walls")
![alt Text](https://user-images.githubusercontent.com/71452847/95080787-e820b800-0718-11eb-92f2-126a2eecbe39.png "2020")


Then, I updated the PlayerController :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080799-efe05c80-0718-11eb-9ddf-98fdf0164f8c.png "Player Controller update")


Since the tutorial slides guide us to duplicate the pickups before creating the prefab, they do not inherit the properties of the prefab.
Fortunately, I can select all of the pick-ups and add the script at once :
 
![alt Text](https://user-images.githubusercontent.com/71452847/95080812-f373e380-0718-11eb-8bb9-bbd0d1076b65.png "Settings pickups")


Finally, I added the "Count" and "Win" text, a Text Mesh Pro object :

![alt Text](https://user-images.githubusercontent.com/71452847/95080820-f53da700-0718-11eb-854e-9962905e3490.png "Texts")


My game was now ready to be build. I built it with the settings given, and Ta Da ! My first Roll A Ball game works on my computer :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab2/RollABallComputer.gif?raw=true "Video")



## Bonus

I gaved an IP Paris tuch to the game, by moving the pickups to form IPP instead of 2020 :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab2/IPP.JPG?raw=true "IPParis")
