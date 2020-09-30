# Image Caption Generation

The Flickr8k image data set can be obtained from https://github.com/jbrownlee/Datasets/releases/tag/Flickr8k

Background:
Given a image and five reference caption, an encoder-decoder architecture can be used to generate caption of the given image.

The encoder learns the compressed encoding features using Pretrained CNN architecture RESTNET and subsequently feed into a RNN / LSTM network.
The RNN/LSTM network uses sequence of words as input and output.



