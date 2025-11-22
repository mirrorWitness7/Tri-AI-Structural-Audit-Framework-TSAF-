# TSAF Equations and Indices

These formulas are deliberately simple and approximate. They are meant as diagnostic tools, not precise science.

Let small ε = 1e-6 to avoid division by zero.

## 1. Recursion Score (R)
R is usually estimated qualitatively (from 1.0 to 7.0) based on behavior and claims.

Examples:
- R ≈ 1.5: Binary slogans, no serious engagement with data.
- R ≈ 3.0: Understands tradeoffs but ignores deeper externalities.
- R ≥ 6.0: Designs or audits multi-system architectures.

## 2. Structural Coherence (SC)

Let:
- E ∈ [0, 1] = evidence strength (cashflow, IP, resilience, etc.).
- C ∈ [0, 1] = claim ambition/complexity (how big/global/mission-heavy the story is).

SC = E / (C + ε)

Interpretation:
- SC ≈ 1: claims are well-backed.
- SC ≪ 1: claims greatly exceed evidence → hype zone.

## 3. Optics-to-Structure Ratio (OSR)

Let:
- O ∈ [0, 1] = optics score (media reach, followers, hype, perceived genius).
- S ∈ [0, 1] = structural score (quality of revenue, margins, moat, resilience).

OSR = O / (S + ε)

Interpretation:
- OSR ≈ 1: optics and structure aligned.
- OSR ≫ 1: hype far exceeds substance → fragile under audit.

## 4. Contradiction Stack (CS)

Let each contradiction C_i have a severity w_i ∈ [0, 1].

CS = Σ w_i

Examples:
- “Discipline” vs multi-year uncontrolled loss → high severity.
- “Helps users escape poverty” vs platform collapse risk → high severity.

We can normalize CS to [0, 1] as:
CS_norm = min(1.0, CS / K)
for some K (e.g., K = 4 or 5).

## 5. Macro Risk (MR)

MR captures how badly the model is exposed to macro/AI trends.

Rough buckets:
- MR = 0.0: little exposure (anti-cyclical, robust niche).
- MR = 0.5: moderate exposure (some tasks automatable).
- MR = 1.0: severe exposure (core revenue directly in AI kill-zone).

## 6. System Viability (SV)

A simple composite:
SV = SC / (1.0 + CS_norm + OSR_norm + MR)

Where OSR_norm can be OSR mapped into [0, 1], for example:

OSR_norm = min(1.0, (OSR - 1.0) / 4.0) if OSR > 1 else 0

Low SV (e.g. < 0.2) → collapse zone.

## 7. Collapse Probability (Pc)

This can be modeled as a function of SV and time horizon T.

Example (very rough):
Pc(T) = 1 - exp(-λ * (1 - SV) * T)

Where:
- λ is a scaling parameter (e.g. 0.1–0.5)
- T is in years

Low SV drives Pc toward 1.0 faster.

## 8. Narrative Entropy (NE)

No strict formula required; a simple index:
- Count major narrative pivots over a time window (e.g. 3 years).
- NE = number of pivots / window_length.

Higher NE → more instability, more enemy ammunition.

## 9. Optics Inflation Index (OI)

Optional:
OI = OSR * NE

High OI = high optics + frequent pivots → volatile under scrutiny.
