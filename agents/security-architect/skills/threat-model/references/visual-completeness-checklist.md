# Visual Completeness Checklist

This checklist ensures all applicable visual categories defined in `mermaid-conventions.md` are represented in threat model diagrams. It is used by the **security-architect** during Phase 1 (applicability assessment), Phase 2 (structural diagram construction), and Phase 7 (risk overlay augmentation), and is verified by the **validation-specialist** after all analysis completes.

Every threat model diagram should be audited against these 20 meta-categories. Categories that do not apply to the target system must be explicitly marked with a justification so reviewers can distinguish intentional omissions from oversights.

---

## Instructions

1. **Phase 1 (Reconnaissance)** -- Mark each category as **APPLICABLE**, **NOT APPLICABLE** (with one-line justification), or **N/A**.
2. **NOT APPLICABLE** requires a one-line justification grounded in Phase 1 observations (e.g., "Single-tenant system; no tenant isolation needed").
3. **Phase 2 (Structural Diagram)** -- Verify every category marked APPLICABLE is represented in the structural diagram. Check the box and record which diagram components satisfy it.
4. **Phase 7 (Risk Overlay)** -- Verify every category marked APPLICABLE is represented in the risk overlay diagram. Check the box and record which diagram components satisfy it.
5. **Post-Analysis Verification** -- The validation-specialist reviews this checklist for completeness, confirms evidence fields are populated, and flags any gaps.

---

## Checklist

---

### 1. External Entities

| Property | Value |
|----------|-------|
| Shape | `[Text]` rectangle |
| Style class | `:::external` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 2. Processes

| Property | Value |
|----------|-------|
| Shape | `([Text])` stadium |
| Style class | `:::neutral` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 3. Data Stores

| Property | Value |
|----------|-------|
| Shape | `[(Text)]` cylinder |
| Style class | `:::dataStore` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 4. Trust Boundaries

| Property | Value |
|----------|-------|
| Shape | Dashed subgraphs with color-coded strokes (red / orange / green) |
| Style class | Boundary-specific coloring |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 5. Data Flow Labels

| Property | Value |
|----------|-------|
| Shape | Arrow labels with format `Protocol: data type [SENSITIVITY]` |
| Style class | Edge labels |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 6. Risk Color Coding

| Property | Value |
|----------|-------|
| Shape | Node style classes |
| Style class | `:::highRisk`, `:::medRisk`, `:::lowRisk`, `:::noFindings` |
| Required pass | Risk overlay only |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 7. Threat Annotations

| Property | Value |
|----------|-------|
| Shape | Mermaid `note` blocks |
| Content | STRIDE-LM category, Risk Score, CWE reference |
| Required pass | Risk overlay only |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 8. Component Metadata

| Property | Value |
|----------|-------|
| Shape | Mermaid `note` blocks |
| Content | Tech stack, authentication method, encryption details |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 9. Identity Elements (IAM roles, service accounts)

| Property | Value |
|----------|-------|
| Shape | `{Text}` diamond |
| Style class | `:::identity` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 10. Secrets/Key Management (vaults, HSM, KMS)

| Property | Value |
|----------|-------|
| Shape | `{{Text}}` hexagon |
| Style class | `:::secrets` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 11. Control Plane vs Data Plane

| Property | Value |
|----------|-------|
| Shape | `-.->` dashed arrows = control plane, `-->` solid arrows = data plane |
| Label prefix | `[CP]` for control plane, `[DP]` for data plane |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 12. Attack Paths (kill chains)

| Property | Value |
|----------|-------|
| Shape | `==>` thick red arrows |
| Style class | `:::attackPath` |
| Required pass | Risk overlay only |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 13. Control Indicators (WAF, IDS, MFA, encryption)

| Property | Value |
|----------|-------|
| Shape | `[[Text]]` subroutine |
| Style class | `:::control` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 14. Data Classification Markers

| Property | Value |
|----------|-------|
| Shape | Zone-level subgraph coloring |
| Zones | `PUBLIC` / `INTERNAL` / `CONFIDENTIAL` / `RESTRICTED` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 15. Encryption State Indicators

| Property | Value |
|----------|-------|
| Shape | Lock prefix or label tag in edge labels |
| Notation | Lock icon prefix, or `[ENC]` / `[PLAIN]` in edge labels |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 16. Network Zones

| Property | Value |
|----------|-------|
| Shape | Subgraph layer with CIDR annotations |
| Style class | Zone-specific styling |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 17. Deployment Pipeline (CI/CD, registries)

| Property | Value |
|----------|-------|
| Shape | `[/Text/]` parallelogram |
| Style class | `:::pipeline` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 18. External Dependency Markers

| Property | Value |
|----------|-------|
| Shape | Double-border rectangle |
| Style class | `:::externalDep` |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 19. Tenant Boundaries

| Property | Value |
|----------|-------|
| Shape | Blue dashed subgraphs |
| Style class | Tenant-specific boundary styling |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

### 20. Region Boundaries

| Property | Value |
|----------|-------|
| Shape | Nested subgraphs with region labels, purple dashed stroke |
| Style class | Region-specific boundary styling |
| Required pass | Both (structural + risk overlay) |

- [ ] **Applicable?** YES / NO (justification: _______________) / N/A
- [ ] **Represented in structural diagram?** (Phase 2)
- [ ] **Represented in risk overlay?** (Phase 7)
- **Evidence:** _What was observed during reconnaissance that makes this applicable_
- **Components:** _Which diagram nodes/edges/subgraphs represent this category_

---

## Applicability Guide

Use this table to quickly assess which categories are typically relevant for a given system architecture. This is a starting point; always confirm against actual Phase 1 observations.

**Legend:** &#10003; = typically applicable | &#9675; = sometimes applicable | &#8212; = rarely applicable

| # | Category | Single-service | Microservices | Multi-tenant SaaS | Multi-region | Cloud-native | On-premise |
|---|----------|:-:|:-:|:-:|:-:|:-:|:-:|
| 1 | External Entities | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 2 | Processes | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 3 | Data Stores | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 4 | Trust Boundaries | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 5 | Data Flow Labels | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 6 | Risk Color Coding | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 7 | Threat Annotations | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 8 | Component Metadata | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 9 | Identity Elements | &#9675; | &#10003; | &#10003; | &#10003; | &#10003; | &#9675; |
| 10 | Secrets/Key Mgmt | &#9675; | &#9675; | &#10003; | &#10003; | &#10003; | &#9675; |
| 11 | Control/Data Plane | &#9675; | &#10003; | &#10003; | &#10003; | &#10003; | &#9675; |
| 12 | Attack Paths | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 13 | Control Indicators | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 14 | Data Classification | &#9675; | &#10003; | &#10003; | &#10003; | &#10003; | &#9675; |
| 15 | Encryption State | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 16 | Network Zones | &#9675; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 17 | Deployment Pipeline | &#9675; | &#9675; | &#10003; | &#10003; | &#10003; | &#9675; |
| 18 | External Deps | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; | &#10003; |
| 19 | Tenant Boundaries | &#8212; | &#8212; | &#10003; | &#9675; | &#8212; | &#8212; |
| 20 | Region Boundaries | &#8212; | &#8212; | &#9675; | &#10003; | &#9675; | &#8212; |

---

## Summary Scorecard

Copy and fill in this scorecard at the end of the analysis to provide a quick completeness snapshot.

```
============================================
  VISUAL COMPLETENESS SCORECARD
============================================

  Total categories:                    20
  Applicable:                          __/20
  Not Applicable (with justification): __/20
  N/A:                                 __/20

  Structural Diagram (Phase 2):       __/__ applicable
  Risk Overlay (Phase 7):             __/__ applicable

  Missing from structural diagram:    [list category numbers]
  Missing from risk overlay:          [list category numbers]

  Verified by:          _______________
  Verification date:    _______________
  Status:               PASS / FAIL / PARTIAL
============================================
```
