# Security Audit Summaries

**Independent Security Research | Focused Security Assessments | Responsible Disclosure**

## About

I'm **SFDrake001**, an independent security researcher with an interest in software security, vulnerability research, and practical security testing.

My approach combines hands-on technical investigation with AI-assisted research, analysis, and reporting.

This repository serves as a public record of independent security research and security assessments performed within clearly defined and permitted boundaries.

## Published Security Assessments

| Software / official project | Maintainer | Our assessment | Outcome |
| --- | --- | --- | --- |
| [InformationBox (EvotecIT)](https://github.com/EvotecIT/InformationBox) | [Przemysław Kłys](https://github.com/PrzemyslawKlys) | [InformationBox Security Assessment – September 2026](assessments/informationbox/2026-09-security-assessment.md) | 2 medium-severity vulnerabilities and 2 additional issues remediated; independent retest completed September 30, 2026 |
| [Everything (voidtools)](https://www.voidtools.com/) | [David Carpenter](https://www.voidtools.com/en-us/contact/) ([GitHub](https://github.com/voidtools)) | [Everything Security Assessment and Retest – September–October 2026](assessments/everything/2026-09-30-security-assessment.md) | 1 medium- and 1 low-severity security issue fixed in 1.5.0.1424b; independent retest completed October 15, 2026 |
| [PinTab](https://github.com/schalkburger/pintab) | [Schalk Burger](https://github.com/schalkburger) ([website](https://schalkburger.dev/)) | [PinTab Security Assessment and Retest – September–October 2026](assessments/pintab/2026-09-security-assessment.md) | 1 low-severity hardening issue and 1 functional/policy issue fixed in 1.4.1.0; independent retest completed October 24, 2026 |
| [Cryptomator](https://github.com/cryptomator/cryptomator) | [Skymatic GmbH / Cryptomator Team](https://cryptomator.org/) | [Cryptomator Security Research Summary – October 2026](assessments/cryptomator/2026-10-security-research.md) | Cross-user code execution vulnerability fixed in 1.19.5; published as [GHSA-gqm6-7vjr-g6jr](https://github.com/cryptomator/cryptomator/security/advisories/GHSA-gqm6-7vjr-g6jr), Moderate CVSS 6.7, reporter credit @SFDrake001 |

Each assessment has its own Markdown page. Published summaries focus on verified findings, the maintainer's response, and the outcome of remediation and retesting where applicable.

## What You'll Find Here

The focus is on concise, publicly shareable summaries of security assessments, including:

- Assessment scope and methodology
- Security observations and verified findings
- Testing outcomes and relevant technical context
- Recommendations and lessons learned

The goal is to document real security research clearly, accurately, and without unnecessary complexity.

## Responsible Disclosure

Research is conducted only within clearly defined, lawful, and ethical boundaries. Where explicit authorization is required, it is obtained before testing. Open-source projects may also be reviewed independently using locally controlled systems and test data.

Sensitive information, confidential materials, and details that could expose unresolved vulnerabilities are excluded from public reports.

**Research first. Evidence over assumptions. Responsible disclosure.**
