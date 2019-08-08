Problem Statement
The goal for this project, and jupyter notebook, is to determine whether the words in the title or the body texts can help determine which particular website the post came from.  Here I webscrape over two different subreddits within the website Reddit.  The two subreddits chosen for the project are World News and Geopolitics.  I wanted two topics with what I felt would be similar posts and therefore, similar words but still be able to make a good enough model to discern between them.  If successful, the model could be modified to be applied to many other texts!

Executive Summary
Since the first part of the project included pulling data from two subreddits and to dissect that data, I first used the praw wrapper to pull 1000 posts from each site.  After examing the data, some simple feature engineering and test breakdown using a lemmatizer was performed.  The title and body texts were separated and set up to have the models run on them individually.  This was done because numerous amount of posts didn't have body text.

The modeling process began setting up a pipeline with a CountVectorizer estimator. A gridsearch was also set up to find the optimal parameters for score for the models.  The models included a logistic regression, k-nearest neighbors, and multinomial naive Bayes models. All were fitted to the text data and scored.  The best model in accuracy came out to be the title for naive Bayes with the logistic regression being close behind and the best custom made model.

After the modeling some sentiment analysis was performed using VADER.  This allowed me to run another breakdown of the text to see the coefficients for each word, and thus be able to see the words liklihood of being in a subreddit or not.  In the end, the title models performed the best at determining where a post came from.  More tweaks will be needed to get the model to perform better on these subreddits and for others in the future.

Outline
- Problem Statement
- Executive Summary
- Outline 
- Imports
- Data Scraping
- Data Cleaning
- Modeling
- Logistic Regression
- Multinomial Naive Bayes
- KNN Classification
- Sentiment Analysis
- Conclusion|

Conclusion
After checking out the scores from the models, it was clear to see that the title texts were much better at determining which post the subreddit came from.  There was much overfitting seen between the training and testing data in the models.  This could be alleviated by using a TFIDF Vectorizer instead.  The best custom made model THat I can interpret is the logistic regression.  This provided a title text accuracy score of 0.79 on the test data.  Not bad, but very much need for impovement.  The best parameters in the models asked for no stopwords.  This allowed for common words to have higher coefficients for the geopolitics subreddit.  Words like "what", "why", and "how" took the top.  This makes sense since many of the posts were discussion based.  On the other side, the top words in world news were "UK", "French", and "Middle East".  Also makes sense since much of the global news outside of the US centers around those areas.  Better models could have also been fitted and scored like a random forest or SVC and could have provided better scores.