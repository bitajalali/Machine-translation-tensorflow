# Machine-translation-tensorflow

In this project, we have produced a model for machine translation using an encoder-decoder structure including LSTM and GRU recurrent neural networks.
The figure below shows the structure of the encoder-decoder framework:
![Capture1](https://user-images.githubusercontent.com/115353236/200183144-4fb78f5f-93a8-44ed-8c12-c9658ec7e700.PNG)
You can download the used data set from this [link](http://www.manythings.org/anki/deu-eng.zip).<br> In this dataset, there are 200,519 pairs of English sentences
and their German equivalents. 
We have divided this data set into training and test data sets after loading using TensorFlow tools.
To implement this structure, we have first produced a custom model for the encoder, which includes an embedding layer, which will be mentioned in more detail later.
In this model, the output of the embedding layer for each word is sent to a recurrent network to be encoded. In the last step, 
the context vector from the encoder network will be sent to the decoder network. Next, the decoder model receives a context vector as input and produces a sentence 
in the target language with the same meaning as the input sentence using this context vector. The encoder model receives the context vector and previously generated 
words in each step and produces a feature vector. The generated feature vector is then fed into a dense layer and a Softmax layer to generate the probability distribution
of the next word at each time step. Note that the word with the highest probability is used as the next word in each time step.
We have used the BLEU score to evaluate the model. This method, which is implemented in the nltk library, takes the reference sentences in the dataset and the sentence 
produced by the decoder and calculates the similarity of the input sentence to the reference sentences. We have used the following command to calculate this score:

BLEU_score = nltk.translate.bleu_score.sentence_bleu([references], hypothesis)

In this project, we have trained the model once without using the embedding layer, i.e. by inputting one-hot vector directly to the model and once using the embedding 
layer provided by TensorFlow libraries. We also trained the encoder and decoder models once using the LSTM unit and once using the GRU unit. 
and we consider the decoder model once as one layer and once as two layers consisting of LSTM units.
