# PDF-XChange Editor security assessment and retest (October to November 2026)

**Project:** [PDF-XChange Editor for Windows](https://www.pdf-xchange.com/product/pdf-xchange-editor)  
**Maintainer:** [PDF-XChange Co Ltd](https://www.pdf-xchange.com/)  
**Research type:** Authorized independent security assessment  
**Tested version:** 11.1.1.0  
**Retested version:** [11.1.2.0](https://www.pdf-xchange.com/product/pdf-xchange-editor/history?build=11.1.2.0)  
**Status:** All three reported issues passed independent retesting under default settings.

During an authorized assessment of PDF-XChange Editor for Windows, we identified three security issues affecting document import in version 11.1.1.0.

- **Document access.** Content in an imported Markdown document could gain access to local files beyond the document’s own folder.
- **Active content in email.** Imported email messages could run embedded scripts or contact external servers under the default settings.
- **External connections in an email-reading component.** A separate issue allowed a component used by the editor to contact an external server automatically while processing a message.

We rated the first issue High and the two email-related issues Medium in the assessed build.

### Remediation and independent retest

We reported the findings privately to PDF-XChange Co Ltd. The maintainer changed the default handling of imported content and updated the affected email-reading component. We retested the public Windows release, [PDF-XChange Editor 11.1.2.0](https://www.pdf-xchange.com/product/pdf-xchange-editor/history?build=11.1.2.0), with its default settings.

**Outcome:** None of the three reported behaviors recurred in the retest. This result applies to the document-import features and settings assessed.
