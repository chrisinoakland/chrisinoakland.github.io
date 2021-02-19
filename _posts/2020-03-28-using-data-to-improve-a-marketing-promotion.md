---
title: "Using Data to Improve a Marketing Promotion"
date: 2020-03-28T15:17:12-04:00
categories:
  - blog
tags:
  - R
  - marketing
  - promotion
classes: wide
    
header:
    image: /assets/images/baseball.jpg
---

Using Data to Improve a Marketing Promotion.

### Introduction

This is an exploration of improving the attendance of a Major League Baseball game by using data science.

### Import Data

Let's import the data, shall we?

```{r load, echo=TRUE, collapse=TRUE, results=FALSE}
# Load the readr package:
library(readr)

# Read the baseball data in from the csv file:
baseball <- read.csv("dodgers.csv", stringsAsFactors = FALSE)
```

### Summarize

Now let's take a quick look using the `summary` and `str` commands to make sure our import worked as expected and we're seeing the data we expect:

```{r summary, echo=TRUE, collapse=TRUE}
# Show a summary to get an understanding of the results:

summary(baseball)
str(baseball)
```

It looks like our data has twelve different variables, with the last four `cap`, `shirt`, `fireworks`, and `bobblehead` as promotions at those home games.

### Variables

Now let's create a few variables from this data set:

```{r variableNames, echo=TRUE, collapse=TRUE}
# First let's get a look at the names of our different columns of data that will become the variables:

for (i in 1:length(baseball)) {
column <- (names(baseball[i]))
print(column)
}
```

### Freebies!

Everybody loves free stuff. Let's create variables for the promotional items, showing only the data for days when there was a promotional event:

```{r promoVariables, echo=TRUE, collapse=TRUE}
promoCap <- subset(baseball, baseball$cap == "YES")
promoShirt <- subset(baseball, baseball$shirt == "YES")
promoFireworks <- subset(baseball, baseball$fireworks == "YES")
promoBobblehead <- subset(baseball, baseball$bobblehead == "YES")
```

Now let's get a look at the output of the promotional variables:

```{r promoResults, echo=TRUE, collapse=TRUE}
promoCap

promoShirt

promoFireworks

promoBobblehead
```

Now let's get a look at the `summary` of the promotional variables:

```{r promoSummary, echo=TRUE, collapse=TRUE}
summary(promoCap)

summary(promoShirt)

summary(promoFireworks)

summary(promoBobblehead)
```

### Exploration of Promotions

Looking at the promotions, we see that of the four different types of promotions the Dodgers ran during home games this season, they broke down as follows:

| Promotion Type | Promotion Frequency | Mean Attendance |
|:--------------:|:-------------------:|:---------------:|
|      Cap       |         2           |     38,190      |
|     Shirt      |         3           |     46,644      |
|    Fireworks   |         14          |     41,078      |
|   Bobblehead   |         11          |     53,145      |

As a little synopsis of that information, it's probably fair to say that fireworks at the conclusion of a game are pretty common. Lots of teams do this, and they probably aren't a huge driver in the decision to take in a baseball game. The mean for attendance on games when fireworks for a promotion was 41,078. Not too shabby.

The cap and shirt promotions were pretty few and far between, with only five games offering a fan either of those giveaways. The mean attendance on cap giveaway games was 38,190 and on shirt giveaways it was 46,644.

But look at the bobbleheads. There were a total of eleven games when the Dodgers gave away a bobblehead, and the mean attendance during these games was 53,145. Dude. People love free stuff, and a bobblehead is just a really cool, quirky, and fun thing to have on your desk at work or home, eh?

### Box Plots

Now let's create a few box plots to get a look at our data. We'll start with one that looks at attendance on the days of the week:

```{r boxPlot1, echo=TRUE, collapse=TRUE}
# Boxplot of day of the week attendance:

boxplot(attend~day_of_week,data=baseball, main="Day of the Week Attendance", 
   xlab="Day", ylab="Attendance")
```

That's a bit messy so let's order the days like a regular weekly calendar rather than using the default alphabetical order. Let's also give the boxplot's color something more applicable to our example, the use of `dodgerblue`:[^1]

```{r boxPlotClean, echo=TRUE, collapse=TRUE}
baseball$day_of_week <- factor(baseball$day_of_week , levels=c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"))

# Boxplot of day of the week attendance:

boxplot(attend~day_of_week,data=baseball, main="Day of the Week Attendance", 
   xlab="Day", ylab="Attendance", las=2, col="dodgerblue")
```

A few things stand out here. It looks like Mondays and Wednesdays are the days of the week where fans aren't coming out for baseball. That makes sense because most people are either working or in school during the day, and at night might not come out due to getting an early start the next day for work or school.

Higher attendance on a Friday, Saturday, or Sunday makes sense.

### Terrific Tuesday

What's up with Tuesdays? Pulling in an average of 50,000 people on a Tuesday seems rather remarkable. Let's keep pulling this thread. Let's go in for a deeper dive on trying to see what drove that Tuesday attendance.

```{r tuesdays, echo=TRUE, collapse=TRUE}
tuesday <- subset(baseball, baseball$day_of_week == "Tuesday")
print(tuesday)
summary(tuesday)
```

Looking things over here, it seems the Dodgers are heavily using promotional giveaways on Tuesday to bring fans out. In fact, of the 13 home games on Tuesdays in their 2012 season, the Dodgers gave fans a free cap (1 time), shirt (1 time), and bobbleheads (6 times) just for showing up (and I'm assuming that the promo items are limited to the first x amount of fans to arrive as this encourages people to get there early/on time to receive the promotional item).

Just like in our Exploration of Promotions area earlier, we see that promotions are important for briging out crowds, and fans especially are fans of bobbleheads.

### Monday, Monday

Now let's isolate Mondays and see if we can tell why the draw on that day is so low:

```{r mondays, echo=TRUE, collapse=TRUE}
monday <- subset(baseball, baseball$day_of_week == "Monday")
print(monday)
summary(monday)
```

With a mean attendance of 34,966, Mondays were the lowest attendance draw at Dodger Stadium in 2012. One thing really stand out to me as a good reason why, that being how many promotions were done on Mondays: of the 12 home games on Mondays in 2012, the Dodgers only had 1 promotional giveaway, a shirt on June 11th against the Angels. The other thing that stands out? The night they gave away that shirt to their fans they had the largest Monday night crowd of the season bringing in 50,559 people. Swag fills the seats!

### Scatter Plots

Now let's create a few scatter plots to get a look at our data. We'll start with one that looks at attendance and the game time temperature to see if there's any correlation there:

```{python scatterPlot1, echo=TRUE, collapse=TRUE}
# Scatter plot of attendance and weather:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

baseball = pd.read_csv (r'dodgers.csv')

x = baseball.attend
y = baseball.temp

plt.scatter(x, y, c='c', alpha=0.5, s=150.00)
plt.title("Game Time Temps and Attendance")
plt.xlabel("Attendance")
plt.ylabel("Game Temperature")
plt.show()
```


### Linear Regression Model

I'd like to do linear regression analysis using game attendance and game time temperature to see if there is any impact. 

```{r regression, echo=TRUE, collapse=TRUE}
# Run our linear regression model:

simple.fit = lm(attend~temp, data=baseball)
summary(simple.fit)
```

A cursory glance at the regresion output:

* Residuals: The section summarizes the residuals, the error between the prediction of the model and the actual results.  Smaller residuals are better.
* Coefficients: For each variable and the intercept, a weight is produced and that weight has other attributes like the standard error, a t-test value and significance.
* Residual Standard Error: This is the standard deviation of the residuals.  Smaller is better.

Based upon a quick look at things here, the game time temperature doesn't really show that it impacts people coming out for games at Dodger Stadium.

### Train/Test and Regression Testing

Let's do some train/test splits on our data, again I will isolate weather:

```{python train, echo=TRUE, collapse=TRUE}
import pandas as pd
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from matplotlib import pyplot as pltd

# Import the baseball file into a data frame:
baseballP = pd.read_csv (r'dodgers.csv')
print(baseballP)

# Declare the column names:  
columns = "temp".split()
print(columns)

df = pd.DataFrame(baseballP, columns=columns)
print(df)

# define the attendand variable 'attend' (dependent variable) as y:
y = baseballP.attend

# Now we can use the train_test_split function in order to make the split. The test_size=0.2 inside the function indicates the percentage of the data that should be held over for testing. It’s usually around 80/20 or 70/30:

# Create the training and testing vars
X_train, X_test, y_train, y_test = train_test_split(df, y, test_size=0.2)
print(X_train.shape, y_train.shape)
print(X_test.shape, y_test.shape)
```

Now we’ll fit the model on the training data:
```{python train2, echo=TRUE, collapse=TRUE}
# fit a model
lm = linear_model.LinearRegression()
model = lm.fit(X_train, y_train)
predictions = lm.predict(X_test)
print(predictions)
```

Now let's plot that training model:

```{python trainPlot, echo=TRUE, collapse=TRUE}
## The line / model
plt.scatter(y_test, predictions)
plt.xlabel("True Values")
plt.ylabel("Predictions")
```

And our accuracy score:

```{python trainScore, echo=TRUE, collapse=TRUE}
print("Score:", model.score(X_test, y_test))
```

All of the training/test split info also yields points to temperature data not having a big impact on crowd size.

### Final Recommendation

After going through the data in different ways, including scatter plots, box plots, and regression analysis, my main recommendation is for the Dodgers marketing department to plan to offer more giveaway items, in particular, bobbleheads. Of the 11 times the Dodgers had a bobblehead giveaway, they put large numbers in the stadium. Looking through the data, they had a large turnout on Tuesdays, primarily due to bobblehead giveaways.

To answer the original problem — _"What night would be the best to run a marketing promotion to increase attendance?"_ — my recommendation is to start offering bobbleheads on Mondays to help bring more people out. Mondays were the lowest draw during the week, so giving the fans a reason to show up by giving them a freebie would be a good way to get attendance boosted on that day.

[^1]: Ugh, as a Cubs fan, this hurts, but I'll stay professional for the sake of this assignment.
