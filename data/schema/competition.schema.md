# Competition Data Schema

Defines the structure of a football competition page.

## Competition

name  
country  
season  
logo  

## Teams

list of teams participating in the competition

Fields

- team_id
- name
- logo
- country

## Matches

list of matches

Fields

- match_id
- home_team
- away_team
- score
- date
- stadium

## Standings

league table information

Fields

- position
- team
- matches_played
- goal_difference
- points

## Top Players

player rankings

Fields

- player_name
- team
- goals
- assists
- market_value

## Media

content related to competition

Fields

- highlights
- news
- analysis
