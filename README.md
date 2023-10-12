![banner](https://github.com/lorainemnrc/rnn-machine-translation/assets/23328647/95d3f068-76d3-4086-86fb-553be5d8ea6c)

<h1 style="color: #1048CB"><b>Overview</b></h1>
<p align="justify"> &emsp;
Neural machine translation is an approach that utilizes neural networks to transform a sequence of words from a source language, such as English, into a desired target language, such as French. More formally, neural machine translation involves finding the target sentence, denoted as $y$, that maximizes the conditional probability of $y$ given the occurrence of a source sentence, denoted as $x$.
</p>

<p align="justify"> &emsp;
One approach for tackling this task is the sequence-to-sequence (*Seq2Seq*) framework, which is based on Recurrent Neural Networks (RNNs). In this framework, the RNN model processes an input sequence token by token and generates the output tokens in a similar sequential fashion.
</p>
For this exercise, we explore the use of Sequence-to-Sequence RNNs with Attention to translate texts from one language to another. Specifically, we have the following learning objectives:

<p align="justify"> &emsp;
1. Describe what neural machine translation is and how it is done using a sequence-to-sequence RNN with attention.
2. Describe the dataset being used in this example.
3. Describe the preprocessing steps being done in preparation for training the model.
4. Describe the postprocessing code/functions that have been created for performing inference and analyzing the model weights.
5. Compare and contrast the DecoderRNN and AttnDecoderRNN models in terms of loss, training time, parameter count, and quality of translation (qualitatively).
6. In the AttnDecoderRNN model, swap out the GRU for an LSTM. Compare and contrast the two models in terms of loss, training time, parameter count, and quality of translation.
7. Using the best model you’ve found, perform translation on some samples (4 at least) and compare the results with Google Translate. No need to quantitatively evaluate this comparison.
8. Plot the attention weights for the samples you chose and describe the results.
</p>

<h1 style="color: #1048CB"><b>Data Source</b></h1>

As an example, data on thousands of English-French translation pairs derived from the [`Tatoeba Project`](https://www.manythings.org/anki/) was used.

The dataset, `eng-fra.txt`, is a tab-delimited file consisting of 135,842 sentence pairs initially. This was reduced to 9,924 pairs with 4,165 French, and 2,661 English words, respectively.

<h1 style="color: #1048CB"><b>Highlights</b></h1>

In comparing different model variations, a RNN with attention using GRU (`AttnDecoderRNN`), and LSTM (`AttnDecoderRNN_LSTM`) have comparable results based on loss. `AttnDecoderRNN_LSTM` ran for 45 mins, had a 0.45 loss, and got 90% of the 10 sample sentences correct. Whereas `AttnDecoderRNN` ran for 43 min, had a 0.51 loss, and got 70% of the 10 sample sentences correct.

Although `AttnDecoderRNN_LSTM` achieved higher accuracy with a lower loss, it required a slightly longer runtime. Again, this shows that the choice between the two models would depend on the specific priorities and trade-offs of the translation task at hand.

In this case, LSTM may have performed better than GRU due its capability to capture long-term dependencies in sequential data which is achieved by using a "memory cell". Moreover, LSTMs have larger model capacity which allows to potentially capture more complext patterns and relationships in data. 
