---
title: "Pulling Data from Twitter API"
date: 2020-02-06T15:17:42-04:00
categories:
  - blog
tags:
  - python
  - weather app
classes: wide
---

How to pull data from Twitter using API's.

### Introduction



```python

# File: Exercise9_2.py
# Name: Christopher M. Anderson
# Date: 02/06/2020
# Course: DSC540 Data Preparation
# Week: 9
# Assignment Exercise: 9.2: Pulling Data from APIs


import oauth2
import tweepy
import dataset
from tweepy.streaming import StreamListener
from tweepy import OAuthHandler, Stream
import pprint


# In this exercise, you will create a twitter account (if you don’t already have one, or don’t wish to use
# your personal account) and practice pulling data from Twitter’s publicly available API. You can
# delete the twitter account as soon as you have completed the exercise. Include your
# code and output for each step.

# 1) Create a Twitter API Key and Access Token (Data Wrangling with Python, pg. 365-366)

# 2) Do a single data pull from Twitter’s REST API (Data Wrangling with Python, pg. 366 – 368).

# 3) Execute multiple queries at a time from Twitter’s REST API (Data Wrangling with Python, pg. 368 – 371).

# 4) Do a data pull from Twitter’s Streaming API (Data Wrangling with Python, pg. 372 – 374).


# ----------| 1) TWITTER API KEYS & ACCESS TOKENS |----------

API_KEY = 'your key here'
API_SECRET = 'your secret token here'
TOKEN_KEY = 'your token key here'
TOKEN_SECRET = 'your token secret here'


# ----------| 2) DATA PULL FROM TWITTER REST API |----------


def oauth_req(url, key, secret, http_method="GET", post_body=b"",
              http_headers=None):
    consumer = oauth2.Consumer(key=API_KEY, secret=API_SECRET)
    token = oauth2.Token(key=key, secret=secret)
    client = oauth2.Client(consumer, token)
    resp, content = client.request(url, method=http_method,
                                   body=post_body, headers=http_headers)
    return content


url = 'https://api.twitter.com/1.1/search/tweets.json?q=%23childlabor'
data = oauth_req(url, TOKEN_KEY, TOKEN_SECRET)

with open("/Users/chris/Documents/Education/MSDS/PyCharm/dsc540/week9/data/hashchildlabor.json", "wb") as data_file:
    data_file.write(data)


# ----------| 3) DATA PULL FROM TWITTER REST API |----------

def store_tweet(item):
    db = dataset.connect('sqlite:///data_wrangling.db')
    table = db.create_table('tweets', primary_id=False)
    item_json = item._json.copy()
    for k, v in item_json.items():
        if isinstance(v, dict):
            item_json[k] = str(v)
    table.insert(item_json)


auth = tweepy.OAuthHandler(API_KEY, API_SECRET)
auth.set_access_token(TOKEN_KEY, TOKEN_SECRET)

api = tweepy.API(auth)

query = '#childlabor'
cursor = tweepy.Cursor(api.search, q=query, lang="en")

for page in cursor.pages():
    for item in page:
        store_tweet(item)


# ----------| 4) TWITTER PULL FROM TWITTER STREAMING API |----------

class Listener(StreamListener):

    def on_data(self, data):
        pprint.pprint(data)
        return True


auth = OAuthHandler(API_KEY, API_SECRET)
auth.set_access_token(TOKEN_KEY, TOKEN_SECRET)

stream = Stream(auth, Listener())
stream.filter(track=['child labor'])

```