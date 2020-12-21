---
title: "Logging and Automation"
date: 2020-02-16T15:17:42-04:00
categories:
  - blog
tags:
  - python
  - logging and automation
classes: wide
---

### Introduction

How to use Python to perform logging and automation

```python
# File: Exercise10_2.py
# Name: Christopher M. Anderson
# Date: 02/16/2020
# Course: DSC540 Data Preparation
# Week: 10
# Assignment Exercise: 10.2: Logging and Automation


import oauth2
import logging
from datetime import datetime
from twilio.rest import Client


# Complete the following using Python – make sure to show your work and show the values returned.
# You can submit via your notebook or code editor, no need to export your work.

# 1) Add Python logging to previous code that you have written. In your logging, include a note to
# yourself with the area of the code writing the message so you know where the error occurred.
# Include your code and output in your submitted assignment. An example of this can be found
# on page 406-408 of your text, Data Wrangling with Python.

# 2) Add an automated message to previous code that you have written. You can choose to do an
# email, text or call. Make sure to include the failure/success in your message. Include your
# code and output in your submitted assignment. An example of this can be found
# on page 408-412 of your text Data Wrangling with Python.

# ----------| PREVIOUS CODE |----------

# Twitter Account Information:

API_KEY = 'your key here'
API_SECRET = 'your secret token here'
TOKEN_KEY = 'your token key here'
TOKEN_SECRET = 'your token secret here'

# Data Pull from Twitter Rest API:


def oauthReq(url, key, secret, http_method="GET", post_body=b"", http_headers=None):
    consumer = oauth2.Consumer(key=API_KEY, secret=API_SECRET)
    token = oauth2.Token(key=key, secret=secret)
    client = oauth2.Client(consumer, token)
    resp, content = client.request(url, method=http_method,
                                   body=post_body, headers=http_headers)
    return content


url = 'https://api.twitter.com/1.1/search/tweets.json?q=%23childlabor'
data = oauthReq(url, TOKEN_KEY, TOKEN_SECRET)

with open("/Users/chris/Documents/Education/MSDS/PyCharm/dsc540/week10/data/data.json", "wb") as data_file:
    data_file.write(data)

# ----------| 1) LOGGING PREVIOUSLY WRITTEN CODE |----------

# Initialize the log file. This code creates a log file named 'DSC540_week10_'
# followed by the date & time it was ran. The logging level is set to 'DEBUG'.


def startLogger():
    logging.basicConfig(filename='DSC540_week10_%s.log' %
                        datetime.strftime(datetime.now(), '%m%d%Y_%H%M%S'),
                        level=logging.DEBUG,
                        format='%(asctime)s %(message)s',
                        datefmt='%m-%d %H:%M:%S')


# ----------| 2) AUTOMATED MESSAGING WITH TWILIO |----------

# Twilio Account Information:

accountSID = " "  #insert your data here 
authToken = " "   #insert your data here

client = Client(accountSID, authToken)

# Let's log!

startLogger()
logging.debug("SCRIPT: Starting")

try:
    data = oauthReq(url, TOKEN_KEY, TOKEN_SECRET)
    # Success message
    message = client.messages.create(
        to="+ ",   # Your number here
        from_="+ ",  # A Twilio temporary number is used to send messages
        body="Yay! DSC540 Week 10 Exercise - sending an automated message was a success!")

except Exception:
    logging.exception('SCRIPT: We had a problem!')
    logging.error('SCRIPT: Issue with division in the main() function')
    # Failure message
    message = client.messages.create(
        to="+ ",   # Your number here
        from_="+ ",  # A Twilio temporary number is used to send messages
        body="Uh oh. DSC540 Week 10 Exercise - sending an automated message has failed!")
    logging.debug('SCRIPT: Finish!')

# Print copy of the text message that was sent:

print("Text Message: {}\n".format(message.body))

# Verify/review the output:

print(type(data))
print(data)

```