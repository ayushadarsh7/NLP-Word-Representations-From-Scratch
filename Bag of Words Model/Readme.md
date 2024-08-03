# Bag of Words Model

* This repository contains the Python script to **crawl web pages, preprocess the text data, and generate a Bag of Words model.**
[![bag-of-words.png](https://i.postimg.cc/MKPZdCJR/bag-of-words.png)](https://postimg.cc/YhFwSy9q)
* The script performs the following tasks:

1. Crawling data from provided URLs.
2. Preprocessing the crawled data.
3. Generating a Bag of Words model from scratch.
4. Generating a Bag of Words model using scikit-learn.

## Requirements

- Python 3.x
- Requests
- BeautifulSoup4
- Pandas
- Scikit-learn

Install the required packages using:

```bash
pip install requests beautifulsoup4 pandas scikit-learn
```
## Directory information
* **`Bag_of_Words.ipynb`** is the jupyter notebook having all the code of the model.
* **`urls&crawled_data`** has the list of urls in **`urls.txt`** from where the data has been crawled.**`crawled_data.txt`** containing crawled data and **`preprocessed_data.txt`** contains pre-processed data after crawling.
* The crawled data is in **Hindi** language.
* **`pre_processed_corpus`** contains the pre-processed data divided into 4 corpora. Each corpus contains 2000 lines of text in **Hindi** language.
* **`Output`** contains the output of the model used.
  
## Output
* **`Bag_of_words_scratch.xlsx`** contains the output of word representations using the **bag of words** model whose code has been written from scratch, without using any pre-existing framework.
* **`Bag_of_words_scikit.xlsx`** contains the output of **bag of words** made using **scikit - learn** library.
* **`vocabulary_scratch.txt`** contains the **vocabulary(unique words)** obtained from the corpus using my model prepared form scratch.
* **`vocabulary_scikit.txt`** contains the **vocabulary(unique words)** obtained from the corpus using model prepared using **scikit-learn**.
