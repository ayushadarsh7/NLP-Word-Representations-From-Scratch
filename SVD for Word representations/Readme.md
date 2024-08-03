# SVD for word representations

This repository contains a Python script to perform **Singular Value Decomposition (SVD)** on a **Hindi** text corpus. The script reads the text data, creates a co-occurrence matrix, and then uses SVD to generate word representations.
[![svd.png](https://i.postimg.cc/wTrGj2dL/svd.png)](https://postimg.cc/jLzX8z2S)
## Requirements

- Python 3.x
- NumPy
- Pandas
- tqdm

## Repo Structure
- `SVD_Theory.md`: Contains the theory of **SVD** in detail with examples and sample code.
- `Corpus.txt`: Contains the Hindi text corpus.
- `SVD_on_Hindi_Corpus.ipynb`: Jupyter notebook with the complete code for processing the corpus and performing SVD.
- `word_representations_SVD.csv`: CSV file containing the word representations generated from the SVD.
- `word_representations_SVD.xlsx`: Excel file containing the word representations generated from the SVD.
-  I have converted **csv** file to **xlsx** because of the poor encoding in csv , the **Hindi** words were not readable, which they are in **xlsx**.

## Code Structure

1. **Reading the Corpus**
    The script reads the Hindi text data from `Corpus.txt`.
2. **Creating the Vocabulary**
    The script creates a vocabulary from the text data and maps each word to a unique index.
3. **Creating the Co-occurrence Matrix**
    The script creates a co-occurrence matrix based on the context window of size 2 (i.e., one word to the left and one word to the right).
4. **Performing SVD**
    * The script performs **Singular Value Decomposition** on the co-occurrence matrix to reduce its dimensionality.
    * It uses a **rank-100** approximation for SVD.
5. **Generating Word Representations**
    The script computes the word representations using the top 100 singular values and their corresponding singular vectors.

6. **Saving the Results**
    The word representations are saved to `word_representations_SVD.csv` and then converted to `word_representations_SVD.xlsx` to improve readability.




