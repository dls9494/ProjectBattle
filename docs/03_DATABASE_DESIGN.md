# PROJECT BATTLE

# Database Design

Version: 1.0.0

Status: Draft

Owner: David

Codename: Project Battle

---

# 1. Philosophy

Project Battle stores facts.

Project Battle never stores intelligence.

Project Battle never stores conclusions.

Project Battle never stores recommendations.

Every report, projection, and insight MUST be reproducible from stored raw data.

---

# 2. Database Principles

The database MUST satisfy the following principles.

- Offline First
- Local First
- Immutable History
- Minimal Duplication
- Deterministic Reconstruction
- Versioned Schema
- Human Readable
- Future Migration Friendly

---

# 3. Database Technology

Version 1

Database

Hive CE

Reason

- Fast
- Offline
- Lightweight
- Excellent Flutter support
- No SQL required
- Easy export/import

Future migrations to SQLite or Isar MUST be possible without changing the Domain Layer.

