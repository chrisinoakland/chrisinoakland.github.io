---
title: "Project 1: Titanic Crew Member Survival Data"
date: 2020-12-13T14:34:30-04:00
categories:
  - blog
tags:
  - titanic
  - project 1
  - projects
---

- [Project Proposal](#project-proposal)
- [Project Check-In / Milestone 2](#project-check-in--milestone-2)

## Project Proposal

### Which Domain?

_What domain is this data going to come from? Please list 10 references (with a brief annotation) to use to make sense of what you’re doing with these data._

The sinking of the Titanic is a heart-breaking tale, and while much of the tragedy focuses on the passengers of the ship, I feel the workers have a story that goes untold. My first project will be an analysis of the crew members employed by the White Star Line that were aboard the fateful voyage.

#### References and Annotations:
1. Harrell, Frank E. (2002, December 27). "Titanic Data” from [http://biostat.mc.vanderbilt.edu/wiki/pub/Main/DataSets/titanic.html](http://biostat.mc.vanderbilt.edu/wiki/pub/Main/DataSets/titanic.html)
2. Zuckerman, Arthur. (2020, May 24). “57 Titanic Statistics: Deaths, Passengers & Survivors” from [https://comparecamp.com/titanic-statistics/](https://comparecamp.com/titanic-statistics/)
3. Encyclopedia Titanica. (2020). “Titanic Crew Survivors” from [https://www.encyclopedia-titanica.org/titanic-crew-survivors/](https://www.encyclopedia-titanica.org/titanic-crew-survivors/)
4. Ultimate Titanic. (2012, April). “Titanic: By the Numbers” from [https://www.ultimatetitanic.com/facts-statistics/](https://www.ultimatetitanic.com/facts-statistics/)
5. Encyclopedia Britannica. (2020). “Titanic” from [https://www.britannica.com/ topic/Titanic](https://www.britannica.com/ topic/Titanic)
6. Titanic Database. (2012, April). “List of crew members on board RMS Titanic” from [https://titanicdatabase.fandom.com/wiki/Crew_of_the_RMS_Titanic](https://titanicdatabase.fandom.com/wiki/Crew_of_the_RMS_Titanic)
7. History on the Net. (2020). “The Titanic — Crew” from [https://www.historyonthenet.com/the-titanic-crew](https://www.historyonthenet.com/the-titanic-crew)
8. Lehnhardt, Karin. (2019, July 3). “45 Unsinkable Titanic Facts” from [https://www.factretriever.com/titanic-facts](https://www.factretriever.com/titanic-facts)
9. RMS Titanic - Ship of Dreams. (2014). “Designing & Building Titanic” from [http://www.titanicandco.com/construction.html](http://www.titanicandco.com/construction.html)
10.History. (2020, October 30). “Titanic by the Numbers: From Construction to Disaster to Discovery” from [https://www.history.com/news/titanic-facts- construction-passengers-sinking-discovery](https://www.history.com/news/titanic-facts- construction-passengers-sinking-discovery)

### Which Data?

_What is the dataset you’ll be examining? Please provide a codebook if there is one or a link to the dataset as well as a detailed description._

For information specifically on Titanic’s crew, I will be using data from the Titanic People Database as created by Encyclopedia Titanica. More information can be found at [https://www.encyclopedia-titanica.org](https://www.encyclopedia-titanica.org). The site has an online and downloadable listing of records of passengers and crew, survivors, etc. I’m a bit of a Titanic junkie, so I already had a subscription to this site which allows for more granular downloading of data in csv format. Another source of data is Kaggle: [https://www.kaggle.com/c/titanic/data](https://www.kaggle.com/c/titanic/data).
             2

These are a few of the variables that I will be exploring:

| Variable  | Definition   | Key  |
|---|:-:|--:|
| PassengerId | Passenger ID | |
| Survived  | Survival     | 0 = No; 1 = Yes   |
| Pclass    | Ticket class  | 1 = 1st, 2 = 2nd, 3 = 3rd  |
| Name | Name of passenger |   |
| Sex  | Sex  |   |
| Age  | Age in years  |   |
| SibSp  | # of siblings / spouses aboard the Titanic  |   |
| Parch  | # of parents / children aboard the Titanic  |   |
| Ticket  | Ticket number  |   |
| Fare  | Passenger fare  |   |
| Cabin  | Cabin Number  |   |
| Embarked  | Port of Embarkation  | C = Cherbourg, Q = Queenstown, S = Southampton  |

### Research Questions? Benefits? Why Analyze these Data?

_How are you proposing to analyze this dataset? This is about your approach. Here, you’ll be proposing your research questions as well as justifications for why you’d offer these data in this way._

I specifically want to know about the survival rate of Titanic’s crew. How many total crew members were there and how many survived? How many were men and how many were women? In which parts of the ship did they work? At which port did they board the ship? I will be using Python and/or R to do the data analysis an attempt to find answers to these questions.

### What Method?

_What methods will you be using? What will those methods provide in terms of analysis? How is this useful?_

The methods I will use for the analysis of the crew survivors will most likely include bar charts, ROC curve, and logistic regression. These will provide clarity on crew members, who survived, and if there are any trends or patterns in the data as to why they survived while others did not.

### Potential Issues?

_What challenges do you anticipate having? What could cause this project to go off schedule?_

I am worried about not having enough information to draw any conclusions that I will be able to state definitively whether there are any actual predictors to which crew members would have survived the sinking.

### Concluding Remarks

There were many people that died when RMS Titanic sank on its maiden voyage in April 1912, including those who were crew members, employed by the White Star Line to service the passengers on the ship. I am exploring data on the crew members to look for any trends in the data from those that survived the disaster.

## Project Check-In / Milestone 2

### _Any surprises from your domain from these data?_

The sinking of the Titanic is a heart-breaking tale, and while much of the tragedy focuses on the passengers of the ship, I feel the workers have a story that goes untold. My first project is an analysis of the crew members employed by the White Star Line that were aboard the fateful voyage. So far, there isn’t anything too surprising with the data; however, it was a bit jarring to see how far many more men were members of the crew than women. But after looking over the data and seeing it from the perspective of the different departments, it began to make sense as there were many more men that were parts of the crew to shovel coal into the boilers to provide power and electricity to the steam-powered ship.

### _Is the dataset what you thought it was?_

Going into it, I was pretty confident that that dataset from the Titanic People Database as created by Encyclopedia Titanica — [https://www.encyclopedia-titanica.org](https://www.encyclopedia-titanica.org) — was going to be what I expected, and it turned out that it was. As I’m a bit of a Titanic diehard, I already had a subscription to this site which allows for more granular downloading of data in csv format and I was able to view online and download a listing of records of all crew data including survival data. I also retrieved data from Kaggle: [https://www.kaggle.com/c/titanic/data](https://www.kaggle.com/c/titanic/data) as a way to do cross-referencing and build out a more complete dataset if/as needed.

### _Have you had to adjust your approach or research questions?_

We are a few weeks in, and so far I have not yet had to adjust my approach or research questions. With the data that I have, I can see how many total crew members there were on the ship, and how many of them survived. I have a dataset showing how many crew members were men and how many were women, and I can also see the different departments of the ship they worked in — for example, engineering, hospitality, etc. Another interesting data point is the port (city) in which they boarded Titanic and began their working journey on the trip to New York.

### _Is your method working?_

As I make my way through the data and look to get answers to my questions, the methods for analyzing Titanic crew survivor data appear to be working. I have gotten a good look at some of the information using bar charts, a nice and simple way to see the answers to my questions. Another part of the process has been converting categorical data for the port city information to numerical data and that has gone smoothly as well. Time will tell if the ideas that I have here will completely pan out but I believe that they will based upon what I am seeing so far.

### _What challenges are you having?_

Regarding challenges, I am still working through the best way to present the data. I am comfortable displaying this information using a combination of bar charts and other methods, but am wondering if there is something else that would work as effectively or better. I am contemplating the idea of creating something more visually appealing such as a nice infographic and using multiple graphics to help better tell the data story of the crew and where they worked on the ship, such as their physical location and deck level on the ship. As I work more through the data, I am sure that the best answer will present itself.