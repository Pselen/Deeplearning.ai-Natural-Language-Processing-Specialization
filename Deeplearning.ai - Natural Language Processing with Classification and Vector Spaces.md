## Deeplearning.ai - Natural Language Processing with Classification and Vector Spaces



**Week 1: Sentiment Analysis with Logistic Regression **

###### Supervised Machine Learning & Sentiment Analysis:

In supervised machine learning

- We have; 
  - Input features, X
  - Set of labels, Y
- The goal is to minimize the error rates/cost as much as possible
- To do this we have;
  - Prediction function;
    - Takes in parameters, θ
    - Maps X to predicted labels Ŷ
    - The best mapping is achieved when the difference between Y and Ŷ is minimized
  - Cost function, F;
    - Compares Y and Ŷ
    - Checks how close they are
- We update the parameters and repeat the whole process until the cost is minimized.

![](C:\Users\parla\Desktop\DL\supervised ml.PNG)

- To build a logistic regression classifier:
  1. *Extract features*: Process raw data in the training set and extract useful features
  2. *Train*: Train your classifier so that the cost is minimized
  3. *Predict*

###### Vocabulary & Feature Extraction

In order to use the text data in our classifier we need to represent the text as a vector. First, we need to build a vocabulary, V. A *vocabulary* allows to encode any text as an array of numbers. Using the vocabulary we extract the features.

**Text**: I am happy because I am learning NLP. I hated the movie.

**Vocabulary**: List of unique words from whole text

[I, am, happy, because, learning, NLP, hated, the, movie]

**Sparse representation**: Assign a value of 1 if a word appears in the V, and assign 0 if it doesn't appear. Feature vector of text "I am happy because I am learning NLP" using V 

[1, 1, 1, 1, 1, 1, 1, 0, 0, 0]

![](C:\Users\parla\Desktop\DL\sparse representation.PNG)

- Problems with the sparse representation:

  - Each representation has a number of features equal to the size of the entire vocabulary, |V|.

  - A LR model has to learn (n+1) parameters; 
    $$
    [θ_0, θ_1, θ_2, ..., θ_n]\\
    n = |V|
    $$

  - If V gets larger it requires larger training time and larger prediction time.