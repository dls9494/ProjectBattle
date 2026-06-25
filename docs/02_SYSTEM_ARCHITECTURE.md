# PROJECT BATTLE

# System Architecture

Version: 1.0.0

Status: Draft

Owner: David

Codename: Project Battle

---

# 1. Overview

Project Battle follows an Offline-First, Local-First architecture.

Every core feature must function without internet connectivity.

Artificial Intelligence is an optional enhancement layer and is never part of the application's core business logic.

The architecture is designed around one principle:

> Store Facts.
>
> Generate Intelligence.
>
> Never Store Intelligence.

---

# 2. Architectural Principles

Project Battle MUST satisfy the following principles.

- Offline First
- Local First
- Modular
- Testable
- Deterministic
- Explainable
- Maintainable
- AI Independent

The application MUST continue functioning if every AI service is removed.

---

# 3. High Level Architecture

                 Flutter UI
                     │
                     ▼
             Riverpod Providers
                     │
                     ▼
             Repository Layer
                     │
     ┌───────────────┼───────────────┐
     ▼               ▼               ▼
 Hive Database   Calculation Engine  AI Service
     │               │               │
     └───────────────┼───────────────┘
                     ▼
           Mission Intelligence Engine
                     │
                     ▼
               Dashboard UI


# 4. Layered Architecture

Project Battle follows a strict layered architecture.

Presentation Layer

↓

Application Layer

↓

Domain Layer

↓

Infrastructure Layer

↓

Local Storage

---

## 4.1 Presentation Layer

Responsibilities:

- UI
- Navigation
- User Interaction
- State Rendering

This layer MUST NOT perform calculations.

This layer MUST NOT contain business logic.

---

## 4.2 Application Layer

Responsibilities:

- Use Cases
- Riverpod Providers
- Coordination
- State Management

This layer orchestrates communication between UI and Domain.

---

## 4.3 Domain Layer

The Domain Layer is the heart of Project Battle.

Contains:

- Mission Engine
- Calculation Engine
- Intelligence Engine
- Validation Rules
- Projection Logic

This layer contains zero Flutter dependencies.

Everything inside this layer MUST be pure Dart.

---

## 4.4 Infrastructure Layer

Responsibilities:

- Hive
- Image Storage
- AI Connectors
- File System
- Import / Export

Infrastructure knows about the outside world.

The Domain Layer must never depend on Infrastructure.

---

## 4.5 Storage Layer

Version 1 stores:

- Missions
- Daily Logs
- Weight History
- Screenshots
- Settings

locally only.

No internet dependency exists.

