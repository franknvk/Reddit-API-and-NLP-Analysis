Frank Novak
Project 3
DSI 1010
December 6, 2022 

Neuralink has interest in introducing new forms of research data for their latest brain-interface implants. The data science team has been tasked to compile “alternative” sources of brain stimuli to present to the medical research team for the next leg of implant experiments. After an exhaustive search, subreddits /r/psychonaughts and /r/askphilosophy were identified to have innovative stimuli of interest. Using NLP and a classification model, find what distinguishes the subreddits from one another and evaluate these features for new experiments in brain stimulus research.

The data collection process will be done through Pushshift's API to scrape both askphilosophy and psychonauts subreddits. The loop starts from 2 days before todays date. The scrape will go until 15000 posts are collected with 2 second rests between each requests. The collected data will be added to a dataframe and saved. This occurs for each subreddit.

Features of interest are the text based information: the post text (selfext) and the title of the post. To start, duplicate posts based on the title and the actual post text are removed. This will get rid of any extra information related to spammed posts, moderators posts, or any overall junk. Afterwards, replace any 'remove' or 'deleted' items found in the dataframe with NaN and drop. Any posts from the moderators will be removed to filter maintenance, redundancies, or regulatory information not related to the subreddit. The author feature can be used to locate and remove. Afterwards, the author feature is dropped as it is not needed for our text analysis, calculate the word count of each post, and then combine all text features into one.

Now that the data has been cleaned from nulls and missing values, the text can be structured and organized for vectorizing. This will involve standardizing text, removing special characters, expanding contractions, tokenizing words, tagging the parts of speech, and lemmatize. Parts of speech are important for lemmatizing adequately and condensing similar words. This is a must to give accurate sums of words in each subreddit. 

For modeling, there were 5 seperate models, with specific parameters Gridsearched, to offer a variety of algorithms to the data. TfidfVectorizer was used within the gridsearch in order to remove common words found between both subreddits by optimizing the max_features and max_df parameters. Standard Scaler was also used when needed. First, the baseline accuracy is calculated to compare the models. Accuracy was the metric of choice since false positives or false negatives did not impact the over purpose of the model. 

Out of all the models, using GridSearch, Logistic regression returned the best accuracy with no signs of overfitting the training data. The different areas of interest within each subreddit are very different and specific which lead to the 95% accuracy score. To further improve the models, a more robust parameter searching function may help further improve the modeling like BayesSearch or RandomizedSearch. Increasing possible features may also help improve the accuracy. 
