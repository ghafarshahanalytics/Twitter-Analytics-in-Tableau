#Created by: Ghafar Shah
#About: I created this project to perform analysis on Twitter data in Tableau.
#This was also to practice writing Python, APIs, and pandas.
#Created Date: 08.16.2020

# noinspection PyUnresolvedReferences
import tweepy as tw

# noinspection PyUnresolvedReferences
import pandas as pd

# noinspection PyUnresolvedReferences
import csv

# Twitter credentials for the app
consumer_key = 'Enter your consumer key'
consumer_secret = 'Enter your consumer secret'
access_key = 'Enter your access key'
access_secret = 'Enter your access secret'

# pass twitter credentials to tweepy
auth = tw.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_key, access_secret)

# call the api
api = tw.API(auth)

# assign values to variables to pass into tweepy search query below.
search_words = '#makeovermonday'
date_since = '2020-08-09'
last_date = '2020-08-14'

# search query is stored in the variable called tweets.
tweets = tw.Cursor(api.search, q=search_words, lang="en", since=date_since, until=last_date, tweet_mode="extended").items(1500)

# create an array for loop with all the fields that I need for analysis.
# store the array into a variable called users_tweets
users_tweets = [[tweet.author.name.encode('utf8'), tweet.author.screen_name.encode('utf8'), tweet.created_at,
    tweet.full_text.encode('ascii', 'ignore'), tweet.favorite_count, tweet.retweet_count] for tweet in tweets]

# Create a data frame using pandas to construct a table for fields.
tweet_text = pd.DataFrame(data=users_tweets, columns=['Author Name', 'Twitter Handle', 'Created Date', 'Tweet Text',
                                                      '# of likes', 'Retweet Count'])
# export results into a csv file.
tweet_text.to_csv (r'C:\Users\gshah200\Documents\export_makeovermondayTweetsNEW.csv', index = False, header=True)

#print data frame results to double check output.
print(tweet_text)

# I used the commented out code below to check if the results would show.

#for tweet in tw.Cursor(api.search, q=('#makeovermonday'), since='2020-08-09', until='2020-08-13').items(5):

  #  print("Name:", tweet.author.name.encode('utf8'))
  #  print("Screen-name:", tweet.author.screen_name.encode('utf8'))
  #  print("Tweet created:", tweet.created_at)
  #  print("Tweet:", tweet.text.encode('utf8'))
  #  print("Retweeted:", tweet.retweeted)
  #  print("Favourited:", tweet.favorite_count)
  #  print("Location:", tweet.user.location.encode('utf8'))
  #  print("Time-zone:", tweet.user.time_zone)
  #  print("Geo:", tweet.geo)
  #  print("//////////////////")