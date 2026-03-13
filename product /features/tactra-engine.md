# Tactra Prediction Engine

The Tactra engine generates match outcome probabilities.

The goal is to provide an intelligent prediction model for football matches.

---

# Prediction Output

For each match the engine produces:

Home Win Probability  
Draw Probability  
Away Win Probability  

Example

Bayern vs Dortmund

Home Win — 64%  
Draw — 21%  
Away Win — 15%

---

# Input Signals

The prediction model uses several signals.

## Team Form

Recent match performance.

Example

Last 5 matches

W-W-D-W-W

---

## Expected Goals (xG)

Offensive and defensive strength.

Metrics

- xG per match
- xG conceded

---

## Home Advantage

Teams perform differently at home vs away.

Example

Bayern home win rate 72%.

---

## Squad Strength

Player availability and squad value.

Signals

- market value
- key player availability
- injuries

---

## Head-to-Head

Historical results between the two teams.

Example

Last 5 matches

Bayern wins: 3  
Draws: 1  
Dortmund wins: 1

---

# Prediction Model

The prediction score combines all signals.

Example formula

Prediction Score =
Form Score  
+ xG Strength  
+ Home Advantage  
+ Squad Strength  
+ Head-to-Head

Output is normalized to probabilities.

---

# Usage Across Platform

Predictions appear on:

Homepage  
Match Cards  
Match Pages  
Competition Pages

---

# UX Presentation

Predictions should always be displayed visually.

Options

- probability bars
- percentage indicators
- prediction badges
