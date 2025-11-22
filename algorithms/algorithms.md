# TSAF Algorithms (Pseudocode)

## 1. structural_audit(entity)

Input: JSON describing an entity (see `datasets/schema.json`)
Output: metrics (R, SC, OSR, CS, SV, Pc, qualitative verdict)

Pseudo:

1. Parse claims, structural_data, contradictions, optics_strategy, risk_factors.
2. Estimate recursion score R from language patterns and strategy depth.
3. Score evidence strength E and claim complexity C → compute SC.
4. Score optics O and structure S → compute OSR.
5. Aggregate contradictions with weights → compute CS and CS_norm.
6. Estimate Macro Risk MR based on automation risk + competition.
7. Compute SV using formulas in `equations.md`.
8. For chosen time horizon T (e.g., 3 years), compute Pc(T).
9. Produce a qualitative verdict:
   - If SV < threshold_low → "Collapse zone"
   - Else if SV between thresholds → "Unstable / needs restructuring"
   - Else → "Structurally viable"
10. Return all scores + explanations.

## 2. estimate_recursion_score(claims, behavior)

Heuristic examples:
- If claims are binary (good/bad, winner/loser) with no feedback logic → R ≈ 1–1.5
- If entity recognizes tradeoffs but ignores macro/AI → R ≈ 2.5–3.5
- If entity designs whole systems, admits uncertainty, and models competitive response → R ≥ 5

## 3. compute_SC(evidence, claims)

E = score_evidence(structural_data)
C = score_claim_complexity(claims)

SC = E / (C + ε)

## 4. compute_OSR(optics_features, structural_data)

O = score_optics(optics_features)
S = score_structure(structural_data)

OSR = O / (S + ε)

## 5. compute_CS(contradictions)

CS = Σ w_i over all contradictions
CS_norm = min(1.0, CS / K)

## 6. compute_SV(SC, CS_norm, OSR, MR)

OSR_norm = map_OSR_to_unit_interval(OSR)
SV = SC / (1.0 + CS_norm + OSR_norm + MR)

## 7. compute_Pc(SV, T, λ)

Pc = 1 - exp(-λ * (1 - SV) * T)

## 8. generate_risk_map(...)

Combine:
- Macro risk (MR)
- Market risk
- Cognitive risk (R, CS, NE)
- System risk (negative unit economics)

and output a simple table of entropy drivers and containment layers.
