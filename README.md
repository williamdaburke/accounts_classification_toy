# accounts_classification_toy
Trial of nlp classifiers on small toy dataset

If jupyter notebook is not visible or if live version is desired, open in colab: https://colab.research.google.com/github/williamdaburke/accounts_classification_toy/blob/master/accounts_classification_toy__tfidf.ipynb


Based on the small size of the file, number of labels, number of vocabulary, and average sentence size, I have created some
tfidfs vectors for the text data and classified using simple sklearn classifiers: randomforest, bayes, logistic regression, and
two types of linear svm models.  The best results were always with the linear svc.

I first ran some tests without resampling the minority classes and received decent accuracy to begin with, above 90 f1 score.
The random forest classifier however performs very poorly on a skewed dataset. 

To improve a bit on this I used random over sampling to balance the classes. All models performed slightly better, and random forest
also gave a good result, but linearsvc continued to have the best results.

The reason these simple classifiers are able to perform well is firstly that this is a rather well-separated dataset with
well defined classes, simple language and small sentences.  But more importantly, using a linear classifier on tfidf vectors generally
performs well because N-dimensional, sparse vectors tend to be linearly separable in N - 1 dimensions, the larger N is.  In this case,
the vocab/tfidf vectors for the training set are only about 450 or so words, depending on the training/test split, which is relatively
small for a set of documents, however still high dimensional. 

These models are all quite small, with few parameters and could be easily deployed in most contexts, for example in a flask app.
