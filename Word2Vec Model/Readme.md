# Skip-gram Model Implementation with Negative Sampling

This repository contains an implementation of the **Skip-gram model from scratch** using Python and NumPy. The Skip-gram model is used to learn word embeddings from a large corpus of text.


## Introduction

The Skip-gram model aims to predict context words given a target word. This implementation uses negative sampling to improve the efficiency of training. The loss function used is the cross-entropy loss. The model is trained on a large corpus of **Hindi** text with **vocabulary** above 9000 words. 

## Requirements
- Python 3.x
- NumPy

## Files in Directory
- We have **`pre_processed_corpus`** directory containing 4 corpora of text files on which the model is trained.
- **`Notes_Skip_Gram_Model.pdf`** contains my hand-written notes of the skip gram model.
- **`Skip_Gram_theory.pdf`** contains the lucid explanation of the theory of skip gram model with negative sampling. 
  


### Training the Model

To train the Skip-gram model, we have a corpus of text files.The model is trained with the following parameters:
- `vocab_size`: Size of the vocabulary
- `embedding_dim`: Dimension of the word embeddings
- `window_size`: Size of the context window
### Generating Text

After training the model, we can generate text based on the learned word embeddings. We will provide an input word and specify the number of words we want to generate.

### Example Code:

```python
# Load and preprocess the corpus
corpus_files = ['/path/to/corpus_1.txt', '/path/to/corpus_2.txt', '/path/to/corpus_3.txt']
corpus = ''
for file in corpus_files:
    with open(file, 'r', encoding='utf-8') as f:
        corpus += f.read()

# Train the model
model = SkipGram(vocab_size, embedding_dim)
model.train(corpus, window_size=5)

# Generate text
generated_text = model.generate_text('example_word', 10)
print(f'Generated text: {generated_text}')

