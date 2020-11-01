---
title: "Lab 1"
date: 2020-09-29T15:38:43+02:00
draft: false
---

Hello everyone !

During my first lab of HCI, I learned how to make a blog with the static site generator Hugo, how to deploy it with GitHub, and how to setup a Unity project. 

# Part 1 : Setup my Blog 

## First steps with Hugo

It is my first blog, and my first time using a static site generator. 
For simplicity, I chose to use the one advised by my teachers : Hugo. 
First, I downloaded and followed the steps detailed here : https://gohugo.io/getting-started/installing/ .

I created my Hugo site in a particular folder :

![alt Text](https://user-images.githubusercontent.com/71452847/94617856-91475880-02aa-11eb-9285-4a46f4db9500.png "Creation of the site")

I investigated the different existing hugo theme. 
I chose the basic one : Ananke, because it was aesthetic and easy to use. 
I first chose another theme but when I visited its GitHub, it seemed more complicated to put in place, due to other software used.

![alt Text](https://user-images.githubusercontent.com/71452847/94617863-93a9b280-02aa-11eb-9311-f9c935f1fd7d.png "Ananke theme")

Then, I wrote my first post on my Hugo blog, using the Markdown language in Visual Studio. 
The language is quite easy, and the Markdown Guide is complete. 
To inspire myself, I also looked at the config.toml and the scripts of the posts of the Ananke example site on GitHub.

![alt Text](https://user-images.githubusercontent.com/71452847/95682644-b01ce780-0be6-11eb-9dfd-7cd1ed071046.png "Config.toml")

I was able to test my blog locally with the command : hugo server -D.

![alt Text](https://user-images.githubusercontent.com/71452847/95682659-ca56c580-0be6-11eb-987e-853bc8b2ab5d.png "Blog first draft")

I changed the colours of the different pages of my blog to make it more fun.
To do so I follow the instructions of the ReadMe file :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab1/Colours.JPG?raw=true "Video")

When I was satisfied of what it looked like, I plunged into the most difficult part for me : the deployment ! 


## The Deployment

I used my own GitHub to deploy my blog. Once again a tutorial is present online : https://gohugo.io/hosting-and-deployment/hosting-on-github/.

Following my teacher's advice, I used Project Pages instead of User pages. This way, my project was linked to a collection in my GitHub, instead of being linked to my account.


I created my repository, initialized a git repository in my project folder, and configured the access with an SHH access. 
I created it in my local machine, following this tutorial : https://docs.gitlab.com/ee/ssh/.
However, with the tutorial command I was not able to copy the key, so I had to do it manually, by going in the correct file. 

![alt Text](https://user-images.githubusercontent.com/71452847/94617959-ba67e900-02aa-11eb-9447-54141d762552.png "Remote git repository")

Then, I setup my project to deploy my pages from a "docs" folder. 
I changed the config.toml file, and pushed my project :

![alt Text](https://user-images.githubusercontent.com/71452847/94617963-bc31ac80-02aa-11eb-8edc-b7d203abfe52.png "Commit")
![alt Text](https://user-images.githubusercontent.com/71452847/94617973-bf2c9d00-02aa-11eb-96d2-d5a50e236255.png "Push")

I enabled GitHub pages to use the docs folder :

![alt Text](https://user-images.githubusercontent.com/71452847/94617978-c0f66080-02aa-11eb-847c-ee6808abe634.png "Docs")

Then, little surprise, my blog on the baseUrl did not correspond to my blog on the lacalhost link :

![alt Text](https://user-images.githubusercontent.com/71452847/94617984-c2278d80-02aa-11eb-843a-74e0c798bf03.png "Execute")

It happened because I forgot to execute hugo before pushing, and because my first post was still tagged as a draft.
My blog was finally deployed !


But something was missing no ? The images !

## The Images

I tried using this command to add images to my blog, but it did not worked : 

Finally, the only issue remaining about my blog was the impossibility to put an image.
I used the adequate Markdown syntax, and the folder organisation recommended, but hugo could not find my images in the folders hosted in my Github.
So, I bypassed the problem, by putting my images in GitHub "issues", and using the link given to show my images.

![alt Text](https://user-images.githubusercontent.com/71452847/95682714-1144bb00-0be7-11eb-8df7-04f18e574e98.png "Issues")

Sometime after, I found a solution by adding "?raw=true" to the link of my images in GitHub. 

![alt Text](https://user-images.githubusercontent.com/71452847/95682585-397fea00-0be6-11eb-8d67-1feb51b35d00.png "Images")

I even found how to put a video on my blog. 
First, I tried to do the same process that I did for an image, but my video was too heavy to have a viewing raw in GitHub, so it did not appear on my blog.

Therefore, I reduced the time of the video to 12sec, putted it in the video file, and pushed it on Github. Still the video was too heavy to be visualised. 

Finally I decided to make it a gif, with Photoshop :

![alt Text](https://user-images.githubusercontent.com/71452847/95682577-31c04580-0be6-11eb-9e98-034b5e756476.png "Photoshop")

It worked ! The file could now be previsualised in git, it means that it can now be seen directly on my page, as you can see here :

![alt Text](https://github.com/Ceici92/HugoBlog3/blob/master/docs/images/Lab3/Lab3.gif?raw=true "Video")



# Part 2 : Setup Unity

I already had Unity because I used it last year for a project. However, I did not have the last version, so I uploaded Unity 2019.4 on my Unity Hub. (I also installed Unity 2020.1 because we need it for Lea's class)

![alt Text](https://user-images.githubusercontent.com/71452847/95072832-1d72d900-070c-11eb-8b71-978f17171248.JPG "Installing the new versions")

I created a new Unity 3D project.

![alt Text](https://user-images.githubusercontent.com/71452847/95072753-fa482980-070b-11eb-9dee-05c37cc2484c.JPG "New 3D Project")

I already knew the basics : create an object, change its size, its location, the parent-child relation, etc... Therefore, I directly started by playing around with an example.
I went on the unity learn page, and I chose the FPS microgame :

![alt Text](https://user-images.githubusercontent.com/71452847/95072755-fae0c000-070b-11eb-95f2-53562e6afca3.JPG "FPS Microgame")

I started playing a little to discover it :

![alt Text](https://user-images.githubusercontent.com/71452847/95072758-fb795680-070b-11eb-8dad-ff97d06654a8.png "Play")

I looked into the prefabs of the game, and I added a new room.

![alt Text](https://user-images.githubusercontent.com/71452847/95072759-fb795680-070b-11eb-8d19-216f305b1d84.png "Prefabs")

![alt Text](https://user-images.githubusercontent.com/71452847/95072750-f9af9300-070b-11eb-9782-ad07664fffb8.png "Room")
