---
title: "RNN: Part 1"
date: 2020-12-17T19:24:25+01:00
draft: false
featured_image: "https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/SentimentAnalysis.png?raw=true?raw=true"
---

I followed a class about Recurrent Neural Networks. 
In this first part I will explain what I learned from it, and in a second part in the next post I will explain the lab I did on the same topic.


# Part 1 : What is a Recurrent Normal Network

(All the images used come from my teacher's presentation.)

## Presentation

**A Recurrent Neural Network** (RNN) can, as any neural network, approximate a non-linear function by learning from the given data, in order to output the required vectors. 
Classic neural networks can only use as inputs fixed-size data, while RNN can handle **sequential data**. 


Sequential data is a collection ordered of objects, and a **Feed Forward Neural Network** (FFNN) cannot handle it well.


First, one way for the FFNN to deal with sequential data could be to use a **fixed size window** via. 
This type of RNN processes the sequences by word. It has a dictionary to identify if each word is neutral, positive, or negative, and then it calculates the mean over all the words to output a score. 
The problem with this technique is it does not handle the dependencies between the words nor their order.


Another way for the FFNN to process sequences could be to use **bigger fixed size window**. 
It labels group of words to understand better the context and the dependencies between words. 
However, labelling big groups of words is not easy, and this model still does not handle the share of parameters (similar words for example) between different parts of a sequence. 


Therefore, we use RNN : it can handle variable length vectors, the preservation of order, and the tracking of long-term dependencies. 
In the following parts I will explain how RNN does so, by presenting the Vanilla RNN, the LSTM, its applications, and the attention mechanisms.  



## Vanilla Recurrent Neural Network

One kind of RNN is the Vanilla. 
In the figure below, you can see all the types of sequence modelling problems it answers :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/RNN.png?raw=true "RNN")


The network is represented with green rectangles, the inputs in light blue circles and the outputs in dark blue circles. 
What we can keep in mind from this figure is that the Vanilla RNN is a flexible network that can process sequences of variable length.


To do so, the network applies the following recurrence relation at every time step : 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/Vanilla2.png?raw=true "Vanilla")


It conducts an internal loop to **recurrently** process sequences. 
In the figure, xt is a part of the input sequence, yt a part of the output and ht the internal state. 
The parameters of its function are the same as with a convolutional neural network (CNN): weights. 
However contrarily to the classic CNN, the Vanilla RNN uses the same parameters at every time step.


![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/Loss.png?raw=true "Loss")

As with a CNN, the goal is to minimise the loss function to improve the approximation. 
As you can see the loss is calculated at every time step, and then the mean is calculated to obtain the global loss. 


To improve the approximation of the Vanilla RNN, a **backpropagation through time** (BPTT) is conducted. 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/BPTT.png?raw=true "BPTT")

The system goes back in time to update the weights, and backpropagates errors to increase the accuracy of the neural network. 
Contrarily to a classic backpropagation, a BPTT conducts a more complex calculation of the gradient of the loss : it sums the gradients over time steps. 
The calculation follows the **chain rule** : the calculation of the loss at a time step (Lt) depends on the output (yt) and the cell state (ht) at the same time step.
The calculation of the gradient of the cell state (ht) depends on the gradients at the previous hidden states. 
Therefore, the gradient loss depends on the gradient cell state that comes from the multiplication of the same factor over and over. 


If this factor is higher than 1, the gradient loss will become very large and **explode**, and prevent the model from properly minimise the loss function. 
On the other hand, if the gradient is smaller than 1, the gradient loss will **vanish**. 


Therefore, the Vanilla RNN struggles to process long sequences and is not used in practice.  


## Long Short Term Memory (LSTM)

Another kind of RNN model is the **LSTM**. 
It has the same chain-like structure than the Vanilla one, however, its cell architecture changes, in order to manage information and gradient flow to avoid the vanishing gradient problem we saw before.


LSTM models are defined by two internal hidden states : the **hidden stat** (ht) and the **cell state** (ct). 
You can see their architecture below:


![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/LSTM.png?raw=true "LSTM")

The first one is used to make decisions over short periods of time, while the second one is used to fight the vanishing gradient issue and to track long term dependencies. The cell state is like the memory of the cell.


On the graphic above, you can also identify in pink the four gates used to control information : ft, it, gt and  ot. These four gates filter information. 
The **forget gate** (ft) decides which information should be kept or forgotten. 
The **input gate** (it) decides which value will be written to the current cell. 
The **input modulation gate** (gt) decides how much should be written in the current cell. 
Finally, the **output gate** (ot) decides what will be output from the cell.


Moreover, LSTM still uses **BPTT**, and the previous formulas to calculate loss and weights. 
However, LSTM resolves the vanishing gradient flow with a loss that is not only propagated by ht, but also by ct. 
The backpropagation is now gradient efficient. Therefore, it is widely used in practice. 


In practice, we use a **Multilayer RNN** or called Deep RNN, as you can see below :


![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/DeepRNN.png?raw=true "Deep RNN")


This architecture deals with more complex sequences and representations, the multilayer enables the model to extract diverse spatial features thanks to the different layers.


## RNN Applications

The first application of RNN models is the **Language Modelling**. 
RNN can be used to predict the next word of a sentence given its previous words. 
To do so, as input the RNN is given all the sentences, and for each hidden state one input is analysed at a time.
Backpropagation through time is also used to adjust the weights of the model :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/App1.png?raw=true "App 1")

The network can even be used to generate a whole text based on a given text structure.


Another application of RNN is **Image Generation**. 
The network can predict the value of the next pixels of a given image. 


The third application pf RNN is the **Sequence to Sequence**, for machine translation for example.
A sequence is given as input and a sequence is obtained as output, through two steps : a many to one architecture, and one to many architecture. 
The first one represents the **encoder**: it summarises the input, and the second one the **decoder**: it reads the decoder's output and creates the appropriate output sequence. 
You can find below an example in case of machine translation : 

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/Seq2Seq.png?raw=true "Seq2Seq")

It can also be used for image captioning with a CNN encoder and a RNN decoder, video descriptions, or Visual Question Answering (VQA).



RNN also presents limitations, the pre-processing work of the encoder on large dataset can be too long and become a bottle neck before the decoder. 
Therefore, RNN is not practical for real time approximations. To resolve this issue, another mechanism is added to RNN architectures:  the **Attention** mechanism.


## Attention in RNN

The **attention** is the ability to decide what to focus on. 
To learn a system needs time and attention, those two parameters are joined in the **memory** : the attention over time. 


To help RNN to focus on specific parts of data so it make predictions faster, two types of attention can be used.



The first one is the **Implicit Attention**. 
When the system learns new values of weight based on the loss feedbacks, it already mimics what a human would observe to fit best the data. 
So RNN already use this first kind of attention. 
To estimate this implicit attention, we can use a Jacobian, that will identify the part of the inputs that take an important role in the prediction. 


The second kind of attention is the **Explicit Attention**. 
It is the closer one to human attention, and it enables the system to reduce computations, understand better what the network is doing, and simplifies the sequential processing.


To implement it in an RNN, an additional set of output is conducted : an **attention model**. 
This model is applied on extra data and produces a feedback vector to the network at the next time step. 
As you can see below :

![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/Attention.png?raw=true "Attention")


Attention Models can be divided in two parts : hard ones and soft ones.
Hard attention models will use Reinforcement Learning to train the attention model, and soft ones will use backpropagation to train it. 



Different kinds of **attention models** exist : visual, location, self, content, collaborative, etc ...


One example of attention model is the **Sentiment Analysis**, that uses a pre-processing architecture and then an LSTM, on which it conducts backpropagation. 
In the example below, you can see how the attention model enables the RNN to focus on specific aspects of the text, like the quality of the services or the food, and also how it sees the relations between the different elements of the sentences :


![alt Text](https://github.com/Ceici92/CeciliasBlog/blob/master/docs/images/RNN-1/SentimentAnalysis.png?raw=true "Sentiment Analysis")

Some models get even rid of the recurrent property of the RNN, and only consider the attention mechanism. 
Those kinds of models are called the **Transformer**. 
They are formed of an Encoder and a Decoder architecture, and used what we call a **self-attention** mechanism. 
The transformers are multi-headed, they can track different types of attention, and therefore pay attention to different properties of a sequence at the same time. 
This model is for example used for the Alpha Star system that beats players in a strategy game.


I hope you understand better what an Recurrent Neural Network is, and I invite you to look at the next post, where I describe the RNN I implemented during a lab.
