# PROJECT BATTLE

# Product Requirements Document (PRD)

Version: 1.0.0

Status: Draft

Owner: David

Codename: Project Battle

---

# 1. Executive Summary

Project Battle is a personal mission intelligence system designed to transform a small amount of daily health data into meaningful, evidence-backed intelligence.

Unlike traditional calorie trackers or fitness applications, Project Battle does not attempt to motivate, coach, or judge the user.

Instead, the application continuously observes, measures, analyzes, projects, and explains what the user's own historical data indicates.

The primary objective is to answer one question:

> **"Based on everything I have logged, what is actually happening, why is it happening, and what evidence supports that conclusion?"**

Project Battle is intentionally designed for a single user in Version 1.

Every design decision within the application must align with the Project Constitution.

---

# 2. Problem Statement

Existing fitness applications generally focus on one or more of the following:

- Calorie tracking
- Weight tracking
- Exercise tracking
- Motivation
- Streaks
- Achievements
- Social competition

While these applications collect significant amounts of data, very few help the user understand what that data actually means.

Project Battle addresses this gap by acting as an intelligence layer rather than simply a logging tool.

Instead of collecting more information, it converts existing information into understandable insights supported by evidence.

# 3. Product Goals

Project Battle exists to achieve the following goals.

## Primary Goals

* Transform a small amount of daily user input into meaningful intelligence.
* Help the user understand progress using evidence instead of opinions.
* Minimize daily logging effort while maximizing useful insights.
* Maintain complete transparency for every calculation and conclusion.
* Operate completely offline for Version 1.
* Preserve all historical data for long-term trend analysis.
* Support one active mission at a time.
* Generate deterministic calculations for all measurable metrics.
* Use AI only for explanation and interpretation, never as the source of truth.

## Success Criteria

The product is considered successful if:

* The user chooses to continue using it because it provides useful intelligence.
* Every insight can be traced back to supporting evidence.
* Daily logging requires less than two minutes.
* The application remains fast, simple, and reliable.
* The user understands trends instead of merely viewing numbers.

---

# 4. Non-Goals

The following are explicitly outside the scope of Version 1.

## Social Features

The application will not include:

* Friends
* Communities
* Leaderboards
* Sharing
* Public profiles

## Motivation Systems

The application will not include:

* Motivational quotes
* Achievement badges
* Artificial streak rewards
* Daily challenges
* Gamification unrelated to mission progress

## Cloud Features

Version 1 will not include:

* User accounts
* Cloud synchronization
* Multi-device synchronization
* Online backups

## Health Advice

Project Battle does not diagnose medical conditions or provide medical advice.

The application presents evidence-based observations from user-entered data only.

Final decisions always belong to the user.

---

# 5. Product Principles

Every feature added to Project Battle must satisfy the following principles.

* Reduce manual effort.
* Increase understanding.
* Preserve transparency.
* Be explainable.
* Be evidence-backed.
* Respect user privacy.
* Keep raw data as the source of truth.
* Never sacrifice simplicity for unnecessary functionality.

# 6. Target User

## Version 1

Project Battle is designed for a single user.

The system is intentionally optimized for one person's habits, preferences, and mission workflow.

Version 1 is not intended to support multiple users.

---

## User Characteristics

The application assumes:

* Sedentary lifestyle
* Walking as the primary exercise
* Weight updated manually
* Calories entered manually
* Protein entered manually
* Water entered manually
* Sleep entered manually
* Activity imported from Samsung Health screenshots

---

## User Profile

The following values are fixed in Version 1:

* Gender
* Height
* Age (editable if required)
* Activity level defaults to sedentary

Weight is the primary body measurement that changes over time.

All dependent calculations automatically update whenever weight changes.

---

# 7. Version 1 Scope

## Daily Inputs

The user records:

* Water (litres)
* Calories consumed
* Protein (grams)
* Sleep (hours)
* Samsung Health screenshot

---

## Weekly (or whenever desired)

The user records:

* Body weight

---

## Mission Inputs

The user defines:

* Mission name
* Target weight loss
* Target completion date

The mission may be:

* Active
* Paused
* Completed
* Archived

Only one mission may be active at any given time.

Changing mission targets immediately recalculates all projections.

---

## References

- 00_PROJECT_CONSTITUTION.md

# 8. Functional Requirements

## 8.1 Mission Management

The application shall support one active mission at any given time.

A mission represents a defined objective with measurable progress.

Each mission contains:

- Mission Name
- Mission Description (Optional)
- Target Weight Loss (kg)
- Target Completion Date
- Mission Status
- Mission Start Date
- Mission Completion Date (when completed)

Mission Status shall support:

- Active
- Paused
- Completed
- Archived

Only one mission may remain Active.

Changing the target date or target weight loss shall immediately recalculate:

- Remaining Calories
- Required Daily Deficit
- Estimated Completion Date
- Mission Pace
- Mission Confidence

No historical mission data shall be lost when a mission is edited.

---

## 8.2 Daily Logging

The application shall allow the user to record daily health data.

Daily inputs include:

- Water Intake (Litres)
- Calories Consumed
- Protein Intake (grams)
- Sleep Duration (hours)
- Samsung Health Screenshot

Each daily log shall be editable.

Editing a previous day's data shall automatically trigger recalculation of every affected metric.

---

## 8.3 Weekly Logging

Weight is intentionally separated from daily logging.

The application shall allow weight updates whenever the user chooses.

Weight updates automatically trigger recalculation of:

- BMI
- BMR
- Maintenance Calories
- Mission Projection
- Estimated Fat Loss
- Historical Weight Trend

The application shall never require daily weigh-ins.

---

## 8.4 Samsung Health Integration

Version 1 uses screenshot upload.

The application shall:

- Accept Samsung Health screenshots.
- Store screenshots locally.
- Prepare the architecture for future AI extraction.

The future extraction service shall identify:

- Steps
- Distance
- Walking Duration
- Walking Calories

The screenshot itself shall remain available for manual verification.

### Workflow

Upload Screenshot

↓

AI extracts values

↓

User reviews extracted values

↓

User taps Confirm

↓

Saved

### Engineering Note



AI extraction is an assistive feature.



The user remains the final authority over all imported data.



Every extracted value must be presented for review before being committed to local storage.



This ensures transparency, improves trust, and prevents incorrect AI extraction from polluting historical data.


## 8.5 Automatic Calculations

The application shall automatically calculate the following values.

### Body Metrics

- Body Mass Index (BMI)
- Basal Metabolic Rate (BMR)
- Maintenance Calories

---

### Daily Metrics

- Calories Consumed
- Calories Burned (Walking)
- Estimated Daily Deficit
- Protein Intake
- Water Intake
- Sleep Duration

---

### Mission Metrics

- Total Mission Deficit
- Remaining Calories
- Remaining Estimated Fat Loss
- Mission Progress Percentage
- Days Remaining
- Required Daily Deficit
- Projected Completion Date

---

### Intelligence Metrics

- Confidence Score
- Data Reliability Score
- Mission Pace
- Historical Trend Analysis

The user shall never manually enter any value that can be deterministically calculated.

---

## 8.6 Mission Dashboard

The home screen shall function as Mission Control.

When opened, the dashboard shall immediately answer the following questions.

1. What changed since yesterday?
2. What changed since my last weight update?
3. Where am I in my current mission?
4. What does my data say?
5. What evidence supports the conclusion?
6. How confident is the system?

The dashboard shall prioritize understanding over information density.

# 9. Intelligence System

## 9.1 Overview

The Intelligence System is the core differentiator of Project Battle.

Its purpose is not to motivate, coach, or judge.

Its purpose is to analyze user data and generate evidence-backed intelligence.

Every intelligence output shall be generated from structured data.

---

## 9.2 Intelligence Levels

Project Battle shall support four levels of intelligence.

### Instant Intelligence

Generated immediately after new data is entered.

Purpose:

Provide immediate feedback based on the latest information.

---

### Daily Intelligence

Generated from a single day's data.

Focus:

- Daily deficit
- Water
- Protein
- Sleep
- Walking
- Mission contribution

---

### Weekly Intelligence

Generated from historical trends.

Focus:

- Weight trend
- Walking trend
- Protein trend
- Water trend
- Sleep trend
- Mission pace

---

### Mission Intelligence

Generated from the complete mission history.

Focus:

- Overall mission performance
- Trend analysis
- Projection updates
- Pattern recognition
- Mission review

---

## 9.3 Intelligence Structure

Every intelligence report shall contain the following sections.

### Observation

Describe what the data shows.

---

### Why It Matters

Explain why the observation is relevant.

---

### Evidence

Present the supporting numerical evidence.

---

### Confidence

Indicate how reliable the conclusion is.

---

### Recommendation (Optional)

Suggest what would be required to achieve the selected mission target.

Recommendations must never be judgmental or prescriptive.

# 9. Intelligence System

## 9.1 Overview

The Intelligence System is the core differentiator of Project Battle.

Its purpose is not to motivate, coach, or judge.

Its purpose is to analyze user data and generate evidence-backed intelligence.

Every intelligence output shall be generated from structured data.

---

## 9.2 Intelligence Levels

Project Battle shall support four levels of intelligence.

### Instant Intelligence

Generated immediately after new data is entered.

Purpose:

Provide immediate feedback based on the latest information.

---

### Daily Intelligence

Generated from a single day's data.

Focus:

- Daily deficit
- Water
- Protein
- Sleep
- Walking
- Mission contribution

---

### Weekly Intelligence

Generated from historical trends.

Focus:

- Weight trend
- Walking trend
- Protein trend
- Water trend
- Sleep trend
- Mission pace

---

### Mission Intelligence

Generated from the complete mission history.

Focus:

- Overall mission performance
- Trend analysis
- Projection updates
- Pattern recognition
- Mission review

---

## 9.3 Intelligence Structure

Every intelligence report shall contain the following sections.

### Observation

Describe what the data shows.

---

### Why It Matters

Explain why the observation is relevant.

---

### Evidence

Present the supporting numerical evidence.

---

### Confidence

Indicate how reliable the conclusion is.

---

### Recommendation (Optional)

Suggest what would be required to achieve the selected mission target.

Recommendations must never be judgmental or prescriptive.

