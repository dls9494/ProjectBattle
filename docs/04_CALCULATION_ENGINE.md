# PROJECT BATTLE

# Calculation Engine

Version: 1.0.0

Status: Draft

Owner: David

Codename: Project Battle

---

# 1. Purpose

The Calculation Engine is the mathematical core of Project Battle.

It transforms raw user data into deterministic metrics.

The Calculation Engine MUST:

- Be deterministic.
- Be explainable.
- Be testable.
- Be independent of Flutter.
- Be independent of AI.
- Produce identical outputs for identical inputs.

The Calculation Engine MUST NOT:

- Store data.
- Generate recommendations.
- Generate AI summaries.
- Access the UI.
- Access external services.

---

# 2. Inputs

The engine consumes only validated data.

Inputs include:

- Mission
- DailyRecord
- NutritionEntry
- WaterEntry
- SleepEntry
- ActivityEntry
- WeightEntry

---

# 3. Outputs

The engine produces:

- BMI
- BMR
- Maintenance Calories
- Daily Deficit
- Weekly Deficit
- Mission Progress
- Remaining Calories
- Remaining Weight
- Estimated Completion Date
- Confidence Score
- Data Reliability Score

No output produced by this engine is permanently stored.


# 4. Calculation Pipeline

Every calculation MUST execute in the following order.

1. Validate Input
2. Calculate Body Metrics
3. Calculate Daily Metrics
4. Calculate Mission Metrics
5. Calculate Confidence
6. Calculate Data Reliability

Each stage MUST complete successfully before the next stage begins.

If validation fails, the pipeline MUST terminate with an error.

