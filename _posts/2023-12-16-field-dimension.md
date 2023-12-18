---
title: "How Does the difference in Field Dimension affect the directness of a soccer team?"
date: 2023-12-16
layout: post
---
### Introduction

Unlike other professional sports like the NFL or the NBA, soccer fields can come in a multitude of sizes. In the English Premier League, the highest level of soccer in England, the length of a field must fall between 90 to 120 meters and the width must fall between 45 to 90 meters. While most Premier League teams use the standard field size of 105 meters to 68 meters, this flexibility in the rules has allowed a handful of Premier League stadiums, like Everton’s Goodison Park and Chelsea’s Stamford Bridge to be of slightly different sizes to their Premier League counterparts.

To some, this flexibility has been a key difference in the playstyle and success of teams in game. In reaction to Tottenham Hotspurs’ poor home form, then manager Mauricio Pochettino noted that “Our style means we need a bigger place to play because we play a positional game and it’s true that White Hart Lane is a little bit tight. It’s better for the opponent. For example, on Sunday Newcastle play deep, same with West Brom and Liverpool, and it was difficult for us. We need time to adapt in our new set up and understand better our position on the pitch.” While it is true that White Hart Lane was one of the smallest fields in the Premier League that year, coming in at 100 meters by 67 meters, compared to the standard Premier League size of 105 meters by 68 meters, do those extra meters make a huge difference in the playstyle of the team or is Pochettino just looking for an excuse? Do teams look to play more direct, with longer and more straightforward passes, on shorter fields and play more indirect, with shorter passes, on longer fields? Is there any difference at all?

### Methodology
To find out, we look to compare the average passing distance of manager’s teams in fields that are longer, shorter, wider, and narrower to the average passing distance of the team’s home field. Because of the heavy turnover of managers in professional soccer and the fact that the playstyle of a team is usually dictated heavily by the manager, it makes more sense to represent managers instead of teams as their style of play will remain constant while teams, who may go through multiple managers, might have varying styles of play throughout the season.

Using a play-by-play dataset describing the 2017-2018 Premier League Season, we can use Python and the library Pandas to find every single pass, successful or unsuccessful, made during the 17-18 season:

![AllPasses]({{site.url}}/assets/FieldPitchAnalysis/FieldPitchdf1.png)

Through the team’s ID numbers as well as the date of the game, we can find the manager at the time as well as the size of the team’s home stadium for both team making the pass as well as the opposing team. 

Since the x and y coordinates of both the originating and destination of the pass are considered in terms of percentage from the goal, we can use the size of the home stadium to find the true distance traveled for each pass. 

![Coords](assets/FieldPitchAnalysis/FieldPitchdf2.png)


We then find the average passing distance for both teams for each game, using the game_id parameter:

![AvgPass](/assets/FieldPitchAnalysis/FieldPitchdf3.png)

By filtering for home games and away games at fields of different sizes as the team’s home field, we can use the groupby pandas function to find the average passing distance for each manager under the conditions that we need.

![PerCoach](/assets/FieldPitchAnalysis/FieldPitchdf4.png)

### Results
*i. Longer Field*
![LongerField](/assets/FieldPitchAnalysis/Longerfield.png)

Mean Change: +1.064 meters

Based on the graph, it is quite clear that the change in directness / indirectness is heavily dependent on the manager. For some managers, like Jose Mourinho and Frank de Boer, their teams play substantially more direct, with the average passing distance being upwards of ten meters more than their passing distance at home. However, for managers like Alan Pardew and Rafael Benitez, their teams play more indirect, with their average passing distance dropping around 5 meters compared to at home. 

However, since there is only one field that is longer than the standard Premier League pitch size(Stamford Bridge), there are a multitude of potential confounding variables which may affect how direct a team would play, so it would be unrealistic to draw any real conclusions based on these observations; the sample size simply is not large enough. 

The only teams who have played a substantial portion of their season on longer fields are Ronald Koeman’s Everton, Jurgen Klopp’s Liverpool, and Frank de Boer’s Crystal Palace, where Koeman and Klopp’s teams have very little change while de Boer’s teams play more direct, so it is more than likely that teams either do not change how direct they play or begin to play much more direct, as there is more space to play into.

*ii. Shorter Field*
![ShorterField](/assets/FieldPitchAnalysis/Shorterfield.png)

Mean: -1.845 meters

Since there are more stadiums that are shorter than the standard Premier League field, there is a much larger sample size for teams playing on shorter fields, so it is more reasonable to draw conclusions based on field size. Overall, teams tend to play much less direct than they normally would at home, with average passing distance dropping by 1.8 meters compared to home form. 

This difference follows since there is less space to play into, meaning that it would not make sense to play a long, direct style of soccer. However, there are some notable exceptions, like Pep Guardiola’s Manchester City and Marco Silva’s Watford, whose average passing distance rises when playing on shorter fields. This exception is seen especially heavily in Slaven Bilic’s teams, where the average passing distance rises over 10 meters compared to home form. The exact reason for this difference is a mystery, but it may be a stylistic change for those games.

*iii. Wider Field*
![WiderField](/assets/FieldPitchAnalysis/Widerfield.png)

Mean: +0.160 meters

Like the longer fields, there are very few fields in the Premier League that are longer than the standard width(Huddersfield Town’s Kirklee’s Stadium and Chelsea’s Stamford Bridge), so the sample size for these games is smaller, meaning that other confounding variables and general randomness have a higher effect on the results. 

Based on the current data, it is more than likely that a wider field has negligible effect on the directness / indirectness of a teams playstyle, exemplified by the fact that there seems to be no pattern to how width would affect passing distance and by the relatively small mean of 0.16 meters. 

*iv. Narrower Fields*

![NarrowerField](/assets/FieldPitchAnalysis/Narrowerfield.png)

Mean: -0.937 meters

Because there are only two fields that are wider than the standard Premier League size, there would only be two teams / managers which would play on narrower fields, so it is unlikely that any real conclusions can be drawn from these numbers, as this section was only computed for the sake of completeness and general curiosity.

*v. Same Field Dimensions*

![SameField](/assets/FieldPitchAnalysis/Samefield.png)

Mean: +0.216 meters

To ensure that playing away was not the driving factor between the changes in distances, we look at the passing distance for teams when playing at stadiums of the same field pitch size as their home stadium. While there are notable differences in passing sizes, those differences do not fully account for all of the change when looking at fields of different sizes, with the mean when playing away on the same dimensions of 0.218 meters being much smaller than the means while playing on longer and shorter fields of 1.06 and -1.82 meters respectively. 

*Discussion*

Through our analysis of passing distance, it was found field length, especially when playing on shorter fields, had a notable effect on the directness and indirectness of a teams playing style, where teams playing on longer fields were more likely to play more direct passes while teams playing on shorter fields were more likely to play shorter, more indirect passes. This effect follows since teams playing on longer fields have more space to play longer, more direct passes, while teams playing on shorter fields have less space, leading to shorter, more indirect passes. 

For width, it was unreasonable to draw real conclusions because of the small number of Premier League stadiums that are different widths from the standard Premier League width of 68 meters, however it is more than likely that the width has had a negligible effect on directness of play.

One of the limiting factors is the small sample size. Since only 2017-2018 Premier League play by play data was available, there were less passes and less games where teams were playing in fields of different sizes than their home field, so confounding variables and general randomness could have had a real effect on the passing distance. For future works, it may be sensible to use a large set of seasons, where, because of relegation and promotion, there will be more teams and more stadiums of differing field length, so the sample size would increase.

In addition, it is possible that these changes in directness could have been unrelated to field size. For example, a weaker team playing a traditionally stronger team may change their tactics to play a more direct style of soccer, relying on strength and speed instead of technical ability to win, so this change in passing distance would be based on the strengths of the opposition and a manager’s gameplan, as opposed to adapting to field size. 

To combat this, we first thought to look at reverse fixtures and finding differences in passing distance. However, the generally high turnover rates of high level professional soccer(with 20 changes of managers, including caretaker managers, occuring during the 2017-2018), it is more than likely that a team would have a different manager and therefore a different playing style when compared to the initial fixture and the reverse fixture. It may be valuable to look into how playing stronger or weaker teams can affect the directness of a team in the future.

