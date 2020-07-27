## Text Vectorization

###### Feature Extraction

In order to use the text data in logistic regression we need to represent the text as a vector. We build a *vocabulary* $V$ to encode any text as an array of numbers. Using the vocabulary we can extract features from tweets by assigning a value of $1$ if a word appears in the tweet, and assigning $0$ otherwise. This is called **sparse representation**.

- Example:

  - **Vocabulary:** [I, am, happy, because, learning, NLP, hated, the, movie]
  - **Tweet:** I am happy because I am learning NLP
  - **Vector:** $[1, 1, 1, 1, 1, 1, 1, 0, 0, 0]$

- Problems:

  - Each tweet has a vector with a dimension equal to the size of the entire vocabulary ($|V|$).

  - An LR model has to learn a parameter for each word and a bias, that sums up to $n+1$ parameters.
    $$
    [θ_0, θ_1, θ_2, ..., θ_n]\\
    n = |V|
    $$

  - Thus, sparse representation is not scalable in terms of $|V|$, for both training and prediction.

We can use **positive** and **negative** **frequencies** of words to create a 3-dimensional vector for each tweet. To do so, we count how many times a word appears in a positive and a negative tweet and create a frequency table. In turn, we represent each tweet with a vector as follows:
$$
X = [1, \sum_{w} freq(w, 1), \sum_{w} freq(w, 0)]
$$

where $w$ is a unique word in the tweet in consideration  and $1$ is the bias term.

- Example:

  - **Frequency Table:**

    <img src="D:/Classes/NLP/Course I - NLP with Classification and Vector Spaces/Week I/fig/frequency_table.png" style="zoom: 33%;" />

  - **Tweet:** I am sad, I am not learning NLP.

  - Vector: $[1, \sum_{w} freq(w, 1)= 3+ 3+ 1 + 1= 8, \sum_{w} freq(w, 0)= 3+ 3+ 2+1+1+1= 11]$

**Remark I:** We use the *set of unique words* in a tweet while summing the frequencies. For instance, we consider "I" only once, though it is repeated in the tweet, and added $3$ to the summation, not $6$.

**Remark II:** Frequency label construction needs labels (*supervised*), unlike sparse representation that did not consider any label information (*unsupervised*).

###### Text Preprocessing

To facilitate text vectorization we can:

- Remove stopwords (and, the, that, is etc.) ,
- Remove punctuation,
- Remove URLs,
- Apply stemming (using the a word's stem only by dropping the suffixes),
- Apply case folding.

to reduce vocabulary dimensionality significantly and match similar words such as "I" and "i" or "going" and "go".

By applying these preprocessing steps to each tweet and using word frequency-based vectorization, we obtain the feature matrix $X \in R^{m \times 3}$, where $m$ is the number of tweets in the dataset.