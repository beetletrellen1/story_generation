# Story Generation

## Motivation

This project is an attempt to make children stories based on public domain
stories.  I am starting this project using stories from [Project Gutenberg](https://www.gutenberg.org/ "Project Gutenberg"), specifically "Grimm's Fairy"
and "Hans Christian Andersen Fairy Tales".  The overall goal is to have fun
using neural networks and hopefully learn a little bit with how they work.
In addition, I am looking to make a few short stories for my nephews to enjoy.

## Overview

The primary process being used is the [keras_RNN.py](https://github.com/beetletrellen1/story_generation/blob/master/keras_RNN.py).  
Running this will pull gather the definitions from [character_def.py](https://github.com/beetletrellen1/story_generation/blob/master/character_def.py)
to process the data in the data directory.  Currently I have two different
directories for people to use in the data directory, but this will be updated
from time to time.  ["THE LITTLE MERMAID"](https://github.com/beetletrellen1/story_generation/tree/master/data)
is a little too short to be trained on, but it can be used once model is trained
and weights are saved.

## Simple Breakdown

In the [character_def.py](https://github.com/beetletrellen1/story_generation/blob/master/character_def.py),
it houses definitions to generate text and load data. The text generator captures
a random character then predicts what the next character would be based on the
probabilities of how the neural network trained. Load data pulls the data from
the data directory, tokenizes it based on a character to character base.  

The [keras_RNN.py](https://github.com/beetletrellen1/story_generation/blob/master/keras_RNN.py)
pulls in the arguments, has default settings that can be adjusted on the command
line.  The goal is to us LSTM to help the network remember the most recent
character and learn past that what the next character should be.  Default set
to one hidden layer and 500 nodes, seems to output relatively coherent sentences
within 8 Epochs of training.  

## Current Challenges

As of right now, I am struggling to have the weights loading to have an effect
on the model when restarting it with loaded weights. In addition, the
[test.txt](https://github.com/beetletrellen1/story_generation/tree/master/data)
is not completely cleaned and does not need to be adjusted.

## Future Goals

Currently I am using character to character mapping, but I would like to see how
word to word works and try morpheme to morpheme.  In addition, I do not know how
it currently works, but I will be using [Deep Dream Generator](https://deepdreamgenerator.com/ "Deep Dream Generator") to make pictures that use neural nets to take photographs
and transform them into artwork.  As stated in the motivation, the goal is to
make a book for my nephews.
