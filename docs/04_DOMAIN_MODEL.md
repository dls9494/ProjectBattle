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


# 4. Entity Relationships

UserProfile

↓

creates

↓

Mission

↓

contains

↓

DailyRecord

↓

references

├── WeightEntry
├── NutritionEntry
├── WaterEntry
├── SleepEntry
└── ActivityEntry

Mission

↓

produces

↓

MissionSnapshot

MissionSnapshot

↓

feeds

↓

Intelligence Service

↓

feeds

↓

Explanation Service


# 5. Domain Invariants

The following rules MUST always be true.

## UserProfile

- Exactly one UserProfile exists.

---

## Mission

- At most one Mission MAY have the status Active.
- Archived missions are immutable.
- Completed missions cannot return to Active.

---

## DailyRecord

- At most one DailyRecord exists per calendar day per mission.

---

## WeightEntry

- At most one WeightEntry per day MAY be marked as isOfficial.

---

## MissionSnapshot

- MissionSnapshot is immutable.
- MissionSnapshot is never persisted.
- MissionSnapshot is regenerated whenever dependent data changes.

---

## General

- Raw facts are never overwritten.
- Derived values are never stored as permanent data.
- Historical records are never physically deleted.

