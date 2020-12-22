---
title: "ACV : 3D Reconstruction of human poses"
date: 2020-12-01T22:29:50+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/ACVKhoa/GivenCode.JPG?raw=true"
---

In my Advanced Computer Vision class, I got a lab about the 3D reconstruction of human poses. 
The purpose is to The purpose of the lab is to implement the 3D reconstruction from multi-views of human pose on a calibrated system.

We were given various files, such as videos of each subjects, and the visual output of the reconstruction on each sequence of each subject.

I started by trying to run the reconstruction code given on the sequences of the subject Lea, to see what we were supposed to obtain :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/ACVKhoa/GivenCode.JPG?raw=true "Given Code")

We can observe that the joints are not exactly on the subject.


To put in place this 3D reconstruction from human poses on a calibrated system, I had to complete the following steps :

1 - Read the 2DTXT file and draw the keypoints on original video 

2 - Read the 3DTXT of any activity, the coordinates 3D has the reference on the first camera (camera 0th). Project these coordinates on the frame of the different camera frame Using the relative pose between cameras (pose_0_1.. etc) and camera's intrinsic parameters

3 - Triangulation the 3D keypoint by your own methods and creativity from multi-view of keypoints on each frame

4 - Optimization to have a smooth result


Unfortunately, I was not able to implement it.
