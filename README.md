Read me
Problem Statement: Using Classification model to predict whether exercise or diet subreddit a post belongs to.
Overview
I have 3 notebooks for this project.

Web Scrapping
EDA and Pre Processing
Modelling
We can even find 3 csv files.

diet_dataframe.csv
exercise_dataframe.csv
final_df.csv
We can even find 2 png file where in u can see word cloud images of both diet and exercise sub reddits.

Reddit is a collection of interest-based communities known as subreddits, whose content vary from news to sports teams, to hobbies, to basically anything you can imagine.
By using Natural Language Processing(NLP) , Logistic Regression and Naive Bayes to classify Reddit posts from Diet and Exercise subreddit channels. We will subreddit the post came from by using the selftext.
To handle this, I used the data science process:
Define the problem
Gather the data
Clean and Explore the data
Model the data
Evaluate the model
Answer the problem
Define the problem
Predict from which sub reddit a post belongs to, diet or exercise
Gather the data
Data was gathered from reddit API, using the python request library. API returns a JSON file with the page's content.
If the connection is successful, then a status code of 200 is printed. If you want to retrieve data from a different subreddit, just change the URL.

Since reddit post 26 posts per request, I iterated a couple of times to gather in between 950 to 1000 posts on each sub reddit. I also used the time.sleep() to create a pause between requests. Results were saved in a csv file. In this project, I need title and self text but I also gathered other data such as author, domain, subreddit .

Clean and Explore Data:
To clean the data, I performed the following work.

Removed all the duplicate vlaues from the data
Converts character to lower case.
I replaces all non-numerical and non-alphabetical data to spaces
I replaced the multiple blank spaces with only one space. I did the above two cleaning using Regular expressions
I removed English Stop Words
After the cleaning, I used wordNetLemmatizer() and PorterStemmer() which are the two forms of shortening words so we can combine similar forms of the same word. I did Lemmatizing and Stemming of Selftext and title but chose lemmatizing of self text as it is more correct and precise way of handling things from a grammatical/morphological point of view.

Model and Evaluate the data
I have split the data using default values for train_df and test_df using train_test_split. After getting the train_df and test_df, I did

Countvectorizer with logistic regression
Countvectorizer with Naive Bayes
TF IDF with logistic regression
TF IDF with Naive Bayes
Found the optimal values using grid search and then fit and transformed on the trained data using best optimal parameters. Then I transformed the test data and scored the value.

Next, I did confusion matrix which tells the performance of my algorithm. by which i found my sensitivity and specificity.

Solution of the problem
I found the most top words were from the diet subreddit by which I can conclude that people think more about diet. and eating right food at tight time reminded me at this stage of time. I can even conclude that my model is able to classify my two subreddits almost to 90% accuracy.

