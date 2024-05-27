# Twitter_NER_Case_study

# Problem_staement
Twitter is a microblogging and social networking service on which users post and interact with messages known as "tweets". Every second, on average, around 6,000 tweets are tweeted on Twitter, corresponding to over 350,000 tweets sent per minute, 500 million tweets per day.
Twitter wants to automatically tag and analyze tweets for better understanding of the trends and topics without being dependent on the hashtags that the users use. Many users do not use hashtags or sometimes use wrong or mis-spelled tags, so they want to completely remove this problem and create a system of recognizing important content of the tweets.
Named Entity Recognition (NER) is an important subtask of information extraction that seeks to locate and recognise named entities.You need to train models that will be able to identify the various named entities.

# Data Description
Dataset is annotated with 10 fine-grained NER categories: person, geo-location, company, facility, product,music artist, movie, sports team, tv show and other. Dataset was extracted from tweets and is structured in CoNLL format., in English language. Containing in Text file format.
The CoNLL format is a text file with one word per line with sentences separated by an empty line. The first word in a line should be the word and the last word should be the label.
Consider the two sentences below;

Harry Potter was a student living in london
Albus Dumbledore went to the Disney World

These two sentences can be prepared in a CoNLL formatted text file as follows.

Harry B-PER
Potter I-PER
was O
a O
student O
Living O
in O
London B-geo-loc
Albus B-PER
Dumbledore I-PER
went O
to O
the O
Disney B-facility
World I-facility

# Preprocessing
Load data of train_sample and test_sample and schema(combination of all entity tags: Beginning and intermediate)
from the visuals, we see 'O' tag has the highest number count
Max_length:39 i.e. maximum number of words in a single tweet.
vacab_size 25382 i.e. Highest number of unique words in train and test samples.

# Train LSTM+CRF model:
Download Glove 200 dimension Twitter data embedding vector. Which were trained on Twitter data.
create an all_sentence list containing every sentence word only.
crf_tokenizer creates a word index based on word frequency after lowering every word in the all_sentence list.

# Embedding Matrix
prepare an embedding matrix of (21934,200) dimension. put all values 0 where words are not present in the glove vector.

# Create training Datasets
and create a tag2id dictionary to represent all tags with an id value.
prepare a one-hot encoding matrix of tags for every sentence with maximum length. Padding to 0 where max len does not meet. And put 0 for all padding. DO it for train and test samples.

# Training model
Train the model with embedding matrix, 2 bidirectional LSTM, time_distributed dense layer and CRF layer.And then train the model with 300 epochs and train stop early in 81 epoch with val_loss : 0.0033
Got avg accuracy of the model on the test set is 0.986

# BERT
Load the Bert base uncased model . Load Bert auto tokenizer i.e. tokenizer for BERT. 
The tokenizer splits the sentence into tokens and subtokens and puts a unique input ID. These IDs with special tokens like [CLS] (classification) and [SEP] (separator) form the input sequence that is fed into the BERT model for processing. I did it for training and test samples.
Run the model with 10 epochs in training data and got a fantastic accuracy with 0.99.





