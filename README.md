# AI
## Test Summarization
Text summarization is an NLP application that generates a concise and insightful summary of a lengthy paragraph, allowing us to quickly grasp the essence of the subject. Automatic text summarising is essential to better support the discovery of relevant information and access meaningful data.

## Types of Text Summarization
1. *Abstrative Based*: In Abstractive based, we produce new phrases from the original text . It's possible that the sentences produced by abstractive summarization are missing from the source material.

2. *Extractive Based*: In extractive based, we only extract the text that contains the significant lines or phrases from the original text. That compiled text would serve as our summary.

## Problem Statement
Long and detailed reviews from customers are common. Manually assessing these evaluations takes a lot of work. Natural language processing can be used to create a succinct summary for in-depth reviews.
Our goal is to provide a summary for the "Amazon Fine Food Reviews" utilizing text summarization techniques that are abstraction-based.

Data Scource: [Kaggle](https://www.kaggle.com/snap/amazon-fine-food-reviews?select=Reviews.csv)

## Project pipeline
1. Understanding Text Summarization
2. Text pre-processing
3. Abstractive Text Summarization using LSTM, ENCODER-DECODER architecture
4. Web scrape an article using BS4
5. Extractive Text Summarization using Transformer
***
## Text cleaner
It preprocesses text to remove HTML tags, converts alphabetic characters, tokenizes words, and joins them back into a string.
 ***
## Summary cleaner
Tokenizes text, removes short words, joins cleaned words back into string.
***
## Tokenizer and dictionary creation
Create a dictionary to map each unique word in the training data to an integer, iterate through each review text, pad integer sequences with zeros, and add 1 to the word_dict size to calculate vocabulary size.
***
## Encoder Decoder
Three LSTM layers encode the input sequence, with the output of the last layer used for decoding. The attention layer helps the decoder focus on relevant parts of the input sequence, producing output vectors the same length as the encoder input sequence. The RMSprop optimizer and sparse categorical cross-entropy loss are used to train a neural machine translation model for 50 epochs with a batch size of 512. Two dictionaries are created to map words to integer indices and vice versa, converting model indices into target language words.

![encoder decoder](https://github.com/aunali1932/project-text-summary/blob/main/Screenshot%202023-05-09%20024835.png)

![encoder decoder]([https://github.com/mnm2401/test/blob/main/Screenshot%202023-05-09%20025751.png](https://github.com/aunali1932/project-text-summary/blob/main/Screenshot%202023-05-09%20025751.png))
***
## Encoder Decoder Inference using Softmax
Inference models for encoder and decoder are used to predict translations, taking encoder_inputs, hidden state, and cell state. Attention is used to pass decoder_hidden_state_input and outputs2 through the attention layer and concatenated tensor through the decoder_dense layer. Moreover, The function decodes a single input sequence using a trained encoder-decoder model, generates an empty target sequence, predicts the next token, and returns the decoded sentence.
***
## Seq2summary
Seq2summary and seq2text are functions used to convert sequences of tokens into their original text form. Seq2summary iterates over a sequence of tokens to check if it is present in the reverse_target_word_index dictionary and joins the list of words to form a string. Lastly, we use a trained model to generate summaries for validation examples, printing the review text, original summary, and predicted summary
