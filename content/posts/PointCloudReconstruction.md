---
title: "Point Cloud Reconstruction"
date: 2020-12-20T13:15:45+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Result1.png?raw=true"
---

The goal of this lab is to reconstruct a 3D object using 2D images, with the C3DC software.


First, I chose to reconstruct the following ladybird. So I put her in a room with homogenous lighting, and took images of it from various angles. However, the images cannot be unconnected, the algorithm was not able to match the feature points on the object and its background. Therefore I added a white sheet of paper beneath the ladybird, as you can see on the following images :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Images.png?raw=true "Images 1")

I tried to reconstruct the object with two set of parameters, but none of them worked, I still had the same problem :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Param1.png?raw=true "Param 1")
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Param2.png?raw=true "Param 2")

 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Error.png?raw=true "Error")


Two of the problems could be that the ladybird is a little reflective, and that the images did not captured a lot of the background, so the algorithm may not have been able to replace the object and identify its angles.


I decided to try with another object, a little mask of a lady with a hat :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Images2.png?raw=true "Images 2")


I used the same previous parameters :
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Param3.png?raw=true "Param 3")

The result is great : the mask is well reconstructed. However, some points are missing, such as the part below the hat, it may be because the angle of the images did not show this part a lot. 
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Result1.png?raw=true "Result 1")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Result2.png?raw=true "Result 2")


I tried to run a new reconstruction of the model with a hight density of points, but the result is not as good. The upside is that we lost the majority of the background, however the mask is lacking a lot of points :
 
 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/PointCloud/Result3.png?raw=true "Result 3")
