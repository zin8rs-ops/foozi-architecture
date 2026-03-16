# API Structure

This document describes the API structure for the football data platform.

The API provides structured football data for the design system and page templates.

---

# Core Endpoints

## Competitions

Returns competition information.

Endpoint

/api/competitions

Example

/api/competitions/bundesliga
/api/competitions/premier-league
/api/competitions/world-cup

Fields

- id
- name
- country
- season
- logo

---

## Teams

Returns team information.

Endpoint

/api/teams

Example

/api/teams/bayern-munich
/api/teams/manchester-city

Fields

- team_id
- name
- logo
- country
- stadium

---

## Matches

Returns match information.

Endpoint

/api/matches

Example

/api/matches/bundesliga
/api/matches/world-cup

Fields

- match_id
- home_team
- away_team
- score
- date
- stadium
- status

---

## Standings

Returns league tables.

Endpoint

/api/standings

Example

/api/standings/bundesliga
/api/standings/premier-league

Fields

- position
- team
- matches_played
- goal_difference
- points

---

## Players

Returns player data.

Endpoint

/api/players

Example

/api/players/top-scorers
/api/players/market-values

Fields

- player_id
- name
- team
- goals
- assists
- market_value

---

## Media

Returns videos and news.

Endpoint

/api/media

Example

/api/media/highlights
/api/media/news

Fields

- title
- type
- image
- video_url
- date
