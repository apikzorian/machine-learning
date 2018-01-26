# Machine Learning Engineer Nanodegree

## Kaggle Airbnb New User Predictor
Apik Zorian
January 25, 2018

## Proposal

### Domain Background

Airbnb is an online peer-to-peer property rental service that allows users to book short-term lodging. This includes rooms, apartments, entire homes, vacation rentals, etc. Airbnb brokers reservations between users and landlords for lodging all over the world. As of January 2018, the company had over 3 million listings in 65,000 cities over 191 countries. 

One way to immediately pique a new user's intrest is to cater to advertise bookings in a city or country the user would first like to visit. By accurately predicting where a new user will book his or her first trip, Airbnb can curate personalized content to send to the user. For Airbnb, this helps decrease the average time to first booking for a new user and personalize content with their community. It also improves the new user's first booking experience by curating content to their travel preferences. 


### Problem Statement
The challenge then becomes: How can Airbnb predict the country in which a new user will make his or her first booking?

In this project, we will predict a new user's first booking by deploying machine learning algorithms to analyze data about the user that will help predict this first booking. Airbnb has posted this very problem as a [Kaggle Recruitment Challenge](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings#description) and has provided New User Booking Data to help participants develop models to predict the new user's first booking. This data includes information about the users, including demographis, web session records, and some summary statistics. 

Our goal is to analyze the data, remove irrelevant features or combine features that can be used together, build and train a model, and predict a new user's first booking. 

### Datasets and Inputs

The dataset provided by Airbnb includes 5 .csv files:

* [train_users.csv](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/download/train_users_2.csv.zip) - the training set of users
* [test_users.csv](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/download/test_users.csv.zip) - the test set of users
* [sessions.csv](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/download/sessions.csv.zip) - web sessions log for users
* [countries.csv](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/download/countries.csv.zip) - summary statistics of destination countries in this dataset and their locations
* [age_gender_bkts.csv](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/download/age_gender_bkts.csv.zip) - summary statistics of users' age group, gender, country of destination

You can access the dataset [here](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/data)

In this section, the dataset(s) and/or input(s) being considered for the project should be thoroughly described, such as how they relate to the problem and why they should be used. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included with relevant references and citations as necessary It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem.

### Solution Statement
_(approx. 1 paragraph)_

In this section, clearly describe a solution to the problem. The solution should be applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, describe the solution thoroughly such that it is clear that the solution is quantifiable (the solution can be expressed in mathematical or logical terms) , measurable (the solution can be measured by some metric and clearly observed), and replicable (the solution can be reproduced and occurs more than once).

### Benchmark Model
There are 12 possible outcomes of the destination country: 'US', 'FR', 'CA', 'GB', 'ES', 'IT', 'PT', 'NL','DE', 'AU', 'NDF' (no destination found), and 'other'.  

To determine our benchmark, we will attempt to predict the top 5 most common results. We will train our model on the provided training set, test the model on our testing set, and try to predict the 5 most common outcomes. 

### Evaluation Metrics
_(approx. 1-2 paragraphs)_

Kaggle assesses submissions based on Normalized discounted cumulative gain (NDCG). NDCG is calculated as:

![alt text](https://image.ibb.co/dc1btb/Capture.jpg)

where reli is the relevance of the result at position i. We will be making a maximum of 5 predictions per booking (k = 5). 

For each new user, we make a maximum of 5 predictions on the country of the first booking. The ground truth country is marked with relevance = 1, while the rest have relevance = 0.

If, for example, the destination for a particular user is France (FR), then the predictions become:

![alt text](https://image.ibb.co/bBNhYb/NDCG1.jpg)

As NDCG is the [evaluation metric that Kaggle uses](https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings#evaluation), to assess participants for their competition, this will be our metric as well.

### Project Design

Our project will be composed of three steps:

  1. Data Exploration: Along with visualizing our dataset, this step will include using feature manipulation techniques, such as:    
    * Detecting and removing irrelavant features
    * Utilizing clustering to create new features    
    * Detecting outliers
    * Evaluating outliers significance
    * Removing null values
    
  2. Training and evaluating model: In this step, we will consider various supervised Machine Learning models and use cross validation    to determine which will be best suited for our task. We will also utilize Gridsearch to optimize our parameters
  
  3. Testing model: We will utilize our testing set to test our trained model, submit to Kaggle.
