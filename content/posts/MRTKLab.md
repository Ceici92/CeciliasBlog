---
title: "MRTK Application"
date: 2021-01-29T19:04:04+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/Feature.png?raw=true"
--- 


For the AR class I created an MRTK application on Unity. 

The goal of the app is the following :
*“We are in 2027. You are the CEO of an AR startup.
Today is the Paris Motor Show.
You had the chance to make a deal with the organizers of the event.
You are demonstrating your AR application to the public. 
A good review of the visitors will get you a big fat contract with the Paris Motor Show.”*

 
I described below the different aspects of my application and how I produced them.
As for the set up of an MRTK application, I followed the Microsoft tutorial available here :
https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01

You can also find the documentation about the MRTK example package here :
https://github.com/microsoft/MixedRealityToolkit-Unity


0. Creating the environment

To give the impression of being in a real Paris Motor Show, I created a big white floor with a red carped on top, and added some cars from the Unity Asset Store.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/0Environment.png?raw=true "Images 1")


# 1. Welcome Menu

When the user arrives to the Paris Motor Show, he is welcomed with the following panel :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/1Welcome.png?raw=true "") 

Instead of the Unity UI facade, ** 3D components and 3D text ** are more suited for mixed-reality applications. 
Therefore, on the following image you can see a 3D TextMesh Pro text on a plane with the MRTK_Standard_TransparentCyan material.


In order to enable the Welcome menu to follow the user, I added to it the **SolverHandler** and the **RadialView** components, and set the Tracked Target to the head. 

The lerp times configure the time for the menu to updates its position and rotation, the min and max distances configure the distance from the user, and the min and max degrees correspond respectively to the min distance in degrees the panel will have from the user (such as an “offset” from the center of the view) and the distance allowed before the panel position updates.
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/1Welcome2.png?raw=true "")


Finally, the “Continue” button is the “Button” prefab from the MixedRealityTookit-Unity Examples package.
It is set as a normal button, and triggers the apparition of the next panel.
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/1Welcome3.png?raw=true "")



# 2. Collect Car Preferences

To collect the car preferences of the user I used another panel : 
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/2Preferences.png?raw=true "")

The only difference with the previous one is the type of button used.

This time the buttons come from the PressableButtonHololens2Bar3H MRTK example package.
This prefab is more suited for the use of several buttons, because it already has a Button **Collection** with a **GridObjectCollection** component, that allow us to easily control the positions of the buttons :
  
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/2Preferences2.png?raw=true "")


Originally a symbol is present in the middle of the buttons, but I choose to remove it by changing the material of the square icons to HolographicbuttonThinContent :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/2Preferences3.png?raw=true "")


# 3. Guide the user to the cars

Once the user chose his favourite car brand, two **solvers** are triggered.

A solver is a MRTK component that indicates the user the position of a selected object.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/3Guide.png?raw=true "")


To create those two, I took chevrons from the MRTK examples, and added to them a **Solver Handler** and a **Directional Indicator**.

The Solver Handler script defines the object that will be followed by the cheveron : the head for the first solver and the chosen car for the second solver.

The Directional Indicator script configures the object to point at : the car for both solvers.


# 4. Information about the car

Once the user is close enough to the car, the following options will appear :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/4Information.png?raw=true "")


## A. The trigger :
To trigger the apparition of the information panels when the camera is close enough of the car, I created a new empty game object called PlayerTrigger as a child of the Main Camera. I defined its tag to “Player” and added to it a box collider large enough. 
As for the car, I added to it a big box collider (it defines the space in which the player will be detected)  and the following script that I wrote :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/4Information2.png?raw=true "")


The script triggers the activation of the OnCollision event when the PlayerTrigger is detected, in this event I displayed the car information and I made the solvers disappear.

## B. The information
To display the information, I chose to use a panel (like the one for the welcome menu) to show the main characteristics of the car, and to use **Tooltips** to display information about specific parts of the car.

To create the Tooltips I used the prefabs of the MRTK package, the anchor represents the anchor of the line under the panel of the tooltip, and the pivot the position of the panel.


# 5. Interactions with the car 

## A. Colour Change 

Once close enough of the car, the user can choose to change the colour of the displayed car.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5Interaction.png?raw=true "")
 

So as you can see above, I created four buttons, each of a specific colour, if the user click on one of them the car will change its colour to correspond to the one on the button.
The example below show the result if the user choses the blue one.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5Interaction2.png?raw=true "")


To enable this colour change, I first created the buttons using the PressableRoundButton prefab from the MRTK example package, and I put them in an empty object with a GridObjectCollection component as seen previously. 

I struggled to change the colours of the buttons, it is not only necessary to change the colour’s material of CylinderContainer, I had to create a new **Colour Theme** for the button, as you can see below for the blue one :
   
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5Interaction3.png?raw=true "")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5Interaction4.png?raw=true "")


Next, regarding the car, I duplicated its body, and in the OnClick() buttons event I changed the material of the duplicate to new material with semi-transparent ones with the suited colours.


## B. The miniature
The miniature car next to the real car, is an **object manipulator**.
The user can grab it and manipulate it with one or two hands, to see the car on new angles.
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5InteractionB.png?raw=true "")


## C. Speech command to quit

Once the user wants to quit the application, he can say “Enable quitting” to make a balloon appear, which if he clicks on it will trigger the quitting panel.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5InteractionC.png?raw=true "")

To configure the **speech command** I made sure the Microphone capability was enabled in MRTK > Utilities > Configure Unity Project. Then, on the MixedRealityToolkit object in the scene, in the Input > Speech panel, I cloned the DefaultMixedRealitySpeechCommandsProfile and selected the new one as Input System. 

In the new profile I created a new **keyword** as showed below :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5InteractionC2.png?raw=true "")


Then, to control the speech commands, I created a new game object in the scene called “SpeechInputHandler”, I added to it the **Speech Input Handler** component and configured to display the balloon :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/5InteractionC3.png?raw=true "")


In the tooltip confirmation, I dragged a variant of the **SpeechConfirmation Tooltip** from the MRTK package.


As for the configuration of the **interactable** balloon, I used the balloon from the MRTK example package prefabs, and configured its interactable script to make it react on touch and trigger the rating panel.


# 6. The rating panel

Once the user clicks on the balloon, a new panel appears to make him rate the application between 0 and 5. 

The creation of the panel is similar as the car preferences panel seen before.

To end the experience, once the user rated the rated the app, a thank you message displays.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/MRTKLab/6Rating.png?raw=true "")