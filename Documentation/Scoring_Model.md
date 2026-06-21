# Risk Scoring Model

## Overview

The Defender VM Risk Prioritization Engine calculates vulnerability risk using multiple security and operational factors.

Traditional vulnerability management often relies mainly on severity. This model combines exploit likelihood, threat context, exposure, age, and business impact to provide operational prioritization.

---

# Final Risk Score

```
Risk Score =
CVSS Points
+ EPSS Points
+ Threat Intelligence Points
+ Exposure Points
+ Age Points
+ Business Impact Points
```

---

# Scoring Components


## 1. CVSS Impact

CVSS represents the technical severity of the vulnerability.

Calculation:

```
CVSS Points = (CVSS Score / 10) × 25
```

Maximum contribution:

25 points


---

## 2. EPSS Probability

EPSS estimates the likelihood of exploitation activity.

| EPSS Score | Points |
|---|---|
| >= 0.70 | 20 |
| >= 0.30 | 15 |
| >= 0.10 | 10 |
| < 0.10 | 2 |

---

## 3. Threat Intelligence

Threat indicators increase priority.

| Indicator | Points |
|---|---|
| Public exploit available | +10 |
| Known active threats | +15 |
| Related security alerts | +5 |

---

## 4. Exposure Impact

Prioritizes vulnerabilities affecting more assets.

| Exposed Machines | Points |
|---|---|
| >500 | 15 |
| 100-500 | 10 |
| 10-99 | 5 |
| <10 | 1 |

---

## 5. Vulnerability Age

Older unresolved vulnerabilities increase operational risk.

| Age | Points |
|---|---|
| >90 days | 10 |
| 30-90 days | 5 |
| <30 days | 1 |

---

## 6. Business Context

Adds asset criticality awareness.

Examples:

| Asset Type | Impact |
|---|---|
| Domain Controllers | Critical |
| Exchange Servers | Critical |
| SQL Servers | High |
| Internet Facing Assets | High |
| Workstations | Standard |

---

# Priority Classification

| Priority | Meaning |
|---|---|
| P1 | Immediate remediation focus |
| P2 | High priority remediation |
| P3 | Planned remediation |
| P4 | Standard remediation lifecycle |

---

# Note

The scoring model can be adjusted based on organizational risk appetite.
