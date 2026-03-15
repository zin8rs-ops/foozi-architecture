# Foozi Tech Stack

This document defines the technology stack used to build the Foozi platform.

The stack must support a scalable football data platform with predictions, AI insights and SEO optimized pages.

---

# Architecture Overview

The Foozi platform consists of several layers.

Frontend  
Backend API  
Database  
Prediction Engine  
AI Insight Engine  
Infrastructure  

---

# Frontend

The frontend renders all pages of the platform.

Responsibilities

- page rendering
- UI components
- client navigation
- data display

Recommended stack

Next.js  
React  
TypeScript  

Benefits

SEO friendly  
fast development  
large ecosystem  

---

# Backend API

The backend API provides structured football data to the frontend.

Responsibilities

- match data
- team data
- player data
- statistics
- predictions
- insights

Recommended stack

Node.js  
Express or Fastify  

Alternative

Python (FastAPI)

---

# Database

The database stores structured football data.

Core entities

competitions  
teams  
players  
matches  
standings  
statistics  

Recommended database

PostgreSQL

Benefits

strong relational model  
excellent query performance  

---

# Prediction Engine

The prediction engine calculates match outcome probabilities.

Example

Home Win — 64%  
Draw — 21%  
Away Win — 15%

Recommended stack

Python

Libraries

pandas  
numpy  
scikit-learn  

---

# AI Insight Engine

The AI Insight Engine generates natural language insights from football data.

Example

"Bayern scored in 9 consecutive home matches."

Recommended stack

Python  
LLM APIs

Possible providers

OpenAI  
Anthropic  

---

# Data Processing

Data pipelines process football statistics.

Responsibilities

data ingestion  
statistical aggregation  
prediction features  

Recommended tools

Python  
Airflow or scheduled jobs  

---

# Infrastructure

The platform should be deployed on scalable cloud infrastructure.

Recommended providers

Vercel (frontend)  
AWS or Google Cloud  

Key services

compute  
database hosting  
storage  
background jobs  

---

# Platform Goals

The Foozi tech stack should support

scalable football data processing  
AI-powered insights  
SEO optimized pages  
fast frontend performance
