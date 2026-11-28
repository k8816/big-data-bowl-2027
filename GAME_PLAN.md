# Big Data Bowl 2027 — Game Plan

**Goal:** Predict NFL pass-rusher success from Combine (and related) data.

**Players:** Defensive linemen, defensive tackles, and outside linebackers — everyone who rushes the passer.

**Rules / schema:** See `CompetitionDescription/`.

## Data scope / cohort

Given the available competition data, the cleanest cohort is:

- **Draft years:** 2022–2023 only.
- **Evaluation window:** each player’s **first two NFL seasons**.
- **Exclude:** 2024 draftees — they have only rookie-year outcomes, which is an unfair comparison against multi-year peers.

This keeps Combine predictors and early-career outcomes aligned without mixing incomplete career windows.

---

## Pillar 1 — Combine

- **Raw static measures:** 40-yard dash, broad jump, bench press, 10-yard split, 20-yard shuttle.
- **Custom tracking metrics:** Athleticism signals derived from D-line Combine drills (beyond the raw statics).

## Pillar 2 — In-game athleticism

- **Now:** Raw get-off — mean and standard deviation (from existing aggregate notebooks).
- **Later:** Model expected get-off, then measure pass-rush performance above expected get-off.

## Pillar 3 — In-game pass-rush impact

- **Now:** Pressures measured from in-game tracking.
- **Goal:** Impact metrics that go beyond pressures alone.

---

## Modeling strategy

1. **Direct:** Combine → impact.
2. **Indirect / mediated:** Combine → athleticism → impact.

---

## Big Tasks

Schedule note: **no work Dec 23–27.**

1. **Custom Combine drill metrics** — Due **Dec 4**. Build two tracking-based athleticism measures from D-line Combine drills (beyond raw statics).
2. **Expected get-off model** — Due **Dec 11**. Fit a sparse ML model of get-off from situation; flag rushes that are faster than expected.
3. **Impact beyond pressure** — Due **Dec 18**. Define two pass-rush impact metrics that go past pressure counts alone.
4. **Pathway regressions** — Due **Dec 30**. Regress Combine ↔ athleticism ↔ impact, using both static Combine measures and the custom drill metrics.
5. **One-play visualization** — Due **Jan 2**. Show metrics and model outputs on a single play for interpretability.
6. **Story notebook** — Due **Jan 4** (buffer before the **Jan 6** deadline). Deliver the submission narrative as a polished notebook that ties pillars, models, and results together.
