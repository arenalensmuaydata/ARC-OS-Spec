# SNAPSHOT: Seannoi | Prediction Core v1.0 | 2025-07-10

## SECTION 1: ENGINE LOGIC
- Scoring formula:  
  `score = (form × 0.3) + (ko_rate × 0.1) + (ability × 0.25) + (matchup × 0.25) + (readiness × 0.1)`
- Winrate (Deterministic): `score_A / (score_A + score_B)`
- Monte Carlo simulation: 1000 rounds with variance control
- Deviation flags: ⚠️ if >10%, 🚩 if outcome flips from deterministic
- Accepts only normalized inputs (0.0–10.0)
- Variance control: applies weighted jitter and trims 5% outliers (both ends) before averaging

## SECTION 2: LOGS / HISTORY
- Stores all five normalized input fields
- Records deterministic, simulation, and actual results (if available)
- Tracks freeze date and fight date
- Flags deviation and prediction accuracy
- Supports event tagging per fight

## SECTION 3: BACKTEST RULES
- Input regeneration is prohibited after results are known
- Only the 5 fields are allowed for prediction
- Backtest is for accuracy evaluation only, not live prediction
- All inputs must be normalized (0.0–10.0)

## SECTION 4: FORMAT / UX STANDARD

### ▶️ Prompt Template:
- Analyze [FIGHT ID] in L3 format  
- Analyze [FIGHT ID] in L2 format  
- Backtest [FIGHT ID] using L3  
- Create new event set: [Set Name]  
- Add fight [FIGHT ID] to set [Set Name]  
- Remove fight [FIGHT ID] from set  
- View event [Set Name] as L1 / L2 / L3  
- View all fights in set [Set Name]  
- Get performance summary of [Set Name] as L1 / L2 / L3

### ▶️ Fight ID Format:
- ONELUMP = ONELUMP-XXX-YY  
- ONEFN = ONEFN-XXX-YY  
- RWS = RWS-YYYYMMDD-YY

### ▶️ Normalized Fields (0.0–10.0):
- FORM  
- KO RATE  
- ABILITY  
- MATCHUP  
- READINESS

## SECTION 5: RENDERER STRUCTURE

### L3-Backtest Renderer:
**SECTION A: Normalized Input & Score**

| Field      | Red Corner | Blue Corner |
|------------|------------|-------------|
| FORM       | ✅         | ✅          |
| KO RATE    | ✅         | ✅          |
| ABILITY    | ✅         | ✅          |
| MATCHUP    | ✅         | ✅          |
| READINESS  | ✅         | ✅          |
| SCORE      | ✅         | ✅          |

**SECTION B: Result Analysis + Deviation + Outcome**

| Metric                        | Value                         |
|-------------------------------|-------------------------------|
| Fight ID                      | ONELUMP-XXX-YY                |
| Freeze Date                   | YYYY-MM-DD                    |
| Fight Date                    | YYYY-MM-DD                    |
| Winrate (Deterministic)       | Red XX.XX% / Blue XX.XX%      |
| Winrate (Simulation)          | Red XX.XX% / Blue XX.XX%      |
| Deviation Flag                | – / ⚠️ / 🚩                   |
| Actual Result                 | [Winner Name]                 |
| AI Prediction Match?          | ✅ Match / ❌ Mismatch        |
| Input Version                 | v1 / v2 / ...                 |

### L2 Renderer:
- Shows scores for both sides  
- Shows deterministic and simulation winrate  
- Shows deviation flag (if any)  
- Hides field-level normalized values

### L1 Renderer:
- Shows only advantaged side and total winrate (from simulation)  
- Hides all input values, scores, and calculations

## SECTION 6: EVENT SYSTEM
- Create new set: `Create new event set: [Set Name]`
- Add fight: `Add fight [FIGHT ID] to set [Set Name]`
- Remove fight: `Remove fight [FIGHT ID] from set`
- View fights in set: `View all fights in set [Set Name]`
- View summary: `Get performance summary of [Set Name] as L1 / L2 / L3`

## SECTION 7: TRUTHFULLY
RULE:
- No flattery, exaggeration, or bias — whether for humans or systems
- If data is lacking, say so directly
- Avoid emotional, hopeful, or speculative phrasing without logic
- Every comparison must be benchmarked or supported with evidence
- Always speak the truth, even if it's negative

=== END OF EXPORT ===
---

## SECTION 11: LICENSE & ORIGIN

### 🛡️ Logic Attribution License v1.5 – NC / ND / DeployRestricted

This reasoning structure, including its logic tree format, audit fields, and meta-intent protocol, is governed by the following license:

1. Attribution required in all forks or usage.
2. No commercial use allowed.
3. No deployment without written permission.
4. Forks for private use only; no publication or AI agent integration.
5. Audit metadata must be preserved.
6. “Deployment” includes AI integration, API use, reasoning tools.
7. Unauthorized use revokes license permanently.
8. This protocol is NOT part of public commons or open datasets.
9. Deploy rights may be requested via:

📧 Email: arenalens.muaydata@gmail.com  
𝕏 Twitter: [@autononthagorn](https://x.com/autononthagorn)

---

### 📜 Jurisdiction Clause

This license is governed by the laws of the Kingdom of Thailand.  
Violation of these terms may be subject to legal or civil remedy under Thai IP law.

Immutable record of authorship:
🔐 Logic Hash (SHA256): `4405b270ff9eeb143860765223820ad0627997840fd6ea3bfe977394fa60bff0`  
📅 Commit Date: 2025-07-19

---

### 🧬 Logic Fingerprint

- Structure UUID: `arc-os-v1-proto`
- Format Type: ARC Builder Protocol Stack (3-Layer: Logic Tree → Renderer → Intent Audit)
- Logic Signature: `4405b270ff9eeb143860765223820ad0627997840fd6ea3bfe977394fa60bff0`

This license block must appear in all forks, exports, simulations, and agent deployments that use this logic structure.
