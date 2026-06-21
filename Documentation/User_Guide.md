# User Guide

## Defender VM Risk Prioritization Engine v1.0

This guide explains how to use the Defender VM Risk Prioritization Engine.

The engine converts Microsoft Defender Vulnerability Management export data into prioritized remediation actions using risk-based scoring.

---

# Requirements

To use the engine:

- Microsoft Excel
- Microsoft Defender Vulnerability Management vulnerability export
- Basic understanding of vulnerability remediation ownership

---

# Workbook Structure

The workbook contains multiple sections:

---

## 1. About

Provides:

- Engine overview
- Version information
- Feature summary
- Project disclaimer

---

## 2. Instructions

Provides:

- Quick start workflow
- Usage steps
- Important notes

---

## 3. Defender Export

Purpose:

Input sheet for Microsoft Defender Vulnerability Management vulnerability data.

Steps:

1. Export vulnerability data from Defender VM
2. Paste/import data into this sheet
3. Keep the expected column structure

The Risk Engine will use this data for calculations.

---

## 4. Risk Engine

Main calculation layer.

Automatically generates:

- CVSS scoring
- EPSS weighting
- Threat intelligence score
- Exposure impact
- Vulnerability age score
- Business context score
- Final risk score
- Priority level
- SLA status
- Owner mapping
- Remediation guidance

Important:

Do not overwrite calculation columns unless modifying the scoring model.

---

## 5. Asset Context

Used to customize prioritization based on the environment.

Configure:

- Software ownership
- Asset groups
- Criticality
- Exposure type
- Business impact

Example:

Critical server vulnerabilities can receive higher priority than standard endpoint findings.

---

## 6. Executive Dashboard

Provides management visibility:

- Vulnerability overview
- Risk distribution
- Priority tracking
- SLA status
- Top risky vulnerabilities

Designed for reporting and decision-making.

---

## 7. Remediation Intelligence

Provides operational remediation insights:

- Owner-based grouping
- Number of open vulnerabilities
- Priority distribution
- Exposure impact
- Recommended actions

Helps teams focus on highest risk reduction activities.

---

# Recommended Workflow

```
1. Import Defender VM Export

2. Review Asset Context

3. Validate Risk Engine Results

4. Review Executive Dashboard

5. Track Remediation Intelligence

6. Update vulnerability status
```

---

# Customization

Organizations can modify:

- Risk scoring weights
- Priority thresholds
- SLA timelines
- Ownership mapping
- Asset criticality

based on their vulnerability management policy.

---

# Notes

This engine is designed as an operational prioritization layer.

It should support vulnerability management decisions together with existing security processes and business requirements.


