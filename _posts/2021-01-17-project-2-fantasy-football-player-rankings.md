---
title: "Project 2: Fantasy Football Player Rankings"
date: 2021-01-30T11:12:00-04:00
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
---

A project to explore the possibility of creating an accurate fantasy football player ranking system.

### Abstract

The simplistic beauty of fantasy football is that it is a wonderful and true microcosm of the real game — well, at least the non-physical parts. Luckily, you don’t have to go through training camp or be in elite physical shape to play the game. Instead, you fulfill nearly every other non-athletic role that real NFL teams have: owner, general manager, scout, statistics department, head trainer, team doctor, and of course, the head coach. During the duration of the fantasy football season, those of us who play in a league — or multiple leagues — are faced with a multitude of decisions. After you draft your team, each week you are tasked with choosing the best players at each position you feel will win you your matchup against your opponent. This sounds simple, right? The choice of who to start vs. who to leave sitting on your bench may seem like something that is just left up to luck or chance, or done by random choice. You drafted two great quarterbacks, you can just flip a coin as to who to start that weekend, right? Wrong.

### Executive Summary

Having success at fantasy football takes more than just luck or drafting the right players. Sure, those things help, but nearly every weekend, matchups are won or lost based upon individual performances that are either way above projections, or far below. What if I told you that you that those crazy highs and lows might actually be predictable?

Wanting to take the luck and randomness out of how my fantasy teams would perform each week, I had the idea to take a more analytical approach by creating a player ranking system for each position on the roster. This ranking would update each week, based upon a number of variables including offensive and defensive rankings, individual performance rankings and accuracy, and even weather data. My first stab at building an algorithm to spit out a player ranking system started with the kickers, and preliminary research has shown that a model to help predict who will score big — and who might tank — might actually give you a huge leg up to winning your league.

### Introduction and Background

It goes without saying that there are a lot of random things that happen during the course of an NFL football game that contribute to the game’s final outcome and individual player performance and statistics. But there are a multitude of variables that come into play even before opening kickoff that can provide you with information to help you make your decisions.

### Problem Statement

The problem that I will be addressing aims to take the randomness and guesswork out of weekly fantasy football matchups by creating a player ranking system. The rankings are driven by a unique algorithm for each of the following positions that comprise a typical fantasy football roster:

* Quarterback (QB) 
* Running Back (RB)
* Wide Receiver (WR)
* Tight End (TE)
* Kicker (K)
* Defense and Special Teams (DST)
* Defensive Player (D) 

_Note: for purposes of this project, I am only going to summarize one position on the fantasy football roster, that being the kicker. While each of the other positions will have their own separate ranking system, the algorithm for each position will share some common elements. However, due to the interest of time and scope, I will only discuss the kicker position and lay out the model used for this particular position._

### Detailed Background

The life of the special teams group in the game of American football is — to me — one of the most underrated parts of the game. For here we have the hidden yards including both kickoff and punt return yardage. These return yards aren’t shown in statistics for offense, but a great return game is just as important as any weapon on the offensive side of the ball. For example, a great punt and/or kick returner can set your offense up for a short touchdown drive, or in some cases of the outliers — the great return men of the game — swing momentum singlehandedly by scoring touchdowns. These hidden yards score points for a fantasy football owner under the DST position (Defense and Special Teams). But that is not the focus of this particular project.

The other primary pieces of special teams units are the guys with the golden legs: the kickers and punters. Actually, there are a few other huge components of this group, those being the holder and the long snapper, but they aren’t accounted for in fantasy football even though their jobs are a monumental part of special teams. I digress... To try to keep this brief, the punter kicks the ball away to the other team if the offensive unit stalls and is not within field goal range, and is also not accounted for in fantasy football — another travesty if you ask me. That leaves us with the kicker. Ahh yes, the kicker.

The kicker is the player that attempts to score his team points via field goals and PATs (points after touchdown). Most simply, they are most often either one of two things: a hero or a villain; the determination of which is usually upon the outcome of a single, last second, potentially game-winning kick, or a culmination of that game’s kicks. Make a game-winning kick as time expires? Hero! Miss 3 out of 5 and cost your team that day’s victory? Ugh, pack your bags you might not be long for this team. And trust me, I would know. As a Chicago Bears fan, I watched the team’s kicker double-doink us out of advancing in the Playoffs during the 2018 season. Double-doink? Oh, that’s a new phrase invented specifically for kicker Cody Parkey and it can be defined as such:

> “A game-winning field goal attempt in which the football hits one of the uprights —producing a loud DOINK sound — that then falls down onto the crossbar (making another loud DOINK sound) and finally, takes an un-fortuitous bounce off of said crossbar backwards into the end zone resulting in a miss and therefore no points.”

I will not delve more into that particular situation and its outcome; however, I will state that Mr. Parkey was released quickly after that miss concluded the Bears’ 2018 NFL season. But don’t think that his dismissal was an over-reaction to that one failed kick. Unfortunately (for me as a fan), the Bears didn’t release him because he missed just that one (hugely important!) kick at the most important point of their spectacularly winning season. Oh no. Parkey had plenty of other misses in 2018: out of 30 attempts that season, he made only 23 of them for an abysmal (by kicking standards) 76.7% accuracy rate. When you make your living making kicks in the NFL, that simply doesn’t cut it. As a human being, I feel for the guy. It’s hard to be perfect. But as a football fan of the Chicago Bears, I say good riddance.

I use that heart-wrenching narrative as a setup to this: the kicking position is extremely important. For real NFL teams, a good, reliable kicker with a solid, accurate leg is the thing that can give your team that ticker tape parade in February that all fans dream of. 

Greg “The Leg” Zeurlein kicked his Los Angeles Rams (a team the Bears soundly defeated in 2018) into the Super Bowl. Yes, sure, a little non-called pass interference might have had something to do with it, but the important thing is that the guy nailed some huge kicks (on the road in New Orleans) to get the NFC Championship game into overtime and eventually to win it.

The same goes for your fantasy team. You have to get this position right. All things being equal across the other positions, I feel having the top kicker — or kickers if you play in a league where you have two — each week on your roster is a very easy way to help you beat your opponent using almost the same “hidden yards” concept of the return game. Getting high scores from your kicker(s) on your fantasy team is like getting “hidden points”. Oh, and if your kicker outscores one of your opponents’ skill position players, that is just outright comical, and you sir or madam should be given bonus points.

### Methods and Technical Approach

Based upon research and EDA from asking the question “what are the biggest contributions to kicking attempts in a game?” I am hypothesizing that the best kickers to start on a given week — the ones who will score the most fantasy points — will most likely come from a combination of the following variables:

* A kicker with a high rate of accuracy
* A kicker’s offense with a high ranking in offensive efficiency
* A kicker’s offense with a low ranking in red zone efficiency
* A kicker facing a defense that has a high ranking in red zone efficiency
* A kicker’s team is a heavy favorite
* A kicker’s team is not a heavy underdog
* A kicker competing in a game that is expected to be close
* The weather will not have a detrimental impact on the kicking game

### Data Sources

My data sources consist of a mixture of the following:

* NFL statistics and/or data sets from Pro Football Focus
* Fantasy football statistics, content, and data sets from FantasyPros
* Forecasted weather data for NFL stadiums from various sites; in particular hyper-local weather data such as available via Dark Sky.

### Analysis

My model will rank kickers before the week’s games on a week-by-week basis, and can be adjusted as needed. For example, the weight that one of the variables has in determining the final ranking might show over time that it is either too high or too low. How much impact does bad weather have? Is kicking in rain harder than kicking in wind? What about snow? Does it matter if its a dry powdery snow or a wet, heavy snow? Analysis will help drive the answers to these questions and the kicker ranking algorithm.

### Variables

To try to accurately predict how kickers in the NFL will perform during a week’s games, I will attempt to create a model that uses the variables talked about previously in the Technical Approach section. Let’s dig into these variables briefly.

It’s important to understand why these eight items stand out, as they are the variables that will make up the kicker ranking algorithm. I will do this as succinctly as possible: You want to start a kicker with a high rate of accuracy, plays for a team with a highly efficient offense, and one that is less prone to score touchdowns once they get into their opponent’s red zone. Additionally, the algorithm will call for the kicker’s opposing defense to be really good at preventing touchdowns in the red zone, the kicker’s team to not be a heavy underdog, and the kicker’s team expecting to either win big or be in a close game. Finally, the weather needs to not be a reason why the kicking game would be impacted in a detrimental reason.

My research has shown that the kicker position in fantasy football is rather unique in that starting the same kicker throughout the course of the season (as is pretty typical with a fantasy team) might not ultimately be the best strategy — nor is it always the best strategy to start a kicker that plays for a team with only a highly potent offense.
 
The best kickers to start each week can be determined from the output of a certain set of criteria; as a season progresses, the outputs from these criteria can and will change — for example, think of a kicker’s accuracy as a season progresses, some kickers get better over time, others might trend downhill. It’s common in the NFL for a kicker to start a season off strong, but start to lose confidence with a few misses. Last season, one of the NFL’s best kickers of all time, Adam Vinatieri, almost quit the Colts one day after a handful of missed kicks early on in the season.

### Looking into the Data

To take a swing at my kicker ranking concept, I took a random week from the latter portion of the 2018 NFL season to work with, primarily because I wanted to have a culmination of previous game weeks’ data to work with. First, let’s load in our NFL Week 12 kicker ranking dataset and get a quick summary and look at the data:

```python
2018_w_12_k_data
##                    Name Accuracy Team Opponent Spread OU OppRZD OffRZEff OffRank       Weather            KPlus
## 1       Michael Badgley    100.0  LAC  vs. ARI  -13.0 44     12       13    7     73F, Light Wind          68
## 2      Ka’imi Fairbairn     81.5  HOU  vs. TEN   -6.5 41      2        3   13            Dome              67
## 3         Aldrick Rosas     95.2  NYG   at PHI    7.0 46      7        6   23     55F, 7 MPH Wind          61
## 4         Jason Sanders     93.8  MIA   at IND   10.0 51      9        0   28            Dome              59
## 5          Cairo Santos     83.3   TB   vs. SF   -3.0 54     16       15    1     80F, 7 MPH Wind          57
## 6          Mason Crosby     76.9   GB   at MIN    4.0 48      1       18    8            Dome              56
## 7       Brandon McManus     82.4  DEN  vs. PIT    3.0 48     13       10   11     45F, 8 MPH Wind          54
## 8            Dan Bailey     82.4  MIN   vs. GB   -4.0 48     11        9   14            Dome              54
## 9    Stephen Gostkowski     86.4   NE   at NYJ   -9.0 47      8       22   10     55F, 7 MPH Wind          52
## 10        Justin Tucker     90.5  BAL  vs. OAK  -12.0 43     10       21   12     55F, Light Wind          52
## 11       Dustin Hopkins     85.0  WAS   at DAL    9.0 41      3       12   25            Dome              51
## 12          Brett Maher     84.0  DAL  vs. WAS   -9.0 41      5        8   27            Dome              50
## 13         Jake Elliott     77.8  PHI  vs. NYG   -7.0 46      6       11   19     55F, 7 MPH Wind          50
## 14           Josh Lambo     94.4  JAC   at BUF   -3.0 38     25        5   21     41F, Light Wind          46
## 15          Jason Myers     91.3  NYJ   vs. NE    9.0 47     20        1   29     55F, 7 MPH Wind          46
## 16         Robbie Gould     95.5   SF    at TB    3.0 54     32        4   17     80F, 7 MPH Wind          45
## 17       Adam Vinatieri     83.3  IND  vs. MIA  -10.0 51     15       24    9            Dome              43
## 18          Matt Bryant    100.0  ATL    at NO   14.0 60     28       23    6            Dome              43
## 19          Matt Prater     86.4  DET  vs. CHI    3.0 45     21        7   24            Dome              41
## 20             Wil Lutz     95.5   NO  vs. ATL  -14.0 60     29       28    4            Dome              37
## 21          Cody Parkey     76.2  CHI   at DET   -3.0 45     17       20   16            Dome              36
## 22      Steven Hauschka     93.8  BUF  vs. JAC    3.0 38     14       17   31     41F, Light Wind          36
## 23          Graham Gano     91.7  CAR  vs. SEA   -3.0 47     18       29   15     53F, Light Wind          35
## 24       Daniel Carlson     63.6  OAK   at BAL   12.0 43     22        2   22     55F, Light Wind          34
## 25          Greg Joseph     84.6  CLE   at CIN    3.0 48     23       19   18     53F, 6 MPH Wind          34
## 26        Chris Boswell     72.7  PIT   at DEN   -3.5 48     19       30    5     45F, 8 MPH Wind          33
## 27          Ryan Succop     85.7  TEN   at HOU    6.5 41     30       14   30            Dome              22
## 28 Sebastian Janikowski     75.0  SEA   at CAR    3.0 47     31       25   20     53F, Light Wind          18
## 29        Randy Bullock     75.0  CIN  vs. CLE   -3.0 48     24       31   26     53F, 6 MPH Wind          14
```

Here’s the summary of the variables in that data: 

* ```Name```: The kicker.
* ```Accuracy```: The kicker’s rate of accuracy on the season so far.
* ```Team```: The kicker’s team.
* ```Opponent```: The team the kicker is facing this week.
* ```Spread```: The expected/predicted point spread of the game as determined by oddsmakers. A negative number means the kicker’s team is favored. For example a -7 means the kicker’s team is predicted to win by 7 points.
* ```OU```: The predicted over/under of this game as determined by oddsmakers. This is the expected total combined score of the two teams. A game with a high OU is expected to be a high scoring game, a low OU means lower scoring.
* ```OppRZD```: The ranking of the kicker’s opponent’s red zone defense. A low number here means that the defense is good at preventing touchdowns when their opponent reaches the red zone (20 yards from the goal line).
* ```OffRZEff```: The kicker’s team’s red zone efficiency. A low number here mans that the kicker’s team has a hard time scoring touchdown when they get into the red zone and are more likely to have to kick field goals.
* ```OffRank```: The kicker’s team’s offensive efficiency. A low number here means that the kicker’s offense is good at moving the ball down the field. This is good because a team that moves the ball is more likely to score points. 
* ```Weather```: This is the predicted weather data for the game. If it’s raining heavily or snowing or windy, this will impact the kicking game.
* ```KPlus```: This is the output of my algorithm that takes into account the other variables in the data set. The higher the number here, the better — this drives the ranking order. 

### Charts and Plots

Let’s look at two scatter plots from the data set. The first one shows our projected kicker rankings plotted out on a grid with the variables for offensive red zone efficiency and the opponent’s red zone defense: 

![Chart 1](/assets/images/chart_1.png)

Looking at this scatter plot, it’s easy to see that when a kicker’s team has a low offensive red zone efficiency and their opponent has a strong red zone defense (lower ranking), that’s a good combination for the potential for the kicker to rank highly in the projections (the KPlus score).

Now I would like to present another example, this one showing the projected kicker rankings with the variables for the game’s projected point spread and over / under:

![Chart 2](/assets/images/chart_2.png)

Looking at the second scatter plot, it’s not as easy to discern how the over / under and point spread play into the projections for the kicker, but a few things stand out. Kickers playing in games that are expected to be close have a better chance to do better than those that are expected to be in a blowout loss. Also, kickers playing for teams that are projected to win by a large margin should fare well.

Next, I’d like to take a look at the data doing some regression testing. Here’s the first chart:

![Chart 3](/assets/images/chart_3.png)

From that chart, we can see that the lower the ranking of a kicker’s opponent’s red zone defense is, the better chances there are for a kicker to score points via field goals.

This next chart shows a regression analysis using the KPlus variable as the dependent variable, and the OffRZEff variable as the independent(explanatory) one:

![Chart 4](/assets/images/chart_4.png)

That chart is more visual information that we are on to something here. It looks like kickers on teams that have a low offensive red zone efficiency — they are not good at scoring touchdowns — is a great thing for a kicker, thus likely to have a higher ranking in the algorithm.

### Testing the Hypothesis

Okay, now it’s time to really put all of this together. Using the information from our variables, it is now time to mash them up into an algorithm to drive the model that will power our kicker ranking system. The data in this dataset that the KPlus scores is built from comes from a multitude of sources, including weekly NFL offensive and defensive rankings, kicker accuracy, and weather information from the sites listed in the Data Sources section. As you will see, the primary determinant of the kicker ranking system is the KPlus column, which is a column that I created; the values here come from a unique algorithm using the variables from the data that I described above. The higher the KPlus number, the better. Here is the projected rankings:

![Chart 5](/assets/images/chart_5.png)

Now let’s look at how the kickers actually performed in Week 12 of the 2018 season and see how our prediction rankings fared using similar charts as the ones used to present the projected rankings:

![Chart 6](/assets/images/chart_6.png)

It looks like we have a big outlier here as far as Janikowski; he wasn’t projected to do that well but he ended up tied for the league in points at the kicking position. On the other hand, the three top projected kickers did well, as two out of the three tied for the lead in points this week, while Badgley wasn’t too far behind them.

### Conclusion

The frustrations at the kicker position on my fantasy football roster over various years of playing is the primary reason I chose to key in on it for this project; as such, I set about finding a good way to help predict success at this position by creating an algorithm that could rank each week’s kickers based upon numerous variables pulled from numerous sets of data.

While much of what happens in football can seem random, I believe that by using as much information as possible, we do have a chance at making fantasy football performance forecasting models based upon numerous variables and research.

### Acknowledgements

I owe credit to numerous people in the “regular” football analysis and fantasy sports world, including the writers at fantasypros.com, and in particular Mike Tagliere. His writing and podcasts have really helped me to understand some of the more important “game behind the game” types of things. Additionally, Andrew Swanson who writes at FantasyPros and individually was a primary influence with his “K Score” metric. I took what Andrew and “Tags” talk about and tried to build upon that. Last, I want to thank my family for putting up with me during fantasy football season. I know there are days I am not easy to deal with when my mind is wrapped in data and numbers!

### References and Annotations:

1. Lese, Jared. (2021). “2020 Season in Review: Measuring Consistency” from [https://www.fantasypros.com/2021/01/2020-season-in-review-measuring-consistency-fantasy-football/](https://www.fantasypros.com/2021/01/2020-season-in-review-measuring-consistency-fantasy-football/).
2. NFL. (2021). “Fantasy Football” from [https://fantasy.nfl.com](https://fantasy.nfl.com).
3. ESPN. (2021). “Leagues, Rankings, News, Picks, & More” from [https://www.espn.com/fantasy/football/](https://www.espn.com/fantasy/football/).
4. CBS Sports. (2021). “Fantasy Football News, Stats, and Anaylsis” from [https://www.cbssports.com/fantasy/football/](https://www.cbssports.com/fantasy/football/).
5. Yahoo Fantasy Football. (2020). “Fantasy Football 2020” from [https://football.fantasysports.yahoo.com/](https://football.fantasysports.yahoo.com/).
6. Fantasy Football Today. (2020). “Fantasy Football Today” from [https://www.fftoday.com/](https://www.fftoday.com/).
7. Pro Football Reference. (2020). “Pro Football Statistics and History” from [https://www.pro-football-reference.com/](https://www.pro-football-reference.com/).
8. The Football Database. (2020). “2020 NFL Statistics” from [https://www.footballdb.com/stats/index.html](https://www.footballdb.com/stats/index.html).
9. Pro Football Reference. (2020). “2020 NFL Opposition & Defensive Statistics” from [https://www.pro-football-reference.com/years/2020/opp.htm](https://www.pro-football-reference.com/years/2020/opp.htm).
10. Pro Football Reference. (2020). “2020 NFL Standings & Team Stats” from [https://www.pro-football-reference.com/years/2020/](https://www.pro-football-reference.com/years/2020/).



## Project Proposal

### Which Domain?

_What domain is this data going to come from? Please list 10 references (with a brief annotation) to use to make sense of what you’re doing with these data._

Fantasy football has been a passion of mine for over ten years. While a lot of what happens each weeks seems to be chance or luck or just completely random, I’ve been working on creating a way to more accurately predict player performance — and thereby the chances of fantasy football scoring success and winning your fantasy league — by generating a ranking algorithm for players on a weekly basis, starting with the position of kicker.

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

## Project Check-In

### _Any surprises from your domain from these data?_

So far there are not too many surprises from the data that I am working with. Overall, I am quite happy with the outcome of my data exploration and analysis, and I have learned quite a bit when it comes to creating a system to help take the guesswork out of something that seems so random (fantasy football players scoring points). I know that there is a lot more to do to really pinpoint the potential accuracy of the kicker ranking algorithm, and one way that I can do that is to continue get old game data and run that through my model to see how accurate things are shaping up to be.

### _Is the dataset what you thought it was?_

Going into this particular project, I thought there would be readily available downloadable datasets for doing the type of analysis I planned on doing for this task. And while to some extent that is true, I have found that a lot of my data work is being done manually, since I am looking at data on a weekly basis and am working to predict fantasy football kicker success every week of a fantasy football season. There’s no magic datasets out there that have all the things I’m looking into so it takes time to manually create the datasets. That said, in the future, web scraping and automation could really make all of this a lot easier.

### _Have you had to adjust your approach or research questions?_

Before I began this project, I very much expected the high-scoring kickers in fantasy football to all come from high-powered offenses, or teams that always win. I was way off base here. The best kickers in fantasy football are a lot of times on mediocre or even bad teams (from a won-loss perspective). A lot of my adjustments came after understanding that the best weekly kickers in fantasy football are usually from teams that aren’t good at scoring touchdowns when they get into the opponent’s red zone, and additionally, the defense the kicker is going up against is very stingy in the red zone at allowing touchdowns.

### _Is your method working?_

As I continue to make my way through the fantasy player, NFL statistics, and game-day stadium weather data, I look to get clarity in my search to be able to predict fantasy football player success; thus far, the methods for analyzing and creating a prediction model actually appear to be working. I have gotten a detailed look at past years’s kicking game performances and see that some of my concepts for predicting higher scoring performance appear to be holding true. There is more work to do to verify accuracy, and time will tell if the ideas that I have here will completely pan out, but I believe that they will based upon what I am seeing so far.

### _What challenges are you having?_

I think one of the main challenges I am having is that I did not fully understand nor appreciate just how much time this would take, and to expand on that just a bit, I didn’t comprehend the complexities of building accurate data models. That applies to not just for this project, but also to data science as a whole. I very much understand now how the entire data cycle flow is time-consuming, and I understand just how engrossing it is to ensure that your data is accurate and not biased, especially when you are passionate about the outcome.

## Questions and Answers

_Why did you choose this as a project subject?_

I’ve been a fantasy football enthusiast for over a decade, and while there’s not much hope for my real football team (the Chicago Bears) until they get a franchise quarterback, it’s fun to enjoy the play of other players in the NFL by having them on my team(s). I’ve noticed that I enjoy watching the NFL more in general since becoming a fantasy football player.

_Did anything during this project surprise you? In what way?_

I was a bit surprised at how much sense it made when researching the best way to work on the kicker algorithm. It seemed like it was too good to be true. It’s not perfect, but it’s a good start.

_Is there anything that you would have done differently?_

I think eventually that I would like to work with someone on this project and see if we can really make some progress on a true roster-wide, weekly updated ranking for each player position.

_Did you get all of the answers to your research questions?_

I was able to get all of the answers to my research questions, and believe that there is a way to create an accurate prediction for the kicker position each week.

_What would you have liked to have gone better?_

Creating a weekly updated ranking algorithm for all fantasy football positions would be like a secret weapon, but it was beyond the scope of this project.

_How do you feel about the role of analytics in sports?_

I love the fact that analytics are becoming such a big factor in all of sports. It’s really fun for me to see the intersection of science and data with athletics.

_What good (if any) came as a result of this project?_

I believe that this project is a great start on the beginning of something that can become a viable fantasy football prediction system, and possibly something to continue exploring and working on.

_Are there any other research questions you would like to try to find answers for?_

I wish that I could find the answer as to why the Chicago Bears are so terrible at attaining a franchise quarterback. They are the oldest team in the NFL, and the fact that they have never had a quarterback other than Sid Luckman in the 1940s to consistently lead the team is both pathetic and heartbreaking at the same time. The fact that my team’s arch rival has had best-in-the-league QB play for nearly thirty years straight from just two different players is maddening.

_Do you play in any of the daily fantasy sites or do any sports betting?_

I don’t partake in any of the daily fantasy football stuff, or do any sports betting. It’s just not my cup of tea. I prefer my betting to take place in the stock market.

_Is this project something you would like to continue working on?_

I would most definitely like to continue working on the fantasy football player ranking system; having something that updates weekly prior to each week’s slate of games during the season would be a wonderful tool to help win.

## Project Presentation

[Apple Keynote format](/assets/Fantasy_Football_Player_Rankings.key)

[Microsoft PowerPoint format](/assets/Fantasy_Football_Player_Rankings.pptx)

- [Project Report](#abstract)
- [Project Proposal](#project-proposal)
- [Project Check-In](#project-check-in)
- [Questions and Answers](#questions-and-answers)
- [Project Presentation](#project-presentation)
