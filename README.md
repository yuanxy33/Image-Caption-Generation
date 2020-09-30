# Image Caption Generation

<h3>Background</h3>
Given a image and five reference caption, an encoder-decoder architecture can be used to generate caption of the given image.

The figure below shows an image with the given reference text

![Image1](https://user-images.githubusercontent.com/67460572/94655314-f5146480-0330-11eb-8626-10f3b7c66bb5.PNG)


<h3>Data Set</h3>
The Flickr8k image data set can be obtained from https://github.com/jbrownlee/Datasets/releases/tag/Flickr8k

<h3>Methods</h3>
The encoder learns the compressed encoding features using Pretrained CNN architecture RESTNET and subsequently feed into a RNN / LSTM network.
The RNN/LSTM network uses sequence of words as input and output.

![image](https://user-images.githubusercontent.com/67460572/94655544-55a3a180-0331-11eb-8f86-c2c5d13ca8e2.png)

Encoder extracts image features using the modified resnet-152 pretrained model and feed into the decoder. The image needs to be resized and normalized to 224x224 as per the input of the resnet-152. 

Next, the caption in the data set was cleaned by removing punctuation and lower-case the text. This is to ensure the word embedding only embed the text and ignore the variation of capital and lowercase. A vocab size of 3421 was built on words appears more than 3 times in the caption. The dataset was split into train and testing data were split into ration of 95:5. The word is vectorized into one-hot encoded words.

The decoder then uses the one hot representation of the caption and the features vector as the input to train the model. The loss of RNN and LSTM decreased on every epoch. This is because the feed-backwards network in both networks are learning from the gradient descent backpropagation.

The quality of the generated caption is evaluated through BLEU score (reference: https://machinelearningmastery.com/calculate-bleu-score-for-text-python/#:~:text=Crash%2DCourse%20Now-,Bilingual%20Evaluation%20Understudy%20Score,in%20a%20score%20of%200.0.)


<h2>Result</h2>

![RNNLSTM loss](https://user-images.githubusercontent.com/67460572/94655420-22f9a900-0331-11eb-802f-914d66d21e03.PNG)

The loss in RNN & LSTM drop with epochs, indicating the network is learning. The loss of RNN and LSTM has roughly the same pattern, both drop drastically from 8 to 3 from after first epoch finally reached around 2.3 after 5 epochs. As expected, the BLEU score is terrible before training the model. The output is determined by random initialization of the weight in the neural network.

Evaluating the performance while training, RNN BLEU scores are in the range of 0.41-0.57 while LSTM are in the range of 0.43-0.67. For the second image, RNN scores ranging from 0.41-0.56 while LSTM ranging from 0.39 – 0.73. This suggest that LSTM has a higher BLEU scores than RNN.

![caption generated per epoch](https://user-images.githubusercontent.com/67460572/94650849-0ad25b80-032a-11eb-8811-4de6c0afbb8f.PNG)

The BLEU score generally increased with more training. 

