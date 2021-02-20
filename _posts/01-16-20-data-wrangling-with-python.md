---
title: "Data Wrangling with Python"
date: 2020-01-16T15:15:31-04:00
categories:
  - blog
tags:
  - python
  - data wrangling
classes: wide
header:
    image: /assets/images/data_wrangle.jpg
---

Fixing labels and headers using Python.

### Introduction

Using Python to read in data files and clean them up.

```python
# ----------| FIXING LABELS/HEADERS |----------

# Instructions:

# Fixing Labels/Headers – (page 155 – 156 Data Wrangling with Python).
# Create a new dictionary for each row to create a new array.

# Purpose:

# This portion of the code will read the UNICEF files and clean them up

from csv import DictReader

data = DictReader(open('mn.csv', 'rt', encoding='utf-8'))
header = DictReader(open('mn_headers.csv', 'rt', encoding='utf-8'))

dataRows = [d for d in data]
headerRows = [h for h in header]

print(dataRows[:5])
print(headerRows[:5])

newRows = []

for data_dict in dataRows:
    new_row = {}
    for dkey, dval in data_dict.items():
        for header_dict in headerRows:
            if dkey in header_dict.values():
                new_row[header_dict.get('Label')] = dval
    newRows.append(new_row)

from csv import reader

data = reader(open('mn.csv', 'rt', encoding='utf-8'))
header = reader(open('mn_headers_updated.csv', 'rt', encoding='utf-8'))

dataRows = [d for d in data]
headerRows = [h for h in header if h[0] in dataRows[0]]

print(len(headerRows))

all_short_headers = [h[0] for h in headerRows]

skipIndex = []

for header in dataRows[0]:
    if header not in all_short_headers:
        index = dataRows[0].index(header)
        skipIndex.append(index)

newData = []

for row in dataRows[1:]:
    new_row = []
    for i, d in enumerate(row):
        if i not in skipIndex:
            new_row.append(d)
    newData.append(new_row)

zippedData = []

for drow in newData:
    zippedData.append(list(zip(headerRows, drow)))

dataHeaders = []

for i, header in enumerate(dataRows[0]):
    if i not in skipIndex:
        dataHeaders.append(header)

headerMatch = zip(dataHeaders, all_short_headers)

print(headerMatch)

# ----------| DATA FORMATS READABLE |----------

# Instructions:

# Using the same dataset as the above example (mn.csv and mn-headers.csv), use the format
# method to make output human readable.

for x in enumerate(zippedData[0][:20]):
    print(x)


# ----------| DATE FORMATTING |----------

# Instructions:

# Format the dates to determine when the interview started and ended.

from datetime import datetime

startString = '{}/{}/{} {}:{}'.format(zippedData[0][8][1],
                                      zippedData[0][7][1],
                                      zippedData[0][9][1],
                                      zippedData[0][13][1],
                                      zippedData[0][14][1])

print(startString)

startTime = datetime.strptime(startString, '%m/%d/%Y %H:%M')

print(startTime)

endTime = datetime(int(zippedData[0][9][1]),
                   int(zippedData[0][8][1]),
                   int(zippedData[0][7][1]),
                   int(zippedData[0][15][1]),
                   int(zippedData[0][16][1]))

print(endTime)

duration = endTime - startTime

print(duration)
```