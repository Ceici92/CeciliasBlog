---
title: "Transversal Project : StreetAR"
date: 2021-02-05T10:21:02+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/Feature.jpg?raw=true"
---

As the Transversal Project of the master VAR, we had to create an AR or VR application by groups of two. 
My colleague and I decided to realize an AR application for a street art in Evry.
This fresco was created by children of the  “Maison de Quartier” in Evry, students of Telecom Sudparis and the street artist Vince.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Fresco.png?raw=true "Fresco")

We wanted to make an application in connection with art, and we knew the vast number of frescos in Evry, so we decided to make an AR application that gives life to the one about the environment next to our school. 
We also chose this specific one because we had the artist's contact (Vince). Moreover, the environmental theme is very interesting, even more for kids. 

To define our project and how to implement it, we always had to keep in mind that it had to stay easy to use by users non initiated to AR. I would be an app to launch and to be guiding in. 

The goal of this post is to come back on the technical parts of the project.

Here is a summary of the technologies we decided to use : 
•	Blender was needed for meshes, textures and animation.
•	Unity was the core of the project. It is a technology we already know and that enables everything we needed : from UI to animations and building an app.
•	As SDK we used AR foundation, a unity framework using both AR Core (Google) and AR Kit (Apple) functionalities.


At the end of this post you can download the android version of the application.


# 1.	Blender Animations

We can decide to move the object following a curve.
To do so, we need to start by creating a curve and an empty object.
In the Constraint properties of the empty, add a following path with the curve as the target :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/CurveAnimation.png?raw=true "")


Make the object you want to animate as a child of the empty (select object then empty, Ctrl+P, Parent (keep transformation).
Then, configure the parameters of the axis and the slots as wanted.
Finally, move the offset to make the object follow the path, and add keyframes at the wanted moments.

To manage different Animations of a character in the same file in blender :
We can go on the Dope Sheet : Action Editor, to observe the different actions/animations in the file :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/DopeSheet.png?raw=true "")

If we choose an animation corresponding to the rigging selected, we can see that it is applied on the selected character. If we want to put the same action to different characters it is better to use this button (or it will bug), that duplicate the action :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/DopeSheet2.png?raw=true "")

 
You can’t dele actions (or texture) directly in the action menu, you have to go in the hierarchy of the blender files :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/BlenderFiles.png?raw=true "")
  

 
# 2.	Blender Textures

For the lion model I used a prefab from Sketchfab, but as you can see below it was not textured :

To texture it, first, I got a lion texture from 3dtextures.me, you can also find some on textures.com.  
Here is a good tutorial video about using material images to make a texture:
https://www.youtube.com/watch?v=XI-pZshRp8g

To use this texture on the lion, I started by creating the new material “Fur”, by unwrapping my Lion points in edit mode, and by opening the shader menu.

I added the base colour to the BSDF block (in short it is the more recent block that reunites a lot of other types of materials), and I assigned the fur material to all the lion to see what it looked like.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Textures1.png?raw=true "")


Then I opened the UV Editor, and increased the size of the UV Map to have a more realistic fur :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/UVMap.png?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Textures2.png?raw=true "")

Now I know that it is not the accurate way to do it, because the UV map of the lion must stay in the U and V axis. I should have repeated the pattern instead by adding a block in the shader menu.

Moreover to complete the texturing, I went back to the shader editor, and added the normal map as follows. By hiding the correct part of the texture, it already seems a little more realistic :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/NormalMap.png?raw=true "")
 

Finally I added the roughness image to the shader, to make the texture react correctly to the light :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Roughness.png?raw=true "")


After the texturing of the fur, we still had to represent the other parts of the lion, such as the nose and the mouth. 
To do so I selected the right regions in edit mode and assign a new black material to them  :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Nose1.png?raw=true "")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Nose2.png?raw=true "")



Since it was not really realistic, I triangulated the faces on the sides, and only selected one of the resulting triangles :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Nose3.png?raw=true "")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Nose4.png?raw=true "")


Then I did the eyes by creating a new yellow material, and the mane by darkening the fur color, and adjust the uv map size to make the hairs bigger :

 ![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Mane.png?raw=true "")

 


We also tried the paint option on blender to texture the lion. 
I created a new material, selected the lion, and paint the texture of the new material :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/PaintTexture.png?raw=true "")


3.	Export textures and animations from Blender to Unity

Textures :
We exported the blender models in fbx to keep the materials and the animation in the export. 
Once in Unity, we have to unwrap the materials of the prefab, to assign them the right textures. To assign again the textures we need to have images of our textures.
To have them, we must follow a few steps on Blender. First, we have to unwrap our meshes in edit mode, and to bake the blender texture following those steps :
https://www.youtube.com/watch?v=ZmZDFdeneoo&t=439s
It did not work for my lion because I had problems with the UV Mapping (as you saw I scaled the representation of the meshes on the UV map wrongly before). So I exported my lion on fbx. Then, still in Blender, I created a plane, I added to it the material I wanted to bake. I created in the tree map (shader window) an image texture linked to nothing, with a new image, and I kept it selected. I opened an UV Map window, and made sure my plane was unwrapped. Then, I baked the texture by choosing Cycles render, in bake I chose the right texture type : diffuse (or normal, etc..), and checked the color slot. Bake. And I ended up with the image of my texture on the uv map window.



# 4.	Import textures and animations on unity

Once your fbx object in Unity, it does not directly have its textures, but the materials are created. 
To add the textures, extract the materials from the prefab. Put the object in the scene to see what happens. 
Then import the image of the baked textures in Unity, and add it on the Albedo map of the materials :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/UnityTextures.png?raw=true "")


Depending on your baked texture you can also fill the normal map, heigh, occlusion etc ….
Now, your object on the scene and its prefab should have the right materials.

## Animations :

Export your blender object on the fbx format. Once on unity the prefab should have the animations :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/UnityAnimations.png?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/UnityAnimations2.png?raw=true "")

 
### Issue 1 : Wrong positions

Sometimes the scale or the position of an object changes when its imported animation is played. It is because the position or/and the scale of the object are saved properties in the keyframes of the animation.
To prevent it, the solution is to detect the element that changes of coordinates (here the armature) : 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/RestingArmature.png?raw=true "")


Copy its components while it is running. (Little tip put the problematic animation as the first one in the animation controller, and then you will just have to move the timeline to see the object animated. Or create an animator aimed for all the tests ) :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Animations.png?raw=true "")


Paste the coordinates on the element when the object is static. It will take the same place as in the animation.
Then, create an empty object (coordinates 0 0 0 ) and place the animated object in it. Now if you change the coordinates of the empty, the object will be animated where you want.

### Issue 2 : Play 2 animations simultaneously

To play 2 animations at the same time use the layers in the Animator, and do not forget to put the weights at 1 :
  
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Animator.png?raw=true "")


Ref :
https://docs.unity3d.com/Manual/AnimationLayers.html
https://answers.unity.com/questions/741357/play-two-animation-simultaneously-using-animator.html


# 5.	Placing objects from image tracking
When we use the Image Tracking function of AR Foundation, the spawned prefab does not place itself intuitively regarding the position of the recognized image. To solve this we have to follow this :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/ImageTrackingPosition.png?raw=true "")


The most important part is to create a representation of the detected image in our prefab (with a size 10 times smaller) rotated at 180° on the Y axis, and place the other objects regarding this. 
This way you can visualise how the objects will be spawned in real life.

Example :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/ImageTrackingPositionTest.png?raw=true "")

Above you can see how the prefab is in Unity, and below how it is spawned in real life :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/ImageTrackingPositionTest2.jpg?raw=true "")


# 6.	Transitions


## Chapter Transitions : 

Chapter Transitions is the script we created to assure the transitions between scenes or chapters of the story.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/ChapterTransitions.png?raw=true "")


As you can see on top, the script needs to take as variables a Current Animator : which has the last animation of the scene, and a Transition : the events that will be triggered when the conditions of the script are filled.
The if loop sees if the current animation of the Current Animator has finished ( normalizedTime >1, = 0 : the animation did not start, and between 0 and 1 it is playing), and if the name of the animation is “End”. 
For example, if we use the script at the end of the chapter 1 of the scene 8 (8-1), we would have to do as shown bellow :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/ChapterTransitions2.png?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/End.png?raw=true "")


## Enable Plane Tracking :


At the beginning of our application, we use Image Tracking, but later we have to use Plane Recognition. To realise this transition we created the EnablePlaneTracking script. 
This script enables the Plane Tracking Manager of AR Session Origin, along with the TapTt script. Then, the code starts the UIEvents (defined by the user, such as the apparition of 2D UI inviting the user to find a plane) when a plane is detected. When the object is spawned, the Plane Tracking Manager and the TapTo script are disabled again, and the OnceSpawned events are set active (such as the deactivate the 2D UI).

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/EnablePlanetracking.png?raw=true "")

As you may have guessed this script works with the TapTo script. 
This script is the one that manages the apparition of the new prefab on the ground. 
It detects where the user touched the ground, and if it is on a detected plane it spawns the selected object at this location.
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/TapTo1.png?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/TapTo2.png?raw=true "")


## Activate S11 : 


At the beginning of our application we use Image Tracking, and the prefab of the first animations are spawned directly by the Image Tracking script of AR Foundation. 
However, when we stop the plane tracked scene, we need to come back to the location of the detected image. 
Unfortunately, if we activate again the image tracking to detect the same previous image we had some issues. 
Therefore, we thought about detecting the position of the previous spawned prefab instead. However, we did something simpler than that, we only spawn the new scene at the position (0 0 0) with a rotation of 180° on Y (cf how to position objects after image recognition) since we only play cinematics.


The Activate S11 script is the one that spawns the Scene 11 prefab from our assets :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/ActivateS11.png?raw=true "")
 

# 7.	Optimisation


To optimize our AR application, we followed this video :
Optimizing AR: how to extend battery life and avoid overheating - Unite LA - YouTube
Therefore, we reduced the FramesPerSecond (fps) from 60 to 30, by going in : Edit > Proj Settings > Time > Time Manager > Fixed Timestep to 0.0334 for a project with 30fp.

We also lowered the resolution by half, to 1080 on 2220. We used a script to do so : 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Opti1.png?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/SteetAR/Opti2.png?raw=true "")

 
All these configurations boost our battery life, and the heating of our cell phone.


# 8.	User Interface

Of course with children you don’t want to make a 2 hours long class. They need to be part of the show. It is why we put questions, even at the very beginning. Those are simple, with buttons and with canvas directly in Unity. That way there was no need of coding an application in android studio or anything that would have caused issues of compatibility with IOS.

We tried to incorporate responsive design : when the user clicks on one of the buttons to answer the questions, the sound is different if it is the good answer or not, also the good answers become green and the bad ones red.
For guiding there are both text and icons to make sure the user knows what to do. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/2DSigns.jpg?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Q1.jpg?raw=true "")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/Q2.jpg?raw=true "")


About sound, we learned how central it was in immersive application. Therefore, we added sounds linked to many objects, such as all the living characters. We synchronised them as much as possible with the characters’ movements to be realistic. Sounds are linked to objects and scenes so that they begin exactly with the animations. Moreover, the main lion (Alex) speaks the whole story. 
Furthermore, adding music seemed a perfect way to keep rhythm in the experience, and to enjoy even more the videos for instance. The introduction music while on the first menu enables the user to find the good volume. 

Finally, a script had to be done in order to deal with an object or scene with more than 1 sound, for instance with 2 comments from Alex, or to manage background sound and dialogues at the same time :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/TwoAudio.png?raw=true "")


At the end, we are happy with our application : we obtained an entertaining application, easy to use, and faithful to the fresco.

Try it yourself with this android version :



