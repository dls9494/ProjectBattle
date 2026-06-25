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


# 5. Body Metrics

## BMI

Formula:

BMI = Weight (kg) / (Height (m) × Height (m))

Height is fixed in Version 1.

Weight is taken from the latest official WeightEntry.

---

## BMR

Formula:

Mifflin-St Jeor Equation (Male)

BMR = (10 × Weight) + (6.25 × Height(cm)) - (5 × Age) + 5

Age and Height are obtained from the user profile.

---

## Maintenance Calories

Version 1 uses:

Sedentary Activity Multiplier = 1.2

Maintenance Calories = BMR × 1.2

Future versions MAY support additional activity multipliers.


# 6. Daily Metrics

## Daily Intake

Daily Intake = NutritionEntry.calories

---

## Exercise Calories

Exercise Calories = ActivityEntry.activeCalories

If no ActivityEntry exists:

Exercise Calories = 0

---

## Daily Deficit

Daily Deficit =

(Maintenance Calories + Exercise Calories) - Daily Intake

---

## Protein

Protein = NutritionEntry.proteinGrams

---

## Water

Water = WaterEntry.litres

---

## Sleep

Sleep = SleepEntry.hours

Rules:

- Negative values are invalid.
- Missing values are treated as Unknown, not zero.
- Unknown values reduce the Data Reliability Score.


# 7. Mission Metrics

## Total Deficit

Total Deficit = Sum(Daily Deficit)

---

## Remaining Weight

Remaining Weight =

Current Weight - Target Weight

---

## Remaining Calories

Remaining Calories =

Remaining Weight × 7700

Note:

7700 kcal/kg is an estimation and MUST be configurable in future versions.

---

## Mission Progress

Mission Progress (%) =

((Start Weight - Current Weight) /
(Start Weight - Target Weight)) × 100

Clamp result between:

0% and 100%

