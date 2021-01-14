---
title: "Project 2: Fantasy Football Player Rankings"
date: 2021-01-17T14:30:00-04:00
categories:
  - blog
tags:
  - fantasy football
  - project 2
  - projects
  - player rankings
classes: wide
header:
    image: /assets/images/football.jpg
    image_description: "An American-rules football field"
    caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
---

A project to explore the possibility of creating an accurate fantasy football player ranking system.

- [Project Proposal](#project-proposal)
- [Project Check-In](#project-check-in)
- [Project Report](#project-report)
- [Questions and Answers](#questions-and-answers)
- [Project Presentation](#project-presentation)

## Project Proposal

### Which Domain?

_What domain is this data going to come from? Please list 10 references (with a brief annotation) to use to make sense of what you’re doing with these data._

Fantasy football has been a passion of mine for over ten years. While a lot of what happens each weeks seems to be chance or luck or just completely random, I’ve been working on creating a way to more accurately predict player performance — and thereby the chances of fantasy football scoring success and winning your fantasy league — by generating a ranking algorithm for players on a weekly basis, starting with the position of kicker.

#### References and Annotations:
1. Lese, Jared. (2021). “2020 Season in Review: Measuring Consistency” from [https://www.fantasypros.com/2021/01/2020-season-in-review-measuring-consistency-fantasy-football/](https://www.fantasypros.com/2021/01/2020-season-in-review-measuring-consistency-fantasy-football/).
2. NFL. (2021). “Fantasy Football” from [https://fantasy.nfl.com](https://fantasy.nfl.com).
3. ESPN. (2021). “Leagues, Rankings, News, Picks, & More” from [https://www.espn.com/fantasy/football/](https://www.espn.com/fantasy/football/)
4. CBS Sports. (2021). “Fantasy Football News, Stats, and Anaylsis” from [https://www.cbssports.com/fantasy/football/](https://www.cbssports.com/fantasy/football/).
5. Yahoo Fantasy Football. (2020). “Fantasy Football 2020” from [https://football.fantasysports.yahoo.com/](https://football.fantasysports.yahoo.com/).
6. Fantasy Football Today. (2020). “Fantasy Football Today” from [https://www.fftoday.com/](https://www.fftoday.com/).
7. Pro Football Reference. (2020). “Pro Football Statistics and History” from [https://www.pro-football-reference.com/](https://www.pro-football-reference.com/).
8. The Football Database. (2020). “2020 NFL Statistics” from [https://www.footballdb.com/stats/index.html](https://www.footballdb.com/stats/index.html).
9. Pro Football Reference. (2020). “2020 NFL Opposition & Defensive Statistics” from [https://www.pro-football-reference.com/years/2020/opp.htm](https://www.pro-football-reference.com/years/2020/opp.htm).
10. Pro Football Reference. (2020). “2020 NFL Standings & Team Stats” from [https://www.pro-football-reference.com/years/2020/](https://www.pro-football-reference.com/years/2020/).

### Which Data?

_What is the dataset you’ll be examining? Please provide a codebook if there is one or a link to the dataset as well as a detailed description._

My data sources consist of a mixture of NFL statistics and/or data sets from Pro Football Focus, fantasy football statistics, content, and data sets from FantasyPros, and forecasted weather data for NFL stadiums from various sites; in particular hyper-local weather data.             2

### Research Questions? Benefits? Why Analyze these Data?

_How are you proposing to analyze this dataset? This is about your approach. Here, you’ll be proposing your research questions as well as justifications for why you’d offer these data in this way._

I specifically want to know if an accurate prediction system can be created using data from previous games and current matchup-related information. A few of the research questions I want to answer are if you should you start the same exact players each week? Are the best players always the ones from the best overall team? How much does the weather impact fantasy football scoring?

### What Method?

_What methods will you be using? What will those methods provide in terms of analysis? How is this useful?_

My model will rank kickers before the week’s games on a week-by-week basis, and can be adjusted as needed. For example, the weight that one of the variables has in determining the final ranking might show over time that it is either too high or too low. How much impact does bad weather have? Is kicking in rain harder than kicking in wind? What about snow? Does it matter if its a dry powdery snow or a wet, heavy snow? Analysis will help drive the answers to these questions and the kicker ranking algorithm. These should help to provide clarity on which players to start each week and help show any trends or patterns in the data as to which players on your roster to start or sit, or if you should pick up a fee agent player or snag one from the waiver wire.

### Potential Issues?

_What challenges do you anticipate having? What could cause this project to go off schedule?_

I am concerned that the ranking system I am attempting to generate won’t be accurate and will not provide any help in setting your roster.

### Concluding Remarks

My research has shown that the kicker position in fantasy football is rather unique in that starting the same kicker throughout the course of the season (as is pretty typical with a fantasy team) might not ultimately be the best strategy — nor is it always the best strategy to start a kicker that plays for a team with only a highly potent offense. I look forward to exploring more with data from previous games to find out.
