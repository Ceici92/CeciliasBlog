---
title: "RNN Part 2: The laboratory"
date: 2020-12-18T12:41:10+01:00
draft: true
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/RNN.png?raw=true"
---

This post is the second part of my evaluation for the Recurrent Neural Network class. 
I am going detail what I did during the laboratory.


The lab consisted in implementing a RNN for image captioning, you can find the code on the  Google Collab here :
https://colab.research.google.com/drive/1qft4rTOrA_FAP6kAPhAMfDisNmcfUh-r#scrollTo=0slnzwntg3Xp

I completed it with all that we have seen during the class, and I tried to train the model by my own.

As an input of the model , I must give images and their partial caption input, and as the expected output the words to predict.


So first I tried this way :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-2/Inputs1.JPG?raw=true "Inputs1")


But I got the following error :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-2/Error1.JPG?raw=true "Error1")

So I added dtype=np.float to the creation of arrays, however I got a new error in my processing data :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-2/Inputs2.JPG?raw=true "Inputs2")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-2/Inputs2bis.JPG?raw=true "Inputs2bis")


It must come from the fact that X is composed of two lists of 2 different sizes

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-2/Inputs3.JPG?raw=true "Inputs3")

So I converted the partialCaption to the size of the imageInput with padding, but I got a new error while training :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-2/Error3.JPG?raw=true "Error3")

If I do what is asked by the error, I would turn back to the first error. 
Therefore I did not succeed in training the model with a small dataset. 