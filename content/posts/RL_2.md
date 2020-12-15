---
title: "Reinforcement Learning : Part 2"
date: 2020-12-15T18:14:31+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Part2.png?raw=true"
---

This post is the second part of my work for the Reinforcement Learning labaratory.
I presented the reinforcement learning model in the previous post, and here I am going to explain what I changed in the model to see the impact of the different parameters.

# Part 2 : Manipulations

## First test 

I conducted a first training with the basic following parameters :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/FirstStep.png?raw=true "First Test")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/FirstStep2.png?raw=true "First Test 2")

And I looked at the first results without changing any of those parameters :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/FirstStep3.png?raw=true "First Test 3")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/FirstStep4.png?raw=true "First Test 4")


The loss varies a lot, because the training dataset is changing over time. If we look at the score, it seems stable around 12.


## The Training Algorithm

To observe the impact of the training algorithm on the results, I changed it to Sarsa and conducted another evaluation :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Sarsa.png?raw=true "Sarsa")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Sarsa2.png?raw=true "Sarsa 2")

The new Sarsa algorithm did not impact a lot the resulting score of the system, it stays around 12.
So I went back to QLearning and I tried changing other parameters.


## The Doer 

I changed the Doer to randomly to look at the impact on the results. 
The score becomes quite hight (around 23), however we observe that it is more stable because in this case the model does not learn :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Doer.png?raw=true "Doer")

I turned it back to the previous Doer to keep observing the influence of the other parameters.


## The Experience Replay

To obtain better scores, I first changed the width of the network. 
With a capacity of 16 the network was not going to be able to learn enough to reach higher scores. 
Therefore, I augmented the width of the network to 128. Besides, I diminished the gamma to 0.90, added more Experience Replays, and augmented the buffer size in order to let the system remember more transitions at the same time :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ER.png?raw=true "ERBis")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ER.png?raw=true "ER")

The score is much higher, it almost reaches 40 and then varies around 20. However, even if at the beginning the model seem to learn and progress, its score starts to decrease around the 300th iteration. Our model reaches its second wall.


The loss is also smaller :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ER2.png?raw=true "ER2")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ER3.png?raw=true "ER3")


## The Reward Function

I augmented the batch size of the Experience Replays to try to improve the results.
Then, I changed the reward function as following :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Reward1.png?raw=true "Reward")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Reward2.png?raw=true "Reward2")

The system starts with low scores and improves until reaching a score around 50, before fluctuating a lot, and going down to a score of 20.

I conducted another evaluation with exactly the same parameters. 
Once again, we can observe that the system improves until a hight score (81) and then goes down to a score of 15. 
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Reward3.png?raw=true "Reward3")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Reward4.png?raw=true "Reward4")

Besides, we observe that some episodes last more than 100 iterations since the score does not change, as you can see on the highlighted scores above. 
The model has reached another wall. 
However we also observe huge decreases of the reward and the score : it comes from the fact that the model enters a new area of environment and it forgets how to behave at the beginning of a episode. 



## The Dataset

The manipulation of the training dataset is also what enables the system to reach such high scores, it was already set to only train the system every 3 time steps :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Dataset.png?raw=true "Dataset")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/Dataset2.png?raw=true "Dataset")

On top, we can see the results with the same parameters but with basic utilisation of the dataset.
The system does not success in reaching a higher score than 30, because it does not have time to gather enough data. 
This is why training the model only each 3 iterations, enables the system to gather more data before training, and therefore to improve its choices.



## The Activation Function

Finally, I changed the activation function from Sigmoid to LeakyRelu, to see the impact on the system :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ActivationF2.png?raw=true "ActivationF")

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ActivationF2.png?raw=true "ActivationF2")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_2/ActivationF3.png?raw=true "ActivationF3")

The results are not better, it is the contrary : the score fluctuates from 25 to 15. 
Therefore the Sigmoid function seems more suited for this model.


We could also change the value of the epsilon to observe the influence of the amount of exploration on the performances of the system.
