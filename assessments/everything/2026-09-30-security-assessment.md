# Everything – Security Assessment and Retest (September–October 2026)

**Project:** [Everything – Windows file search by voidtools](https://www.voidtools.com/)  
**Maintainer:** [David Carpenter](https://www.voidtools.com/en-us/contact/) ([GitHub: voidtools](https://github.com/voidtools))  
**Research type:** Authorized independent security assessment  
**Original assessment:** September 29–30, 2026 — Everything 1.5.0.1423b  
**Independent retest:** October 15, 2026 — Everything 1.5.0.1424b  
**Status:** Both confirmed issues remediated and independently retested

During an authorized, local Windows security assessment of Everything, we confirmed two issues involving trust boundaries between users, the Everything Service, and application IPC:

- **EVT-01 — Medium: Everything Service endpoint trust and cross-user search-index poisoning.** A standard-user-controlled endpoint could be mistaken for the legitimate service, allowing false file records to appear in another user's search index and persist across restarts. This affected the search index and its presentation of filesystem information; it did **not** create or alter files in protected Windows directories.
- **EVT-02 — Low: Cross-session IPC modification of another user's client state.** A standard user in a different Windows session could change persistent run-count state belonging to another user's Everything client.

Neither confirmed issue demonstrated arbitrary code execution, elevation of privileges, or unauthorized reading or writing of protected files.

### Remediation and independent retest

The findings were privately reported to **David Carpenter**, the developer of Everything and founder of voidtools, an Australian software company. He investigated the reports and released security improvements in **[Everything 1.5.0.1424b](https://www.voidtools.com/forum/viewtopic.php?t=9787)** on October 15, 2026:

- The Everything client now checks the identity/trust of the service endpoint before accepting its data.
- Everything IPC now rejects connections from other Windows sessions.

An independent retest on Windows 10 Pro x64, using separate local test accounts and synthetic data, confirmed that **both reported security boundaries passed** in the patched build. The original attacks could no longer be reproduced within the tested scope.

**Important correction:** During responsible disclosure, we withdrew an earlier claim that the Everything GUI could be terminated through cross-session IPC3. Further review, assisted by the maintainer, established that the observed `ES -exit` behavior used the ordinary Windows `WM_CLOSE` mechanism, not the IPC3 pipe. **GUI termination is not part of the confirmed EVT-02 finding.**

**Outcome:** 2 confirmed security vulnerabilities (1 Medium, 1 Low), both remediated and independently verified; 1 unsupported portion of the original report explicitly withdrawn.

### About the developer and project

**[David Carpenter](https://www.voidtools.com/en-us/about/)** founded and runs **voidtools**, the Australian developer of Everything, a fast filename-search application for Windows. His verified [GitHub account, `voidtools`](https://github.com/voidtools), hosts related open-source tools including the **[ES command-line interface](https://github.com/voidtools/ES)** and **[Everything SDK3 IPC wrapper](https://github.com/voidtools/everything_sdk3)**. These repositories are related tools, **not** the source repository for the main Everything desktop application.

Official resources: [Everything website](https://www.voidtools.com/) · [Everything downloads](https://www.voidtools.com/downloads/) · [Everything 1.5 beta release notes](https://www.voidtools.com/forum/viewtopic.php?t=9787)

### A Note on Responsible Security Research

This case illustrates two equally important aspects of vulnerability research: verifying fixes independently, and correcting the record when deeper investigation disproves part of an initial finding.

We appreciate David Carpenter's constructive response, technical dialogue, and timely work to strengthen the application's security boundaries.

**Responsible disclosure means reporting only what the evidence supports, working with maintainers, and verifying the resulting improvements.**

*This is a concise public summary, not the confidential assessment or retest report. The conclusions apply to the specific builds, configuration, and security boundaries tested.*
