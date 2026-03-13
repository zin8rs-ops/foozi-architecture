# Foozi Data Strategy

This document defines how football data is stored, processed and generated across the Foozi platform.

The goal is to ensure the platform remains scalable, performant and capable of supporting prediction models and AI-generated insights.

---

# Data Categories

Foozi data is divided into three primary layers.

1. Stored Data
2. Computed Data
3. Generated Data

Each layer serves a different role in the platform architecture.

---

# 1 Stored Data

Stored data represents the core dataset of the platform.

These records are persisted in the database and act as the foundation for all calculations and predictions.

Examples

competitions  
teams  
players  
matches  
standings  
lineups  
match events  

Example Match Record

{
  "match_id": 12345,
  "competition": "bundesliga",
  "home_team": "bayern",
  "away_team": "dortmund",
  "date": "2026-03-20",
  "stadium": "Allianz Arena"
}

Sources

Football APIs  
data imports  
public datasets  

Stored data should remain normalized and structured.

---

# 2 Computed Data

Computed data consists of statistics derived from stored data.

These values are calculated through scheduled processing jobs.

Examples

team form  
goals per match  
xG averages  
home advantage metrics  
head-to-head statistics  

Example

Team Form

Last 5 matches

W W D W W

Computed data can be stored in aggregated tables or generated dynamically through queries.

Processing typically occurs through scheduled jobs such as nightly updates.

---

# 3 Generated Data

Generated data includes content created dynamically by AI systems.

Examples

AI insights  
match previews  
match reports  
player performance summaries  
competition summaries  

Example Insight

"Bayern scored in 9 consecutive home matches."

Generated data may optionally be cached but does not require permanent storage.

---

# Data Flow

The Foozi data pipeline follows this flow.

Stored Data
↓
Computed Statistics
↓
Prediction Engine (Tactra)
↓
AI Insight Engine
↓
Internal API
↓
Frontend Pages

This architecture ensures separation between raw data, calculated statistics and generated insights.

---

# Data Storage Principles

Key rules for the platform data layer.

Normalize core entities such as teams, players and matches.

Avoid storing derived statistics when they can be calculated efficiently.

Cache expensive computations where necessary.

Keep prediction inputs deterministic and traceable.

---

# Example Data Pipeline

Example match prediction pipeline.

Raw Match Data
↓
Team Form Calculation
↓
xG Trend Analysis
↓
Tactra Prediction Model
↓
AI Insight Generation
↓
Frontend Display

Example Output

"Bayern have a 64% win probability due to strong home form and higher xG metrics."

---

# Scalability Considerations

The platform must support a growing number of entities.

Estimated scale

50 competitions  
800 teams  
8000 players  
100000 matches  

The data strategy must support efficient querying and indexing for these entities.

---

# Platform Goal

The Foozi data layer should enable:

fast data access  
accurate predictions  
AI-driven insights  
scalable page generation
