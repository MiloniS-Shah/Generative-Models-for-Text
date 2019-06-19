# Generative-Models-for-Text
Building a generative model to mimic the writing style of prominent British Mathematician, Philosopher, prolific writer, and political activist, Bertrand Russell.<br>
<br>
Downloaded the following books from Project Gutenberg http://www.gutenberg.org/ebooks/author/355 in text format: <br>
i. The Problems of Philosophy <br>
ii. The Analysis of Mind <br>
iii. Mysticism and Logic and Other Essays <br>
iv. Our Knowledge of the External World as a Field for Scientific Method in Philosophy <br>
 
We train a LONG-SHORT TERM MODEL to mimic Russell's style and thoughts. <br>
Steps : <br>
i. Concatenate your text files to create a corpus of Russell's writings.
ii. Use a character-level representation for this model by using extended ASCII
that has N = 256 characters. Each character will be encoded into a an integer
using its ASCII code. Rescale the integers to the range [0,1], because LSTM uses a sigmoid activation function.
iii. Choose a window size, e.g., W = 100.
iv. Inputs to the network will be the first W-1 = 99 characters of each sequence, and the output of the network will be the Wth character of the sequence.
Basically, we are training the network to predict each character using the 99 characters that precede it. 
Slide the window in strides of S = 1 on the text.
v. Note that the output has to be encoded using a one-hot encoding scheme with N = 256 (or less) elements. This means that the network reads integers, but outputs a vector of N = 256 (or less) elements.
vi. Use a single hidden layer for the LSTM with N = 256 (or less) memory units.
vii. Use a Softmax output layer to yield a probability prediction for each of the characters between 0 and 1. 
This is actually a character classification problem with N classes. Choose log loss (cross entropy) as the objective function for
the network. 
viii. We do not use a test dataset. We are using the whole training dataset to learn the probability of each character in a sequence.
ix. Choose a reasonable number of epochs for training, considering your computational power.
x. Use model checkpointing to keep the network weights to determine each time an improvement in loss is observed at the end of the epoch. 
Find the best set of weights in terms of loss.
xi. Use the network with the best weights to generate 1000 characters, using the following text as initialization of the network:
    "There are those who take mental phenomena naively, just as they would physical phenomena. This school of psychologists tends not to  emphasize the object."
