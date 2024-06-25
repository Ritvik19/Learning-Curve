# Zero-Shot Learning

Zero-shot learning is a relatively new research area, so there are no algorithms that proved to have a significant practical utility yet. In ZSL we want to train a model to assign labels to objects. The most frequent application is to learn to assign labels to images.

However, contrary to standard classification, we want the model to be able to predict labels that we didn’t have in the training data. How is that possible?

The trick is to use embeddings not just to represent the input x but also to represent the output y.

Now, in our classification problem, we can replace the label yi for each example i in our training set with its word embedding and train a multi-label model that predicts word embeddings. To get the label for a new example x, we apply our model f to x, get the embedding ˆy and then search among all English words those whose embeddings are the most similar to ˆy using cosine similarity.