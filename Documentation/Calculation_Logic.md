# Calculation Logic

## Overview

This document explains the calculation workflow used by the Defender VM Risk Prioritization Engine.

The objective is to transform raw vulnerability data into actionable remediation priorities by combining vulnerability severity, exploitation probability, threat activity, exposure, age, and business context.

---

# Calculation Flow

```
Defender VM Export
        ↓
Normalize Vulnerability Attributes
        ↓
Calculate Individual Risk Factors
        ↓
Generate Final Risk Score
        ↓
Assign Priority Level (P1-P4)
        ↓
Apply SLA and Ownership Mapping
        ↓
Generate Remediation Intelligence
```

---

# 1. CVSS Calculation

Purpose:

Measure the technical severity of the vulnerability.

Logic:

```
CVSS Points = (CVSS Score / 10) × 25
```

Reason:

A vulnerability with a higher technical impact contributes more risk, but severity alone should not determine remediation priority.

---

# 2. EPSS Calculation

Purpose:

Measure exploitation probability.

Logic:

Higher EPSS values receive higher weight because vulnerabilities likely to be exploited should receive faster remediation.

Example:

```
High CVSS + High EPSS
=
Higher operational priority
```

Reason:

A critical vulnerability with no exploitation activity may represent less immediate risk than an actively exploited vulnerability.

---

# 3. Threat Intelligence Calculation

Purpose:

Identify vulnerabilities associated with real-world attacker activity.

Risk increases when:

- Public exploit exists
- Known threat activity exists
- Security alerts are associated

Reason:

Confirmed attacker interest increases remediation urgency.

---

# 4. Exposure Calculation

Purpose:

Measure environment impact.

Example:

A vulnerability affecting:

```
1 device
```

does not create the same operational exposure as:

```
1,000 devices
```

Reason:

Higher exposure increases the probability of compromise and business impact.

---

# 5. Vulnerability Age Calculation

Purpose:

Identify long-standing unresolved weaknesses.

Older vulnerabilities increase priority because they represent:

- Delayed remediation
- Increased attacker opportunity window
- Technical debt

---

# 6. Business Impact Calculation

Purpose:

Add asset importance into prioritization.

Examples:

Critical systems receive higher priority:

- Domain Controllers
- Servers
- Business critical applications
- Internet-facing assets

Reason:

Two systems with the same vulnerability may not represent the same business risk.

---

# Final Risk Score

All components are combined:

```
Final Score =
Technical Risk
+ Exploitation Probability
+ Threat Context
+ Exposure
+ Age
+ Business Impact
```

---

# Priority Assignment

The final score is translated into remediation priority:

| Priority | Action |
|---|---|
| P1 | Immediate attention required |
| P2 | High priority remediation |
| P3 | Standard planned remediation |
| P4 | Monitor / normal lifecycle |

---

# SLA Logic

Each priority receives an associated remediation timeline.

The engine tracks:

- SLA due date
- Overdue vulnerabilities
- Upcoming remediation deadlines
- Closed items

---

# Ownership Mapping

The engine maps remediation ownership based on:

- Software category
- Asset context
- Responsible technology team

This improves accountability and remediation tracking.

---

# Summary

The engine moves vulnerability management from:

Quantity-based remediation

to:

Risk-driven remediation decisions.
