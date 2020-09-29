---
title: "Post 2: Lab 1"
date: 2020-09-29T22:35:13+02:00
draft: false
---

Hello everyone !

# Lab 1

## Lab a: Setup Blog

It is my first blog, and my first time using a static site generator. 
For simplicity, I chose to use the one advised by my professors : Hugo. 

I started following the slides from this lab, and I created this site.

![alt Text](https://user-images.githubusercontent.com/71452847/94617856-91475880-02aa-11eb-9285-4a46f4db9500.png "Creation of the site")

Then I added the gitignore (just an empty .txt file, because fisrt I used an exemple from an Hugo site but it gave me a hard time during deployment). 
Next step : the theme ! I chose the Ananke theme because it seemed beautiful and easy to use. 

![alt Text](https://user-images.githubusercontent.com/71452847/94617863-93a9b280-02aa-11eb-9311-f9c935f1fd7d.png "Ananke theme")

I played a little with Hugo : I created my first post and studied a little the Markdown syntax.
Then, I plunged into the most difficult part for me : the deployment ! 
I chose to deploy the site on my own GitHub, and even though I already used Git for previous projects, I struggled a little to get back on it !

Thanks to all the documentation on the internet, I was able to : create an SSH key, figure out how to copy it from my windows' shell, create my remote repesitory for the project on GitHub, and set the origin of my local file to the remote repisotory :

![alt Text](https://user-images.githubusercontent.com/71452847/94617959-ba67e900-02aa-11eb-9447-54141d762552.png "Remote git repesitory")

I finally did my first commit :

![alt Text](https://user-images.githubusercontent.com/71452847/94617963-bc31ac80-02aa-11eb-8edc-b7d203abfe52.png "Commit")
![alt Text](https://user-images.githubusercontent.com/71452847/94617973-bf2c9d00-02aa-11eb-96d2-d5a50e236255.png "Push")

Along with some arrangements to use a project pages (publishDir to the config.toml, set the baseUrl, and set the docs folder as the source of my blog's pages)

![alt Text](https://user-images.githubusercontent.com/71452847/94617978-c0f66080-02aa-11eb-847c-ee6808abe634.png "Docs")

I was a little afrfaid first because when I went to the baseUrl link my blog did not look at all like it did during my local testing :

![alt Text](https://user-images.githubusercontent.com/71452847/94617984-c2278d80-02aa-11eb-843a-74e0c798bf03.png "Execute")

It was because I forgot to execute hugo before my commit ! 

Finally, the only issue remaining about my blog was the impossibility to put an image.
I used the adequate Markdown syntax, and the folder organisation recommended, but the process coud not find my images in the folders hosted in my github.
So I bypassed the problem, by putting my images in GitHub "issues", and using the link given to show my images. And it works !

[comment]: <> (![alt Text](https://user-images.githubusercontent.com/71452847/94618476-85a86180-02ab-11eb-9a2f-bac6a2e711d0.JPG "Execute"))
