# Web APIs and Natural Language Processing (NLP)
### Problem Statement
1. Use Pushshift API to scrape data from two subreddits.
2. Build a model that classify subreddit post and predict if they are from one of the two subreddit. 
### Executive Summary
 *r/News* and *r/TheOnion* are the two subreddit I chose. 
 - *r/News* contains news articles about current events in the US and the rest of the world. 
 - *r/TheOnion* is an American **satirical** digital media company and newspaper organization that publishes articles on international, national, and local news.
 
I used PushShift API to pull 2500 most commented post in two years interval from each subreddit. The **title** of each post are used to make the model. 

Then, the data are cleaned. The cleaning process includes: Remove stop words; Change to lowercase; Remove punctuation; Remove bad symbol.

The cleaned data are then vectorized and fit into three classification model: Bernoulli Naive Bayes model, Random Forest model, and AdaBoost model. Using GridSearch, I was able to get the best score from each model. 

After evaluation, the best model is Bernoulli Naive Bayes Model, with a train score of 84.5%, test score of 84.4% and f1 score of 0.845.

### Table of Contents
- Preprocessing
	- 1_Data_Retrieval_Cleaning.ipynb
- EDA
	- 2_EDA.ipynb
- Models
	- 3a_Model_Naive_Bayes.ipynb
	- 3b_Model_Random_Forest.ipynb
	- 3c_Model_AdaBoost.ipynb
- Powerpoint
	- RedditNLP_Powerpoint.pdf
- Datas
	- reddit_df.csv

### Data Cleaning
- Remove stopwords, the stopwords are imported from nltk corpus packages. 
- Change to lowercase 
- Remove punctiation (Ex. .,:?!,)
- Remove bad symbol (Ex. /@#$%^&*_~) 

### EDA
 Most used word in *r/News*:
- Police, Says, Man, New, Arrested, Covid19, officer, shot
- New York, George Floyd, Police Officer, Capitol Riot, Hong Kong, Jeffrey Epstein 

 Most used word in *r/TheOnion*:
- Trump, New, Man, Onion, Says, Nation, Biden, Coronavirus
- White House, Study Finds, Says Nation, Prevent Says, Donald Trump

Word used in *r/TheOnion* tend to be about the White House and the President, while the word from *r/News* are the events that happened around the world. 

### Modeling
The base line accuracy is 50% 
**Bernoulli Naive Bayes** : best model of the three, It also takes shortest time to compute. 
- Train score - 0.845
- Test score - 0.844
- f1 score - 0.845

**Random Forest**: performed worst in the three model. 
- Train score - 0.804
- Test score - 0.780
- f1 score - 0.771

**AdaBoost**: performed slightly better than Random Forest. It appeared to be underfit, but it's common in AdaBoost model. 
- Train score - 0.716
- Test score - 0.796
- f1 score - 0.790

### Important Features
The features with highest coefficient of the three models all have similar theme, which is police activties. 
If the post is about police activities, it has a higher chance to be a r/News post. 



![Feature](https://i.postimg.cc/9Xp082vw/feature-important.png)

### Conclusion
-   Naive Bayes model provide best accuracy score among other, it also has the shortest compute time    
-   More emphasis on police activity in r/news
### Sources
- r/News https://www.reddit.com/r/news/
- r/TheOnion https://www.reddit.com/r/TheOnion/
