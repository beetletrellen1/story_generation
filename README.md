# Story Generation

## Motivation

This project is an attempt to make children stories based on public domain
stories.  I am starting this project using stories from [Project Gutenberg](https://www.gutenberg.org/ "Project Gutenberg"), specifically "Grimm's Fairy"
and "Hans Christian Andersen Fairy Tales".  The overall goal is to have fun
using neural networks and hopefully learn a little bit with how they work.
In addition, I am looking to make a few short stories for my nephews to enjoy.

## Overview

The primary process being used is the [keras_RNN.py](https://github.com/beetletrellen1/story_generation/blob/master/keras_RNN.py). Running this will pull gather the definitions from [character_def.py](https://github.com/beetletrellen1/story_generation/blob/master/character_def.py)
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

## How Does This Work?

Taking a look at the SEQ_LENGTH within [keras_RNN.py](https://github.com/beetletrellen1/story_generation/blob/master/keras_RNN.py)
code, the network will learn read over the text in 50 character chunks to help
predict the next one.  

Example, having a sequence length of 10 the network could produce this:
```Good Morni > n
ood Mornin > g
```

This means in the 2.5Million characters within the data, there 2.5Million minus
the sequence length patterns to learn.  

## Why Do This?

Outside of just having fun and making a cool book for my nephews, using LSTM
recurrent networks helps us see how well a model can learn a problem and learn
more about the problem itself.  We can breakdown how well our model is learning
and apply similar methods to different problems like predicting words that
should be in children stories, or creating a summary of the articles, books,
and papers.

## Text Generation

Using the default settings, these are the texts generated.  


This is how it begins on the first training.  Categorical Crossentropy loss of
2.0121.  Pretty high loss rate.
```
the store and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and the store of the broad and the store of
the broad and the store of the broad and
```

Ten Trainings later.  Categorical Crossentropy Loss of 1.0438.  We are at least
full sentences and relatively proper grammar.  The last line is cut short because
I have only set to it to 1500 characters.
```
‘If you will not see you a stranded time, and I am the stranded boots," said the
stork-mamma. "It is a good thing to do so. In the street and the stranded
some stranded themselves in the streets of the stranded seas. Then she sat down
and said: ‘I am the first steamer in the world is to say, and then I shall be
able to follow themselves to my father and my mother and my boy." Then she fell
asleep. In the morning the stranded little boys were still alive. The stranded
little girl said the storks and the stranded souls. The stranded little boys
were still alive, and the stranded boats were all the stranded beautiful flowers.
The stranded little boys were still alive. The stranded little birds sang the
stranded sisters, and the stranded stranded themselves in the streets of the
stranded seas. Then she sat down and said: ‘I am the first steamer in the world
is to say, and then I shall be able to follow themselves to my father and my
mother and my boy." Then she fell asleep. In the morning the stranded little
boys were still alive. The stranded little birds sang the stranded sisters.
The stranded little boys were still alive. The stranded little birds sang the
stranded sisters, and the stranded stranded themselves in the streets of the
stranded seas. Then she sat down and said: ‘I am the first steamer in the world
is to say, and then I shall be able to follow themselves to my father and my
mother and my boy." Then she fell asleep. In the morning the stranded little
boys were sti
```

This is the 20th training.  It seems that due to the drop out in our LSTM,
occasionally it will get stuck in a loop.  
This is one of my absolute favorites though solely of the line "I shall be able
to move of the sun and moonlight," said the old man." It feels like this old man
has hidden wisdom for either Little Claus, or Hans.  Loss = 0.8199
```
Little Claus, as they said, ‘I will go with you.’

Hans takee this a visit, and I shall be able to move of the sun and moonlight," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.

"'The old man, you shall have my head with a beautiful bird," said the old man.
```

Thirty Epochs in with a loss of 0.7039. It seems to be leveling off with
learning and becoming more coherent. See below for new trainings to tackle this.

```
their hands and kissed
up in the forest. ‘What have you for diasones?" and he sprang to their hands,
which he found himself on the beach, the chief could not see if the last penny
of falling stars shall wrong with their nettles.

And the folliest stood still to correct them to be a dark, not only to be
enjoyed. In each hall have hearts taken of around him, the goblin was about to
close the same six he looked at the piece of fire. As the conversation came forth
from the fire, when the two words of the great heat, and their father was quickly
done.  Those were their own words to be seen; no one can see that he had been a
great toy was to be seen in their clothes as I know that as a good old, he canst
their rings, and travels to their eyes. Then she took their cheeks, and the
shepherd had stolen him to find how the love of the prince with their wings, and
their fingers with their heads in their hands, which he found himself on the
beach, the chief could not see in their lives of the love of the largest to be
kissed, for they were to try and make his way home. He has gone for heart to have
his father on the mountain. The forest had been placed on the grave of Heina, a
porterious tone of the church, which had been covered to him, and the lamp could
not imagine what was has to be carried in the swallow above the country of the
glasses. The loft trees were taken to their rings, and their father was getting
on till the passage below him say this evening. The world is nothing to me.'
```

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
