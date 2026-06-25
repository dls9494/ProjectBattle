# PROJECT BATTLE

# Domain Model

Version: 1.0.0

Status: Draft

Owner: David

---

# 1. Purpose

The Domain Model defines the business language of Project Battle.

It is independent of:

- Flutter
- Hive
- Riverpod
- AI
- UI

The Domain Model represents the problem space, not the implementation.

---

# 2. Core Principle

Project Battle models facts.

Everything else is derived.

Facts become Metrics.

Metrics become Intelligence.

Intelligence becomes Explanation.


# 3. Domain Entities

The following entities make up the Project Battle domain.

## Core Entities

- UserProfile
- Mission
- DailyRecord
- WeightEntry
- NutritionEntry
- WaterEntry
- SleepEntry
- ActivityEntry
- TimelineEvent
- Settings

## Generated Domain Models

The following models are generated at runtime and MUST NOT be persisted.

- MissionSnapshot

## Domain Services

The following services contain business logic.

- Validation Engine
- Metrics Engine
- Intelligence Engine
- Explanation Layer

