# Bittensor Miner Alarm Bot

Monitor Bittensor subnets, compare mining opportunities, and get alerts when conditions change.

![Bittensor Miner Alarm Bot](https://github.com/jerryroyal/BittensorMinerAlarm/screenshot.png)

## Demo

**[▶ Watch demo video (miner.mp4)](https://github.com/jerryroyal/BittensorMinerAlarm/miner.mp4)** — click to play the walkthrough on GitHub.

---

## Getting started

1. Open **Miner.exe**.
2. Wait a few seconds — the app loads data automatically.
3. Check the sidebar: **Connection** should say `Connected` and **TAO** shows the current price.
4. Click **Refresh from Server** anytime to reload.

If you cannot connect, click **Server URL** in the sidebar and confirm the server address with your provider.

---

## Top bar — quick numbers

| Label | What it means |
|-------|----------------|
| **Subnets Monitored** | How many subnets are in the current report |
| **Active Alerts** | Total alerts right now (info + warning + critical) |
| **Agents Run** | How many analysis modules finished (usually 9) |
| **Top Pick** | The highest-ranked subnet at the moment (e.g. SN51 Name) |

---

## Sidebar

| Section | What it means |
|---------|----------------|
| **Connection** | Whether the app can reach the data server |
| **TAO** | Live TAO price in USD and where it came from |
| **Refresh from Server** | Download the latest rankings, alerts, and ROI data |
| **Server URL** | Change the server address (the only setting you need on this app) |

---

## Pages (tabs)

### Overview

Your home screen — best place to start.

- **Top Recommendations** — The 5 best subnets right now. Each card shows:
  - **Attractiveness Score** (0–100) — higher is better overall
  - **Why ranked here** — plain reasons (good rewards, low competition, etc.)
  - **Confidence** — how much data backed this ranking
  - **What could invalidate** — things that might change the picture (high risk, subnet almost full)
  - **Component bars** — Reward, Competition, Burn, Risk, ROI (each 0–100; **higher is better**)

- **Latest Alerts** — The 8 most recent alerts. Color shows urgency:
  - Blue = **info** (FYI or opportunity)
  - Amber = **warning** (be careful)
  - Red = **critical** (urgent)

---

### Rankings

Full list of all monitored subnets, sorted by overall score.

| Column | Meaning |
|--------|---------|
| **Rank** | Position (1 = best opportunity) |
| **Subnet** | Subnet number (e.g. SN8) |
| **Name** | Subnet name |
| **Score** | **Attractiveness** — overall mining appeal (0–100) |
| **Confidence** | How reliable this score is |
| **Reward** | How good the emission trend looks (higher = improving) |
| **Competition** | How easy it is to compete (higher = less crowded / easier) |
| **Burn** | Registration cost attractiveness (higher = cheaper or falling burn) |
| **Risk** | Safety score (higher = **lower** risk — safer subnet) |
| **ROI** | Estimated profitability (higher = better expected return) |

**Tip:** A high **Score** is a good start, but always check **Risk** and **Competition** before registering.

---

### Alerts

All alerts in one place. Use the **Severity** dropdown to filter:

| Severity | Meaning |
|----------|---------|
| **info** | Useful news — opportunities, positive trends |
| **warning** | Caution — rising competition, falling rewards, fragile validators |
| **critical** | Urgent — sudden reward drops or serious risk |

Each alert shows the **agent** that raised it, the **subnet**, a **message**, **confidence**, and **signals** (the data that triggered it).

**Common alert examples:**
- Registration burn dropped sharply → might be a good time to register
- Emission trend falling → rewards may keep dropping
- Subnet almost full → hard to get a slot
- Very few validators → network may be unstable
- High monthly ROI and short payback → strong profit signal (still an estimate)

---

### Agents

Detailed reports from each analysis module. Most miners can skip this tab and use **Overview**, **Rankings**, and **Alerts** instead.

| Agent | What it checks |
|-------|----------------|
| **Subnet Radar** | Scans all subnets for burn drops, low miner counts, capital flowing in |
| **New Opportunity** | Early subnets with few miners; external activity signals |
| **Reward Prediction** | Whether emissions are trending up, down, or flat |
| **Registration Burn** | Current burn and short-term burn forecast |
| **Competition** | How full the subnet is and how hard it is to earn |
| **Validator Intelligence** | Validator count, stake concentration, yield spread |
| **Governance** | On-chain parameter changes (emission, registration rules, etc.) |
| **Risk** | Safety flags — closed registration, emission crashes, weak validators |
| **ROI** | Profit estimates (same data as the ROI Calculator tab) |

---

### ROI Calculator

Estimated earnings per subnet. **These are simplified estimates — not guarantees.**

Shown at the top: TAO price and *“equal reward split assumed”*.

| Column | Meaning |
|--------|---------|
| **Daily TAO** | Estimated TAO per day if rewards were split equally among all miners |
| **Daily USD** | Daily TAO converted to dollars |
| **Monthly Profit** | (Daily USD × 30) minus estimated running costs |
| **ROI %** | Monthly profit as a percentage of upfront cost (registration + ~1 month of costs) |
| **Payback Days** | How many days to earn back the registration fee |
| **Reg TAO** | Current registration cost in TAO |

**Assumptions built into ROI:**
- Every active miner earns an **equal share** of emissions (your real earnings depend on performance)
- **7,200 blocks per day**
- Default running cost of about **$5/day** for GPU/electricity (set on the server)
- Registration cost = current burn in TAO × TAO price

**What ROI does not include:** your actual miner rank, validator weights, staking, or hardware differences.

---

### Subnet Explorer

Raw subnet facts — no scoring. Use this to **double-check** Rankings and ROI.

| Column | Meaning |
|--------|---------|
| **Emission** | TAO emitted per block on this subnet |
| **Burn** | Cost to register (TAO) |
| **Miners** | Number of active miners |
| **Validators** | Number of active validators |
| **Net Flow 7d** | TAO moving into or out of the subnet over 7 days (positive = inflow) |
| **Registration** | **Open** = you can register · **Closed** = registration disabled |

---

## How the score is calculated

Each subnet gets an **Attractiveness Score** from 0 to 100. It blends five factors:

| Factor | Weight | What it measures |
|--------|--------|------------------|
| **Reward** | 25% | Are emissions trending up? |
| **Competition** | 20% | Is the subnet overcrowded or still room to compete? |
| **Burn** | 15% | Is registration cost reasonable or falling? |
| **Risk** | 15% | How safe/stable is the subnet? |
| **ROI** | 25% | Does the math look profitable? |

Higher **Score** = more attractive overall. The component columns in **Rankings** show *why* a subnet scored high or low.

**Confidence** starts around 45% and goes up when more data is available (reward trend, ROI, competition). It goes down if risk is high or the subnet is nearly full.

---

## How risk is calculated

**Risk** in Rankings is a **safety score** (higher = safer). Behind the scenes, the app adds up risk points — more points means more danger:

| Situation | Risk added |
|-----------|------------|
| Registration is **closed** | +25 points |
| Emissions dropped **~30% or more** quickly | +35 points (also a **critical** alert) |
| **3 or fewer validators** (with miners active) | +20 points (also a **warning** alert) |
| Strong **capital outflow** over 7 days | +15 points |

Raw risk is capped at 100. The **Risk column** in Rankings flips this: `Risk score ≈ 100 − raw risk`.

**Example:** Risk column shows **80** → relatively safe (about 20 raw risk). Risk column shows **40** → elevated risk — read the Alerts tab.

---

## How competition is calculated

**Competition** measures how hard it is to earn on a subnet. Higher **Competition column** = easier to compete.

Difficulty is built from:
- **Fill rate** — how full the subnet is (miners ÷ max capacity)
- **Turnover** — how fast miner count is changing
- **Validator ratio** — validators compared to miners

A **warning** alert appears when difficulty is very high (≥ 75/100). An **info** alert when difficulty is low (≤ 25/100) and emissions are active.

---

## How reward trend is calculated

The app compares recent emissions to slightly older emissions (roughly last 5 blocks vs the 5 before that).

- Trend **above +15%** → **info** alert (rewards improving)
- Trend **below −15%** → **warning** alert (rewards falling)
- Subnet **more than 85% full** → **warning** (hard to get in)

---

## Tips for miners

1. Start on **Overview**, then open **Rankings** to compare.
2. Always check **Risk** and **Registration** in Subnet Explorer before paying burn.
3. **ROI Calculator** assumes equal splits — your actual earnings depend on your miner performance.
4. Treat **critical** and **warning** alerts seriously; **info** alerts are opportunities to investigate.
5. Click **Refresh from Server** after a few minutes if data looks stale (server updates about every 5 minutes).

---

## Feedback & collaboration

If you need new features, bug fixes, or changes to how scores and alerts work, **please leave a comment** — share what you want improved, what’s confusing, or what’s missing. Your feedback helps decide what gets updated next.

---

## Donate

If this tool helps your mining decisions, you can support development:

```
5HQNJmjMgpxjy5cwyWTYgxZ64Yd9k7fHDgCLTVzScCqDne4H
```

Thank you for using Bittensor Miner Alarm Bot.
