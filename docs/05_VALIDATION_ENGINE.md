# PROJECT BATTLE

# Validation Engine

Version: 1.0.0

Status: Draft

Owner: David

Codename: Project Battle

---

# 1. Purpose

The Validation Engine is the first component that processes all user input.

Its purpose is to ensure that only valid, consistent, and trustworthy data enters the system.

The Validation Engine MUST execute before any data is persisted.

---

# 2. Responsibilities

The Validation Engine MUST:

- Validate user input.
- Reject invalid data.
- Normalize valid data.
- Return clear validation errors.
- Never modify historical records automatically.

The Validation Engine MUST NOT:

- Perform calculations.
- Generate intelligence.
- Call AI services.
- Access the UI.

---

# 3. Validation Pipeline

Every request follows this sequence.

User Input

↓

Schema Validation

↓

Business Rule Validation

↓

Normalization

↓

Accepted

↓

Repository


# 4. Validation Rules

## UserProfile

- displayName MUST NOT be empty.
- dateOfBirth MUST be a valid past date.
- heightCm MUST be greater than 0.

---

## Mission

- targetWeightKg MUST be greater than 0.
- targetWeightKg MUST be less than the initial weight.
- targetDate MUST be after the mission start date.
- Only one mission MAY have the status Active.

---

## WeightEntry

- weightKg MUST be greater than 0.
- Only one WeightEntry MAY be marked as isOfficial for a given day.

---

## NutritionEntry

- calories MUST be greater than or equal to 0.
- proteinGrams MUST be greater than or equal to 0.

---

## WaterEntry

- litres MUST be greater than or equal to 0.

---

## SleepEntry

- hours MUST be greater than or equal to 0.
- hours SHOULD be less than or equal to 24.

---

## ActivityEntry

- steps MUST be greater than or equal to 0.
- distanceKm MUST be greater than or equal to 0.
- activeCalories MUST be greater than or equal to 0.
- walkingMinutes MUST be greater than or equal to 0.

