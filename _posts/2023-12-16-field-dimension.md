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

![AllPasses](/assets/FieldPitchaAnalysis/FieldPitchdf1.png)
