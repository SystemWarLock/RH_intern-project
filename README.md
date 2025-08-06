# RH_intern-project
# Sales Share CLI (Persistent Version)

## Overview
A Python 3 command-line application for allocating sales incentives among agents, with:
- Persistent storage in JSON
- Flexible scoring based on multiple weighted factors
- Configurable per-agent min/max payout thresholds
- Base allocation per agent before variable distribution
- Iterative clamping and redistribution to respect limits
- Distribution history tracking
- Option to delete agents

---

## Features Implemented
### 1. **Persistent Data**
- Saves and loads all agents, weights, and config from `agents_data.json`.
- Keeps distribution history in `distribution_history.json`.

### 2. **Agent Attributes**
Each agent has:
- **Performance score** (0–100)
- **Seniority** (months)
- **Target achieved points** (0–100)
- **Active clients**
- **Minimum guaranteed amount** (absolute currency)
- **Maximum cap amount** (absolute currency, optional)

### 3. **Scoring**
- Weighted formula:
  - Performance
  - Target
  - Seniority (scaled)
  - Clients (points, capped)
- Normalized weights to ensure fair proportional distribution.

### 4. **Base Allocation**
- Fixed base amount per agent.
- Automatically scaled down if total funds are less than required for base allocation.

### 5. **Variable Allocation**
- Remaining amount after base allocation distributed proportionally to agent scores.
- **Iterative clamping** to ensure per-agent min/max limits are respected.

### 6. **Min/Max Thresholds**
- Per-agent minimum payout guarantee.
- Per-agent maximum payout cap.

### 7. **Editing Agents**
- Modify all agent attributes.
- Modify only min/max thresholds.

### 8. **Deleting Agents**
- Remove an agent by ID with confirmation.

### 9. **Weights & Scaling**
- Change scoring weights.
- Configure seniority scaling method (fixed months or max among agents).

### 10. **History**
- Every distribution saved with timestamp, total amount, and detailed breakdown.

---

## Installation
```bash
pip install rich tabulate
python sales_share_cli_persistent.py
