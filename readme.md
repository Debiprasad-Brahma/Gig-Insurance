# Gig Insurance Platform

### Parametric Insurance for Gig Workers

---

## Problem Statement

Gig workers (delivery partners, drivers, etc.) lose income due to:

- Heavy rain 🌧️
- Heatwaves 🌡️
- Air pollution 🌫️

There is **no automatic compensation system**, and existing insurance is slow and claim-based.

---

## Solution

We propose a **Parametric Insurance Platform** where:

- Environmental data is monitored in real-time
- Predefined conditions trigger payouts automatically
- No claim process is required

### Example:

```
IF rainfall > 50mm OR temperature > 45°C OR AQI > 400
THEN payout is triggered
```

---

## System Overview

```
User → Select Policy → System Monitors Data →
Condition Met → Payout Triggered
```

---

## High-Level Architecture

```
Frontend (React)
      │
      ▼
Backend (Node.js / Express)
      │
      ├── Weather API
      ├── AQI API
      ├── Insurance Engine
      │
      ▼
Database (MongoDB)
```

---

## Adversarial Defense & Anti-Spoofing Strategy

### Problem: Market Crash Scenario

A fraud attack may involve:

- Fake user accounts
- GPS spoofing
- Mass payout triggering
- Coordinated fraud rings

Our system uses **multi-layer defense** to prevent this.

---

### 1. Multi-Source Location Verification

We do not rely only on GPS.

We validate using:

- GPS coordinates
- IP-based location
- Device identification

#### Detection:

- GPS ≠ IP → flagged
- Multiple accounts on same device → flagged
- Sudden location jumps → suspicious

---

### 2. Behavioral Analysis

We track user activity patterns.

#### Signals:

- Working hours
- Movement continuity
- Travel speed

#### Suspicious cases:

- Unrealistic speed
- Sudden activity spikes
- Identical patterns across users

---

### 3. Fraud Ring Detection

We detect coordinated attacks using pattern matching.

#### Indicators:

- Many users at same location
- Same time payout triggers
- Shared device/IP

#### Action:

- Group flagged
- Payouts paused

---

### 4. Risk Scoring System

Each user gets a **risk score (0–100)**.

| Score  | Action         |
| ------ | -------------- |
| 0–30   | Instant payout |
| 30–70  | Delayed payout |
| 70–100 | Blocked        |

---

### 5. Event Validation

Before payouts:

- Verify event using trusted APIs
- Ensure disruption is real and widespread

---

### 6. Payout Controls

- Limit payouts per user
- Cap payouts per event
- Add cooldown periods

---

### 7. Protecting Genuine Users

- No instant bans
- Use delayed verification
- Allow manual review

---

### Key Principle

We do not trust user input alone.

We rely on:

- Multi-source verification
- Behavioral patterns
- System-wide correlation

---

## Tech Stack

- Frontend: React.js
- Backend: Node.js, Express.js
- Database: MongoDB
- APIs: OpenWeather, AQI

---
