# Design System Architecture

This document describes how the design system is structured.

The system follows a layered architecture.

---

## Layer 1 — Design Tokens

Tokens define the visual foundation.

Location:

/tokens

Examples:

- colors
- spacing
- typography
- radius
- shadow
- breakpoints

Tokens ensure visual consistency across the system.

---

## Layer 2 — Components

Components are reusable UI building blocks.

Location:

/components

Examples:

- button
- match-card
- player-row
- team-row
- group-table
- progress-bar

Components use design tokens for styling.

---

## Layer 3 — Patterns

Patterns describe reusable UI sections.

Location:

/patterns

Examples:

- match-list
- leaderboard
- stats-section
- video-carousel
- news-feed
- group-table-grid

Patterns combine multiple components.

---

## Layer 4 — Templates

Templates define complete page structures.

Location:

/templates

Examples:

- world-cup-page
- league-page
- matchday-page
- player-ranking-page

Templates combine patterns into full layouts.

---

## Layer 5 — AI Generation Rules

AI prompts describe how UI should be generated.

Location:

/ai-prompts

Examples:

- page-generation
- component-generation
- layout-generation

AI tools use these rules to generate pages.

---

## System Flow

Design tokens
↓
Components
↓
Patterns
↓
Templates
↓
Pages

---

## Goal

Create a scalable system that allows:

- fast UI development
- consistent design
- AI-assisted interface generation
