# Cryptomator – Security Research Summary (October 2026)

**Project:** [Cryptomator](https://github.com/cryptomator/cryptomator)  
**Maintainer:** [Skymatic GmbH / Cryptomator Team](https://cryptomator.org/)  
**Research type:** Independent security research on an open-source project  
**Affected versions:** Cryptomator 1.19.0–1.19.4 on Windows  
**Tested version:** Cryptomator Desktop 1.19.3  
**Fixed version:** [Cryptomator 1.19.5](https://github.com/cryptomator/cryptomator/releases/1.19.5)  
**Advisory:** [GHSA-gqm6-7vjr-g6jr](https://github.com/cryptomator/cryptomator/security/advisories/GHSA-gqm6-7vjr-g6jr)  
**Severity:** Moderate — CVSS 3.1: 6.7/10  
**CWE:** CWE-732  
**Status:** Privately reported, remediated, and publicly disclosed

During independent security research on Cryptomator Desktop for Windows, we identified a trust-boundary vulnerability in the machine-wide administrative configuration path.

A standard Windows user could pre-create:

`C:\ProgramData\Cryptomator\config.properties`

before Cryptomator was installed, or before upgrading from a version prior to 1.19.0. Because the installer preserved the existing file without resetting its owner or ACL, the lower-privileged user could retain control over the administrative configuration after installation.

The configuration could override settings including `cryptomator.pluginDir`. This allowed a standard user to prepare an attacker-controlled plugin that Cryptomator could later load when another user on the same machine started the application, resulting in **cross-user code execution** in the context of that user.

The issue was privately reported to the Cryptomator team following the project's security disclosure process.

### Official advisory

Cryptomator published [GHSA-gqm6-7vjr-g6jr](https://github.com/cryptomator/cryptomator/security/advisories/GHSA-gqm6-7vjr-g6jr), titled **“Pre-install planting of the Windows admin config enables cross-user code execution.”**

The advisory rates the vulnerability **Moderate (CVSS 3.1: 6.7/10)** with the vector:

`CVSS:3.1/AV:L/AC:H/PR:L/UI:R/S:U/C:H/I:H/A:H`

Affected versions are **1.19.0 through 1.19.4**, with **1.19.5** listed as the patched version. The advisory classifies the issue as **CWE-732: Incorrect Permission Assignment for Critical Resource**.

The reporter credit in the published advisory is **[@SFDrake001](https://github.com/SFDrake001)**.

### Remediation

The Cryptomator team implemented the fix through [Pull Request #4362](https://github.com/cryptomator/cryptomator/pull/4362) and released it in Cryptomator 1.19.5.

The remediation addresses the underlying trust boundary rather than only the original proof of concept:

- The Windows installer secures the administrative configuration directory before writing files into it.
- Cryptomator verifies the owner and permissions of the administrative configuration before trusting it.
- The configuration file and its ancestor directories must not be modifiable by untrusted principals.
- Only trusted Windows principals such as SYSTEM, Administrators, or TrustedInstaller may control the relevant configuration path.
- Paths involving symbolic links or junctions are rejected for the administrative configuration.

The [Cryptomator 1.19.5 changelog](https://github.com/cryptomator/cryptomator/blob/main/CHANGELOG.md) documents the security fix as preventing a standard user from planting the admin configuration before installation and thereby causing other users to load arbitrary plugins.

**Outcome:** 1 cross-user code execution vulnerability identified, privately disclosed, fixed in Cryptomator 1.19.5, and published as GHSA-gqm6-7vjr-g6jr with reporter credit to @SFDrake001.

### A Note on Responsible Security Research

Cryptomator is an open-source project, and this research was conducted independently using locally controlled systems and test data.

The finding was reported privately before publication. The Cryptomator team investigated the issue, implemented a security-focused fix, coordinated disclosure, and credited the researcher in the published GitHub Security Advisory.

We appreciate the Cryptomator team's constructive response and the care taken to address the underlying trust boundary rather than only the specific proof of concept.

**Responsible security research is most valuable when a reproducible security boundary is identified, communicated clearly, and ultimately strengthened.**

*This is a concise public summary of independent security research, not the confidential assessment report. The conclusions apply to the affected Windows versions and security boundary described above.*
