---
permalink: /projects
layout: page
title: Projects
---
I consider projects to be large, long-term undertakings done usually in a group. These projects are usually created as a submission for a data science competition, but some can be made for own personal interest.

## Play Value Without Penalty(October 2023 - January 2024)[[Write-up]](https://www.kaggle.com/code/louzhou/pvwpbigdatabowl){:target="_blank"}

This group project looked to propose a new way for the NFL to punish tackling penalties by proposing a new metric, Play Value Without Penalty(PVWP), which looks into situations where it would be beneficial for defenders to intentionally commit a penalty to prevent a large yardage gain by accounting for both the difficulty of performing a legal tackle(instead of the penalty) as well as the potential yardage gain of the play without the influence of the tackler(who drew the penalty). If the PVWP exceeded the normal yardage penalty of the foul, then the PVWP value should be the yardage penalty.

To account for the difficulty of the tackle, we generated an xTackle model by running a Random Forest in a strictly one-on-one situation between the tackler and the ball carrier and found the probability that the defender would miss the tackle. For the yardage gain of the play, we generated an xYard model by running another Random Forest which used tracking data of the nearest three defenders and nearest two offensive players(on top of the ball carrier) to predict how many yards a play would generate.

In calculating PVWP, for each defensive tackling penalty, we found the odds of missing the tackle through our xTackle model and then ran the xYard model at the frame of first contact, eliminating the influence of the tackler by replacing them with the fourth closest defensive player.

Although it is very rare for penalties to be beneficial for the defense, PVWP both covers those rare cases and discourages defenders from even considering intentionally executing dangerous tackles(like horse collar or tripping tackles) to prevent large yardage gains, preventing injury and making the game safer.

This project was created as a submission to the 2024 Big Data Bowl as well as for academic credit(SMGT 499) through the Rice Department of Sports Management.

## Breaking the Cycle: Reducing Recidivism in Iowa State Prisons(October 2022 - May 2023)[[Write-up]]({% link /projects/MTFC 2023.pdf %}){:target="_blank"}

This group project evaluates the factors contributing to prison recidivism and looks to predict the total fiscal cost of recidivism for the May 2023 population of the Iowa state prison system. To do this, we created a binary classifier using a Feedforward Neural Network which would predict the probability that an inmate, given certain variables, would re-offend. 

Since it was found that time-sensitive, county-level data(e.g. unemployment rate) affected recidivism rates, we fit distributions to model the length of an inmate's sentence, given the severity of the crime, and created regressions to model the county-level data at release time. We also used previous data to find the odds of an inmate committing a different severity of crime, given that they re-offend.

These models were used in a Monte Carlo simulation, where for each trial, the simulation predicts the release month of each inmate and the county-level parameters at that time. Using these variables, a Feedforward Neural Network predicts the odds of recidivism. We also find what level of crime would be committed, given re-offense, for each crime. We would then find the expected cost of recidivism by multiplying all the odds of recidivism by the fiscal cost of the predicted severity of crime.

For factor analysis, we used the SHAP(SHapley Additive exPlantations) library which used Shapley values from game theory to find which variables had the most effect on an inmate's probability of re-offense.

This project was created as a submission for the 2023 Modeling the Future Challenge(MTFC), where we finished 2nd place out of 227 teams, gaining a $15,000 team award as well as a publication in the 2023 edition of the Actuarial Clearing House publication.

## Riding into the Future: Evaluating E-Bikes(March 2023)[[Write-up]]({% link /projects/M3 2023.pdf %}){:target="_blank"}

This group project predicted the growth of electronic bikes in the United States as well as looked into the factors behind this growth. In addition, we looked to evaluate how this growth would affect carbon emissions in the near future.

To predict the growth of electronic bikes, we evaluated 7 factors: Disposable Income, Commute Time, Gas Prices, Environmental Worry(Measured % of Respondents from a Survey), Popularity, Efficiency of E-Bike Batteries, and Population. The popularity of E-Bikes was quantified by finding the average of running a sentiment analysis of tweets containing the term "E-Bikes," and Population was found using U.N. Population Estimates. Disposable Income, Environmental Worry, and Battery Efficiency were predicted using single-variate regressions, and Commute Time, Gas Price, and Popularity were found by fitting distributions. 

We then used a Monte Carlo Simulation to predict these distribution-modeled factors in the future. We then trained a multivariable linear regression using these factors to predict the growth of e-bikes in 2025 and 2028. In evaluating the factors behind this growth, we simply looked at the coefficients as well as ran a sensitivity analysis to figure out which variables had the largest impact on e-bike sales.

In order to predict the effect on carbon emissions, we trained a Random Forest Algorithm to predict the number of rides a given e-bike rider would take and found the distance 10,000 e-bike riders would bike in a year. We then found the effects on CO2 emissions and traffic congestion if those miles were traveled by car, as well as the effect on health for the e-bike riders.

This work was created as a submission for the 2023 Mathworks Math Modeling Challenge, where we were given 14 hours to analyze and produce a write-up of a data science problem. We received an Honorable Mention in Technical Computing, putting us in the top 3% of submissions.

## Quantifying the Last Shot: Introducing DAWG(August 2022 - January 2023)[[Write-up]]({% link /projects/DAWG.pdf %}){:target="_blank"}
This project was my first real foray into data science. In this work, I looked to quantify the strength of a player's ability to hit last-second, potentially game-changing shots in the NBA. To do this, I created two metrics, a metric measuring the difficulty of the shot, as well as a metric measuring the importance of each shot.

To measure the difficulty of the shot, I created an expected points metric(similar to soccer), which used a Random Forest to predict the odds of a shot attempt scoring and multiplied that prediction by the potential point value of that shot. To measure the importance of each shot, I looked into the reaction of Tweets regarding last shots with the potential to change the outcome of a game, running a sentiment analysis on every tweet relating to the shot or the player within 24 hours of the shot. The importance of the shot was then measured by how polarizing a shot was and was combined with the difference between the actual points and the expected points(from the Random Forest algorithm) to find a per-shot value.

For each player, their per-shot values were combined to create a metric called DAWG(Daggers Adequately Winning Game), which quantified a player's ability to hit last-second, high-importance shots with the potential to change the outcome of a game. 

This project was a result of a semester-long independent study during my senior year at Memphis University School. It was mostly created for fun, with the DAWG name being a reference to the "Got That Dog in Him" meme, but this project was given financial backing by my high school, Memphis University School, and I was able to give a [presentation](https://www.musowls.org/news-detail?pk=1414630#){:target="_blank"} on my findings in front of the entire student body.

