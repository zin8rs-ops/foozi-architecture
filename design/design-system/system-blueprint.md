# Foozi Design System Blueprint

This document describes the structure of the Foozi design system.

The system is organized in hierarchical layers to ensure consistency and scalability.

---

# Design System Layers

The Foozi design system consists of five layers.

Design Tokens  
Components  
Patterns  
Templates  
Pages  

Each layer builds upon the previous one.

---

# 1 Design Tokens

Design tokens define the visual foundation of the interface.

Examples

colors  
spacing  
typography  
radius  
shadows  

Tokens ensure visual consistency across the platform.

Example

primary color  
background color  
spacing scale  

Tokens should be reused across all components.

---

# 2 Components

Components are reusable UI elements.

Examples

match-card  
team-row  
player-card  
stat-card  
prediction-bar  
insight-card  

Components combine design tokens with layout structure.

Components should remain small and reusable.

---

# 3 Patterns

Patterns combine multiple components to form UI sections.

Examples

match-list  
leaderboard  
squad-list  
stats-section  
insight-section  

Patterns define layout logic but remain reusable across pages.

---

# 4 Templates

Templates define full page layouts.

Examples

homepage  
competition-page  
match-page  
team-page  
player-page  

Templates combine patterns to create page structures.

Templates define the overall hierarchy of content.

---

# 5 Pages

Pages represent real platform routes.

Examples

/bundesliga  
/team/bayern-munich  
/player/jamal-musiala  
/match/bayern-vs-dortmund  

Pages are generated using templates and populated with data from the API.

---

# System Flow

The design system follows a hierarchical flow.

Tokens  
↓  
Components  
↓  
Patterns  
↓  
Templates  
↓  
Pages  

This structure allows scalable UI development.

---

# Integration With Platform

The design system connects to the platform architecture.

API Data  
↓  
Templates  
↓  
Patterns  
↓  
Components  
↓  
Rendered UI

This ensures the frontend can dynamically generate pages based on structured data.

---

# Design System Goal

The Foozi design system should enable:

consistent UI  
fast development  
AI-assisted interface generation  
scalable football pages
