# Anomaly-Detection-And-Movie-Recommendations-System

## **Overview**


This is a Anamoly Detection and Recommender system using MATLAB. 

The anamoly detection project uses the Multivariate Gaussian Distribution to fit the training data. We  collected data, m=307, when the detection algorithm detected anomalous behavior in the computer servers, thus the unlabeled dataset { x^1, ..., x^m}. The features measure the throughput (mb/s) and latency (ms) of response of each server and we suspect that the vast majority of these examples are "normal" or non-anomalous examples of the servers operating normally but there is a possibility that some of the examples from the servers is acting anomalously from the collected data. 




## **The Dataset**

The graph below is the first dataset:



![Image 12-30-23 at 4 40 PM](https://github.com/ntalib/Anomaly-Detection-Movie-Recommendations-System/assets/90749418/8c163b82-44a5-470c-a8a0-70f26129f2b2)




## **Gaussian Distribution**


To perform this anomaly detection, we need to fit the model to the data's distribution. 

Given that our training set {x^1,...,x^m}, where x^i ∈ R^n, we want to estimate the Gaussian distribution for each of the features x^i. For each i=1...n, we need to find parameters μ<sub>i</sub> and σ<sub>i</sub><sup>2</sup>  that fit the data in the i<sup>th<sup> dimension {*x*<sub>i</sub> ^1 ,....,*x*<sub>i</sub>^m} 

The Gaussian distribution is given by:



![Image 12-30-23 at 6 12 PM](https://github.com/ntalib/Anomaly-Detection-Movie-Recommendations-System/assets/90749418/49af44e8-e824-4c96-bb31-404f081dae53)


Where miu is the mean and the sigma squared controlss the variance.



## Project Schema 1: Estimating the parameters for a Gaussian distribution


To estimate the parameters (miu, sigma squared) of the ith feature by using the following equations. 


To estimate the mean, miu, we will use:

![Image 12-30-23 at 6 17 PM](https://github.com/ntalib/Anomaly-Detection-Movie-Recommendations-System/assets/90749418/c4cb466c-22d0-4f2f-8575-3a8b19f6ac87)


and for the variance, sigma, we will use:

![Image 12-30-23 at 6 18 PM](https://github.com/ntalib/Anomaly-Detection-Movie-Recommendations-System/assets/90749418/ef659cc9-19c9-4bea-aa0e-25ac9aeeb966)


The file *estimateGaussian.m* is a function that takes data matrix X as input and output an n-dimension vector *mu* that hols the mean of all the *n* features and another n-dimension vector mu that holds the mean of all the n features and another n-dimension vector sigma2 that holds the variances of all the features. 

We will also be visulaizing the contours of the fitted Gaussian distribution and we should have a plot similar to below: 

![Image 12-30-23 at 6 40 PM](https://github.com/ntalib/Anomaly-Detection-Movie-Recommendations-System/assets/90749418/7d8b5894-25d1-4b48-ac9b-e03376ea01a0)




## Project Schema 2: Selecting the threshold, ε


After estimating or Gaussian distribution parameters, we can now investigate which training examples have a very high probability given this distribution and which training example has a low probability. 


The low probability training examples are more likely to be the anomalies











#### Fact Table 
**songplays** : records song playes in the log data, records with  `NextSong`
```
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
```
#### Dimension Tables
**users**  : users in the app
```
user_id, first_name, last_name, gender, level
```
**songs**  : songs in music database
```
song_id, title, artist_id, year, duration
```
**artists**  : artists in music database
```
artist_id, name, location, latitude, longitude
```
**time**  : timestamps of records in  **songplays**  broken down into specific units
```
start_time, hour, day, week, month, year, weekday
```

## Project Documents

```sql_queries.py``` : contains sql queries for dropping and  creating fact and dimension tables. Also, contains insertion query template.

```create_tables.py``` : contains code for setting up database. Running this file creates **sparkifydb** and also creates the fact and dimension tables.

```etl.ipynb``` : a jupyter notebook to analyse dataset before loading. 

```etl.py``` : read and process **song_data** and **log_data**

```test.ipynb``` : a notebook to connect to postgres db and validate the data loaded.

## Environments used 
Python 3.6 or above

PostgresSQL 9.5 or above

psycopg2 - PostgreSQL database adapter for Python


## Run

Run the drive program ```main.py``` as below.
```
python main.py
``` 

The ```create_tables.py``` and ```etl.py``` file can also be run independently as below:
```
python create_tables.py 
python etl.py 
```



