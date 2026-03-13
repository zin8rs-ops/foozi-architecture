# Prediction & Insight Data Pipeline

This document describes how football data flows through the Foozi platform.

The pipeline transforms raw match data into predictions and insights used across the platform.

---

# Data Pipeline Overview

External Data Sources
↓
Data Processing Layer
↓
Prediction Engine (Tactra)
↓
AI Insight Engine
↓
Internal API
↓
Frontend Pages

---

# 1 External Data Sources

Raw football data is collected from:

Football APIs  
Statistical datasets  
Scraped public data  

Data includes:

- matches
- teams
- players
- standings
- statistics
- injuries

---

# 2 Data Processing Layer

The processing layer prepares raw data.

Tasks include:

data cleaning  
statistical aggregation  
feature calculation  

Example features

recent form  
xG averages  
home advantage  
player availability

---

# 3 Tactra Prediction Engine

The Tactra engine calculates match outcome probabilities.

Input

processed match features

Output

Home Win Probability  
Draw Probability  
Away Win Probability  

Example

Bayern vs Dortmund

Home Win — 64%  
Draw — 21%  
Away Win — 15%

---

# 4 AI Insight Engine

The insight engine converts statistics into natural language insights.

Example

"Bayern scored in 9 consecutive home matches."

"Dortmund conceded in 7 of the last 8 away matches."

Insights are generated for:

matches  
teams  
players  
competitions

---

# 5 Internal API

The internal API provides structured data to the frontend.

Examples

/api/match/{id}

/api/competition/{id}

/api/team/{id}

/api/player/{id}

---

# 6 Frontend Pages

Predictions and insights appear on:

homepage  
competition pages  
match pages  
team pages  
player pages
