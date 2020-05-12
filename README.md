# Counter-Strike: Global Offensive ELO System

Counter-Strike: Global Offensive  is one of the largest global esports, with
professional tournaments held nearly every weekend. The goal of this project is 
to create a modified ELO system that predicts that outcomes of pro matches. 

The modifications made to our ELO system takes into consideration some extra
variables when calculating the probability of a team winning a match, such as
past performances on a give maps and typical margins of victory for a team.

# How a Counter-Strike game plays out

A Counter-Strike (or more familiarly, CS:GO) game is comprised of two teams of
five players each. There are up to thirty individual rounds, where the
terrorist team (or Ts) tries to plant a bomb, and the counter-terrorist team's goal is
to defuse the bomb if it's planted. If the terrorist team successfully detonates
the bomb, they win that round. If the counter-terrorist team (CT) defuses the bomb,
they win that round. If one of the teams eliminates the entire enemy team, they
win that round. Once fifteen rounds is played, the two teams switch sides. The
first team to win sixteen rounds wins that particular game, and in tournaments
the teams usually play a best of three games before advancing to the next round
(but this can vary depending on the tournament). There are seven different maps
that are available to play on, and typically the teams take turns deciding which
maps to play.

Picking maps is surprisingly a crucial factor to a team's success in tournament 
settings. Some teams absolutely dominate certain maps. For example, one of the 
world's arguably best teams, Astralis, had a 31 game win streak on the map Nuke.
Naturally, they would like to play this map as much as possible due to their 
extreme tactical prowess. 

Similarly, analyses have shown that some maps are more in favor of the CT, which 
is referred to as a map being CT-sided. When a team picks a map, the other team
gets to decide which side they would like to play first. If a map is CT sided, 
they might want to play CT first to gain an extra advantage.

# How we can use ELO?

The [ELO system](https://en.m.wikipedia.org/wiki/Elo_rating_system) was
originally developed as a ranking system to track professional chess players,
but has naturally been extended to other competitive environments since it's a
fairly straightforward system to implement. Initially, every player is assigned
an ELO rating of 1500. Once a match is over, a formula is run on the two
different ELO ratings, and the winning player takes points from the losing
player, making it a net-zero system. The larger the ELO difference between a
higher ranked player and a lower ranked player, the fewer points she'll gain
from her victory. However, if the lower ranked player upsets the higher player,
he'll gain a more substantial amount of points to his own rating. 

But this system can be modified to include additional information. One benefit
of this system is that you can use the two ELO ratings to directly calculate the 
probability of a victory using another really simple formula. There are tricks
you can use to incoporate this extra data though, and [538's NFL ELO system](https://fivethirtyeight.com/methodology/how-our-nfl-predictions-work/) 
is a phenomenal example of this, and is a large source of inspiration for this 
project. Essentially, we would like to incorporate the data about the map into
our calculations, and therefore strengthen our predictive power.