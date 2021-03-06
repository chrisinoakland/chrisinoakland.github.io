---
title: "Scraping a Web Page using Python"
date: 2020-02-02T16:15:38-04:00
categories:
  - blog
tags:
  - python
  - web scraping
classes: wide
header:
    image: /assets/images/scrape.jpg
---

An exercise in scraping and reading web pages using Python.

### Introduction

How to scrape and read a web pages using BeautifulSoup, Selenium, and Python.


```python
import urllib.request
from bs4 import BeautifulSoup
import requests
import pprint
from selenium import webdriver

# ----------| 1) SCRAPE A WEB PAGE |----------

with urllib.request.urlopen('https://podshop.com') as response:
    podshop = response.read()

pprint.pprint(podshop)


# ----------| 2) READING A WEB PAGE WITH BEAUTIFUL SOUP |----------

page = requests.get('https://podshop.com/about/')
site = BeautifulSoup(page.content, 'html.parser')
print(site.title)
print(site.find_all('a'))
print(site.find_all('p'))

headerChildren = [c for c in site.head.children]

print(headerChildren)

navigationBar = site.find(id="nav")

for d in navigationBar.descendants:
    print(d)

for s in d.previous_siblings:
    print(s)

ta_divs = site.find_all("div", id="main")

print(len(ta_divs))

allData = []

for ta in ta_divs:
    dataDict = {}
    dataDict['title'] = ta.h2.get_text()
    dataDict['link'] = ta.a.get('href')
    dataDict['about'] = [p.get_text() for p in ta.find_all('p')]
    allData.append(dataDict)

print(allData)


# ----------| 3) WEB SCRAPING WITH SELENIUM |----------

chromeDriver = '/Users/chris/Documents/Education/MSDS/PyCharm/dsc540/week8/chromedriver'

options = webdriver.ChromeOptions()
options.add_argument('headless')

browser = webdriver.Chrome(executable_path=chromeDriver, options=options)

browser.get('https://www.britishcycling.org.uk/membership/article/20120925-Power-Calculator-0')

searchForm = browser.find_element_by_id('fthr')
searchForm.send_keys('198')

submitButton = browser.find_element_by_id('fthr_button')
submitButton.click()

results = browser.find_elements_by_id('heart_rate_table')
for result in results:
    print(result.text)

browser.quit()
```