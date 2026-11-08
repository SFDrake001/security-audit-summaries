# Bashirra Security Research — Public Audit Summaries

[**bashirra.com**](https://bashirra.com/) · [Research archive](https://bashirra.com/research/) · [Security assessments](https://bashirra.com/services/) · [Coordinated disclosure](https://bashirra.com/disclosure/)

**Independent Security Research | Vulnerability Research | Responsible Disclosure**

## About

This repository is the public evidence companion to [Bashirra](https://bashirra.com/), an independent application security research and assessment practice.

I'm **Andrzej Similski (@SFDrake001)**, an independent security researcher focused on practical software security, vulnerability research, and responsible disclosure.

My work focuses on identifying real security-boundary failures, especially in desktop applications: cross-user trust boundaries, privileged configuration, IPC, services, update paths, executable resolution, and other places where lower-privileged input may influence higher-privileged or cross-user behavior.

This repository is a public record of verified security research and focused security assessments performed within clearly defined and permitted boundaries.

## Published Security Assessments

| Software / official project | Maintainer | Our assessment | Outcome |
| --- | --- | --- | --- |
| [InformationBox (EvotecIT)](https://github.com/EvotecIT/InformationBox) | [Przemysław Kłys](https://github.com/PrzemyslawKlys) | [InformationBox Security Assessment – September 2026](assessments/informationbox/2026-09-security-assessment.md) | 2 medium-severity vulnerabilities and 2 additional issues remediated; independent retest completed September 30, 2026 |
| [Everything (voidtools)](https://www.voidtools.com/) | [David Carpenter](https://www.voidtools.com/en-us/contact/) ([GitHub](https://github.com/voidtools)) | [Everything Security Assessment and Retest – September–October 2026](assessments/everything/2026-09-30-security-assessment.md) | 1 medium- and 1 low-severity security issue fixed in 1.5.0.1424b; independent retest completed October 15, 2026 |
| [PinTab](https://github.com/schalkburger/pintab) | [Schalk Burger](https://github.com/schalkburger) ([website](https://schalkburger.dev/)) | [PinTab Security Assessment and Retest – September–October 2026](assessments/pintab/2026-09-security-assessment.md) | 1 low-severity hardening issue and 1 functional/policy issue fixed in 1.4.1.0; independent retest completed October 24, 2026 |
| [Cryptomator](https://github.com/cryptomator/cryptomator) | [Skymatic GmbH / Cryptomator Team](https://cryptomator.org/) | [Cryptomator Security Research Summary – October 2026](assessments/cryptomator/2026-10-security-research.md) | Cross-user code execution vulnerability fixed in 1.19.5; published as [GHSA-gqm6-7vjr-g6jr](https://github.com/cryptomator/cryptomator/security/advisories/GHSA-gqm6-7vjr-g6jr), Moderate CVSS 6.7, reporter credit @SFDrake001 |

Each assessment has its own Markdown page. Published summaries focus on verified findings, the maintainer's response, and the outcome of remediation and retesting where applicable.

## Research Principles

- Evidence over assumptions.
- Focus on trust boundaries and concrete attacker capabilities.
- Distinguish vulnerabilities from hardening and functional issues.
- Use controlled systems, synthetic data, and minimal-impact proofs of concept.
- Report privately before publishing unresolved security issues.
- Retest the underlying security boundary after remediation.

## Responsible Disclosure

Research is conducted only within clearly defined, lawful, and ethical boundaries. Where explicit authorization is required, it is obtained before testing. Open-source projects may also be reviewed independently using locally controlled systems and test data.

Sensitive information, confidential materials, and details that could expose unresolved vulnerabilities are excluded from public reports.

**Research first. Evidence over assumptions. Responsible disclosure.**
