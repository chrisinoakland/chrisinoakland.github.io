---
title: "Project 2: Fantasy Football Player Rankings"
date: 2021-01-24T14:30:00-04:00
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

## Project Report

### Executive Summary

Having success at fantasy football takes more than just luck or drafting the right players. Sure, those things help, but nearly every weekend, matchups are won or lost based upon individual performances that are either way above projections, or far below. What if I told you that you that those crazy highs and lows might actually be predictable?

Wanting to take the luck and randomness out of how my fantasy teams would perform each week, I had the idea to take a more analytical approach by creating a player ranking system for each position on the roster. This ranking would update each week, based upon a number of variables including offensive and defensive rankings, individual performance rankings and accuracy, and even weather data. My first stab at building an algorithm to spit out a player ranking system started with the kickers, and preliminary research has shown that a model to help predict who will score big — and who might tank — might actually give you a huge leg up to winning your league.

### Abstract

The simplistic beauty of fantasy football is that it is a wonderful and true microcosm of the real game — well, at least the non-physical parts. Luckily, you don’t have to go through training camp or be in elite physical shape to play the game. Instead, you fulfill nearly every other non-athletic role that real NFL teams have: owner, general manager, scout, statistics department, head trainer, team doctor, and of course, the head coach. During the duration of the fantasy football season, those of us who play in a league — or multiple leagues — are faced with a multitude of decisions. After you draft your team, each week you are tasked with choosing the best players at each position you feel will win you your matchup against your opponent. This sounds simple, right? The choice of who to start vs. who to leave sitting on your bench may seem like something that is just left up to luck or chance, or done by random choice. You drafted two great quarterbacks, you can just flip a coin as to who to start that weekend, right? Wrong.

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


