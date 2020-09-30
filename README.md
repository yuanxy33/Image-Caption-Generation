# Image Caption Generation

The Flickr8k image data set can be obtained from https://github.com/jbrownlee/Datasets/releases/tag/Flickr8k

Background:
Given a image and five reference caption, an encoder-decoder architecture can be used to generate caption of the given image.

The encoder learns the compressed encoding features using Pretrained CNN architecture RESTNET and subsequently feed into a RNN / LSTM network.
The RNN/LSTM network uses sequence of words as input and output.

The quality of the generated caption is evaluated through BLEU score (reference: https://machinelearningmastery.com/calculate-bleu-score-for-text-python/#:~:text=Crash%2DCourse%20Now-,Bilingual%20Evaluation%20Understudy%20Score,in%20a%20score%20of%200.0.)

Result:
![RNNLSTM loss](https://user-images.githubusercontent.com/67460572/94650435-47ea1e00-0329-11eb-9d7f-31e01f455640.PNG)
