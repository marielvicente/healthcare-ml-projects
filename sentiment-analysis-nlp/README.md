# Sentiment Analysis of Customer Reviews

Can a neural network tell whether a customer review is positive or negative from the text alone?

## Data

[Sentiment Labelled Sentences](https://archive.ics.uci.edu/dataset/331/sentiment+labelled+sentences) from the UCI Machine Learning Repository: 2,748 reviews from Amazon, IMDb, and Yelp, each labeled positive or negative. The classes are close to even (1,386 positive, 1,362 negative).

The data isn't included here. To run the notebook, put the three `*_labelled.txt` files in a `data/` folder next to it.

## Approach

1. Cleaned the text: removed non-letter characters, lowercased, tokenized, removed stop words, and lemmatized (NLTK).
2. Mapped words to integers with the Keras tokenizer (vocabulary size 5,272).
3. Padded every review to 26 words, the 95th percentile of review length, so a few very long reviews didn't force a lot of padding.
4. Split 80/20, stratified by sentiment.
5. Built a TensorFlow model: an embedding layer, global average pooling, two dense layers (100 and 50 nodes, ReLU), and a sigmoid output. Trained with binary cross-entropy, the Adam optimizer, and early stopping.

## Results

- Early stopping ended training at 7 of 20 epochs
- Test accuracy: 80% (loss 0.48)
- Training accuracy: 94%

The gap between training and test accuracy, and the validation curves leveling off, point to overfitting. Next I'd try dropout and different early stopping settings.

## Tools

Python, TensorFlow/Keras, NLTK, pandas, scikit-learn, seaborn
