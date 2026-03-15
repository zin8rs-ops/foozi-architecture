# Foozi AI Production Pipeline

This document describes how football data is transformed into predictions, insights and rendered pages.

The pipeline connects the data layer, prediction models, AI insight generation and frontend templates.

---

# Pipeline Overview

Football Data Sources
↓
Data Processing
↓
Prediction Engine
↓
AI Insight Engine
↓
Internal API
↓
Page Templates
↓
Rendered Pages

---

# 1 Football Data Sources

Raw football data is collected from external providers.

Examples

matches  
teams  
players  
statistics  

Sources may include football APIs and statistical datasets.

---

# 2 Data Processing

The data processing layer prepares raw data for analysis.

Tasks

data cleaning  
statistical aggregation  
feature generation  

Examples

team form  
expected goals trends  
goal averages  

These features are used by the prediction engine.

---

# 3 Prediction Engine

The Tactra engine calculates match outcome probabilities.

Example

Bayern vs Dortmund

Home Win — 64%  
Draw — 21%  
Away Win — 15%

Predictions are stored and exposed through the internal API.

---

# 4 AI Insight Engine

The insight engine converts statistical signals into natural language insights.

Example

"Bayern scored in 9 consecutive home matches."

Insights are generated for

matches  
teams  
players  
competitions  

---

# 5 Internal API

The internal API provides structured data to the frontend.

Example endpoints

/api/match/{id}

/api/team/{id}

/api/player/{id}

/api/competition/{id}

Responses include

statistics  
predictions  
insights  

---

# 6 Page Templates

Frontend templates consume the API data.

Examples

homepage template  
competition template  
match template  
team template  
player template  

Templates define layout structure.

---

# 7 Rendered Pages

Pages are rendered dynamically using template + data.

Examples

/match/bayern-vs-dortmund

/team/bayern-munich

/player/jamal-musiala

/bundesliga
