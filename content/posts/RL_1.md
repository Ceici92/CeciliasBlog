---
title: "Reinforcement Learning : Part 1"
date: 2020-12-15T14:59:24+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Part1.png?raw=true?raw=true"
---

In this post I will explain one of the laboratories I did this year about Reinforcement Learning. 
During this lab, we used a python code on Google Collab 
to manipulate a deep reinforcement learning network to solve the CartPole game : 
a game where a hammer must not fall. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Hammer.JPG?raw=true "Hammer Game")

In this first part, I am going to explain the different functions of the model, and in the second part in the next post, I will explain what I changed in the model to see the impact of the different parameters.


# Part 1 : Presentation of the model


First, we have the imports of the different objects needed to create our model. For example, gym is for the simulation of the Cart Pole game, and numpy is for the big amount of data used. 


## The QNetwork


The second Class creates the QNetwork used to implement the Qvalues of the model :


![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/QNetwork.png?raw=true "QNetwork")

We can already identify some parameters we will be able to manipulate : the width of the network (here at 64), the activation function set at sigmoid, and the number of hidden layers.

As in a supervised network, the dataset given will be taken as an input of the network, it will pass through the different layers of the model (the hidden layers are all the layers that are not the input and output ones). 
However, contrarily to a supervised network, the output of the layers is the score of each action of the agent at each state.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/QNetwork2.png?raw=true "QNetwork 2")

Since the basic Qnetwork only takes as an input the states, the python code returns a pair of a state and its given action as needed.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/QNetwork3.png?raw=true "QNetwork 3")

The Qfunction returns the Qvalue for the given state in input.


Then, the model is printed to verify that there is no problem, along with it results for 10 random states from the gym dataset :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/QNetworkTest.png?raw=true "QNetwork test")

We observe that the results are given in a matrix with two columns, each represents the qvalue of an action, and as we can see the action 1 is often the best because its qvalues are higher.


## The Doer

The Doer is the part of the agent that acts : it takes the qnetwork, evaluates it on an input state and decides which action the agent should keep in function of the output qvalues of the network. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Doer.png?raw=true "Doer")

One of its parameters is the epsilon set at 10%, it indicates the amount of time where the Doer behaves randomly. 
It designates the amount of exploration the model will do.


Then we test the Doer, and see that it choses the accurate action with the higher qvalue :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/DoerTest.png?raw=true "Doer test")



## The Experience Replay

This function encapsulates all the relevant data from the agent transitions : St (the previous state), At (the previous action), Rt (the reward), St+1 (the current state), and At+1 (the current action). 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/ExpReplay.png?raw=true "Experience Replay")

This function encapsulates all the relevant data from the agent transitions : St (the previous state), At (the previous action), Rt (the reward), St+1 (the current state), and At+1 (the current action). 
With the variable ID, the class identifies each transition, in order in the future to assign them a relevance correlated to their loss. 
Each transition also has a birthdate, to keep in mind their order.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/ExpReplay2.png?raw=true "Experience Replay 2")

The ExperienceReplay class encapsulates the list of transitions in an instance. 
One of the class parameters is the buffer size, that defines the number of transition that the system can hold at every time step. 

The two following parameters designate how the system will choose which transition it is going to keep. 
The weightBatches defines if we choose the more relevant transition (ie. the one that submits the less loss) or if we choose them uniformly (False). 
The SortTransition defines, when the batch is full, if the system removes the older transitions (False) or the one less useful (True).

In the sampleBatch method the system designates which transitions in the batch it will choose to train the network, in function of the parameters chosen previously.


To see how the class works, we print all the relevance of the transitions in an ER, and the ones kept in a batch :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/ExpReplayTest.png?raw=true "Experience Replay test")


## The Learner


This class trains a qnetwork with the batches from the Experience Replay class.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Learner.png?raw=true "Learner")


If we look at the parameters : gamma is the discounting factor, and the algorithm used to improve the network is either Sarsa or QLearning.

We observe that there is a target network that will be trained, and a frozen network that will be used to see the improvement of the network along the training.

Another variable in this class is the optimizer that is set to adam, it is another parameter that could be changed in the next part to observe its impact on the system.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Learner2.png?raw=true "Learner 2")

The learn method updates the equations of the algorithm chosen to improve the system. 
You can see circled in red the targeted qvalues, and at their left the current qvalues. 
The subtraction of those two defines the error of the system, which is used to define the loss of each transition.


The Sarsa algorithm looks at what the system did after (At+1) to define the target qvalues, so it is ON Policy, while the Q-Learning algorithm looks at the maximum, it is OFF Policy.


Then the system gets the batches and makes sure there is no aberration in the data. It extracts all the objects from the batches, and set the target network to train :
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Learner3.png?raw=true "Learner 3")

For every transition, step, iteration, in the batch, the qvalue becomes closer to the target qvalue of the algorithm.  

After the training, the results are displayed to observe the evolution of the batch :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/LearnerTest.png?raw=true "Learner test")
![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/LearnerTest2.png?raw=true "Learner test 2")


The loss is supposed to be smaller after the training, and circled in red we can observe the parameters of the batch at the beginning of the training.


## The Training Loop

The 7th class is the Training Loop. 
The model has been defined, and now it is time to train it to sruvive episodes of the game.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/TrainingLoop.png?raw=true "Training Loop")

The initialization of this class will be the core of our playground during the next part of this article, because there is a lot of parameters to change. 
The initialization concerns all the parameters of the model that will act during the training : the qnetwork, the doer, the learner, and the ERs list.

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/TrainingLoop2.png?raw=true "Training Loop 2")

At every iteration, the agent acts, the system adds a transition in the Experience Replay, this replay is used by the Learner class to improve the model, and the system updates the batch with better actions for the agent.


At each iteration we print the loss resulting from the action and the transition of the agent, along with the score in the game, and the epsilon :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/TrainingLoop3.png?raw=true "Training Loop test")


## The Evaluation

The 8th class is the Evaluation : it displays in a graphic the resulting score of the training of the system :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Evaluation.png?raw=true "Evaluation")


## The Renderer

Finally, the last class renders the movement of the agent during the episode, I did not run it because it took a lot of time.


![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RL_1/Hammer.JPG?raw=true "Renderer")
