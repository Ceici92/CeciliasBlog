---
title: "Lab 1"
date: 2020-09-29T22:35:13+02:00
draft: true
---

Hello everyone !

# Lab 1

## Part a: Setup Blog

It is my first blog, and my first time using a static site generator. 
For simplicity, I chose to use the one advised by my teachers : Hugo. 

I started following the slides from this lab, and I created this site.

![alt Text](https://user-images.githubusercontent.com/71452847/94617856-91475880-02aa-11eb-9285-4a46f4db9500.png "Creation of the site")

Then I added the gitignore (just an empty .txt file, because first I used an example from an Hugo site but it gave me a hard time during deployment). 
Next step : the theme ! I chose the Ananke theme because it seemed beautiful and easy to use. 

![alt Text](https://user-images.githubusercontent.com/71452847/94617863-93a9b280-02aa-11eb-9311-f9c935f1fd7d.png "Ananke theme")

I played a little with Hugo : I created my first post and studied a little the Markdown syntax.
Then, I plunged into the most difficult part for me : the deployment ! 
I chose to deploy the site on my own GitHub, and even though I already used Git for previous projects, I struggled a little to get back on it !

Thanks to all the documentation on the internet, I was able to : create an SSH key, figure out how to copy it from my windows' shell, create my remote repository for the project on GitHub, and set the origin of my local file to the remote repository :

![alt Text](https://user-images.githubusercontent.com/71452847/94617959-ba67e900-02aa-11eb-9447-54141d762552.png "Remote git repository")

I finally did my first commit :

![alt Text](https://user-images.githubusercontent.com/71452847/94617963-bc31ac80-02aa-11eb-8edc-b7d203abfe52.png "Commit")
![alt Text](https://user-images.githubusercontent.com/71452847/94617973-bf2c9d00-02aa-11eb-96d2-d5a50e236255.png "Push")

Along with some arrangements to use a project pages (publishDir to the config.toml, set the baseUrl, and set the docs folder as the source of my blog's pages)

![alt Text](https://user-images.githubusercontent.com/71452847/94617978-c0f66080-02aa-11eb-847c-ee6808abe634.png "Docs")

I was a little afraid first because when I went to the baseUrl link my blog did not look at all like it did during my local testing :

![alt Text](https://user-images.githubusercontent.com/71452847/94617984-c2278d80-02aa-11eb-843a-74e0c798bf03.png "Execute")

The difference existed because I forgot to execute hugo before my commit ! 

Finally, the only issue remaining about my blog was the impossibility to put an image.
I used the adequate Markdown syntax, and the folder organisation recommended, but the process coud not find my images in the folders hosted in my github.
So, I bypassed the problem, by putting my images in GitHub "issues", and using the link given to show my images. And it works !

[comment]: <> (![alt Text](https://user-images.githubusercontent.com/71452847/94618476-85a86180-02ab-11eb-9a2f-bac6a2e711d0.JPG "Execute"))


## Part b: Setup Unity

I already had Unity, because I used it last year for a project. However I did not have the last version so I uploaded Unity 2019.4 on my Unity Hub. (I also installed Unity 2020.1 because we need it for Lea's class)

![alt Text](https://user-images.githubusercontent.com/71452847/95072832-1d72d900-070c-11eb-8b71-978f17171248.JPG "Installing the new versions")

I created a new Unity 3D project.

![alt Text](https://user-images.githubusercontent.com/71452847/95072753-fa482980-070b-11eb-9dee-05c37cc2484c.JPG "New 3D Project")

I already knew the basics : create an object, change its size, its location, the parent-child relation, etc... Therefore, I directly started by playing around with an exemple.
I went on the unity learn page, and I chose the FPS microgame :

![alt Text](https://user-images.githubusercontent.com/71452847/95072755-fae0c000-070b-11eb-95f2-53562e6afca3.JPG "FPS Microgame")

I started playing a little to discover it :

![alt Text](https://user-images.githubusercontent.com/71452847/95072758-fb795680-070b-11eb-8dad-ff97d06654a8.png "Playy")

I looked into the prefabs of the game, and I added a new room.

![alt Text](https://user-images.githubusercontent.com/71452847/95072759-fb795680-070b-11eb-8d19-216f305b1d84.png "Prefabs")

![alt Text](https://user-images.githubusercontent.com/71452847/95072750-f9af9300-070b-11eb-9782-ad07664fffb8.png "Room")

During the next weeks, if I have the time before the evaluation, I will add some IP Paris flavor to the game.