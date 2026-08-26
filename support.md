---
title: "MetaSync for Confluence — Service Level Agreement (SLA)"
---

<!-- Generated copy of SLA.md — edit the root file, then `npm run docs:export`. -->

[← Documentation home](index.md)

# MetaSync for Confluence — Service Level Agreement (SLA)

**Last Updated:** July 31, 2026
**Product:** MetaSync for Confluence
**Publisher:** MetaSync — independent Marketplace Partner, New South Wales, Australia

This SLA describes the support and service commitments that accompany a MetaSync subscription. It forms part of the [Terms of Service](terms.md) and should be read with the [Privacy Policy](privacy.md).

---

## 1. What MetaSync Is

MetaSync is a **commercially licensed, proprietary** Atlassian Marketplace app, sold as a paid subscription billed by Atlassian. It is **maintained by a single developer**. This SLA is written to set honest expectations for that model rather than to imply enterprise-scale support.

The app runs **entirely on Atlassian Forge**. There is no MetaSync-operated server, database or hosted service, which means MetaSync has no infrastructure of its own to take down — and equally, no infrastructure it can restore independently of Atlassian.

---

## 2. Service Availability

- **Uptime:** best effort. **No numeric uptime commitment is made** and no uptime credits are offered.
- **Platform dependency:** availability substantially tracks Atlassian Confluence Cloud and the Forge platform. Platform status is published at https://status.atlassian.com. Sync additionally depends on the availability of your own Salesforce org and its API limits.
- **Sync cadence:** syncs run on the schedule you configure — hourly, daily, weekly, or a custom cron expression — plus manual runs on demand. A scheduled run is queued by a five-minute background trigger, so a run may begin up to five minutes after its nominal time. This is normal behaviour, not a fault.
- **Resilience:** transient Salesforce and Confluence failures are retried automatically. A run that could not capture everything is reported honestly as *Success with exception* or *Partial* rather than being presented as complete, and the affected data is re-scanned on the next run.
- **Planned maintenance:** app updates are deployed with 48 hours notice where practical. Forge deployments are in-place and do not require downtime; a sync in flight may need to be re-run.
- **Emergency maintenance:** critical security patches are deployed immediately, without notice.

---

## 3. Support

### Channel

- 📧 **Email:** metasync.support@gmail.com — the primary and authoritative support channel
- Support is provided in **English**, during Australian Eastern Time business hours, Monday to Friday, excluding NSW public holidays

### Response targets

These are **targets for a first substantive response**, not resolution guarantees, and they are best-effort commitments rather than contractual deadlines.

| Severity | Definition | Response target |
|---|---|---|
| **S1 — Critical** | Confirmed security vulnerability, credential exposure, or data corruption affecting published documentation | **24 hours** |
| **S2 — High** | Sync fails repeatedly for all runs, app unusable, or a report produces materially wrong access data | **2 business days** |
| **S3 — Normal** | A feature misbehaves or a single metadata type is wrong, with the rest of the app working | **3 business days** |
| **S4 — Low** | Questions, cosmetic issues, documentation gaps, feature requests | Best effort |

To help us respond quickly, include: your Confluence site URL, the app version, the sync run ID and status, the text from **Sync history → Details**, and what you expected to happen. Please do **not** email credentials, tokens or exported access matrices.

### Security issues

Report suspected vulnerabilities to the email address above with "SECURITY" in the subject. We aim to acknowledge within 24 hours and will co-ordinate disclosure with you. Please do not disclose publicly before a fix is available.

### Not included

- 24/7 or on-call support
- Phone, chat or on-site support
- Guaranteed resolution times or SLA credits
- Custom development, bespoke reports, or Salesforce org configuration consulting
- Support for the app running against orgs or sites you are not authorised to access

---

## 4. Data and Security

- **Data access:** Salesforce **metadata only** — never business records. Full detail in the [Privacy Policy](privacy.md).
- **Where data lives:** entirely within Atlassian infrastructure (Forge storage and your Confluence site). MetaSync operates no servers, and follows your Confluence site's data residency configuration.
- **Encryption:** TLS 1.2+ in transit; Salesforce credentials stored as Forge encrypted secrets; all other stored data encrypted at rest by Atlassian.
- **Retention:** rolling caps of 20 sync runs and 4 governance snapshots; all site data is deleted automatically on uninstall.
- **No data sharing:** customer data is never sold, rented or shared. The only optional outbound destinations are Slack and Microsoft Teams webhooks you configure yourself, which receive a status-only payload.
- **Data protection roles:** you are the controller, MetaSync is a processor, Atlassian is a sub-processor. A DPA is available on request.

---

## 5. What This SLA Does Not Guarantee

MetaSync makes **no guarantee** of:

- Any uptime percentage, or credits/compensation for downtime
- 24/7 response
- Delivery of any specific feature request, or delivery by any date
- Backwards compatibility of page structure or report format across major versions
- Completeness or accuracy of generated documentation — output is bounded by the permissions of the integration user you connect, and by Salesforce API version 64.0 (see [Terms of Service](terms.md) §4)
- Suitability of any report or audit pack for a specific auditor, regulator or compliance framework

---

## 6. Intellectual Property and Distribution

- **Licence:** commercial and proprietary. A paid subscription grants a right to use, not ownership.
- **Distribution:** the Atlassian Marketplace only. The app may not be forked, resold or redistributed (see [Terms of Service](terms.md) §1 and §6).
- **Your content:** your Salesforce metadata, your Confluence pages and the documentation generated into your space remain yours.

---

## 7. Service Modifications and Discontinuation

We reserve the right to:

- Modify or improve features, with notice for material changes
- Deprecate a feature with **30 days notice**
- Discontinue the app with **90 days notice** to all active subscribers, after which no further subscription charges are made

If the app is discontinued, documentation already published to your Confluence space remains in place and remains yours; it does not depend on the app to be readable.

---

## 8. Liability

MetaSync is provided "AS IS" without warranty. Liability is limited as set out in [Terms of Service](terms.md) §10, including the cap at fees paid in the preceding twelve months. Nothing in this SLA excludes rights that cannot be excluded under applicable law, including the Australian Consumer Law.

---

## 9. Changes to This SLA

This SLA may be updated. Material changes are reflected in the "Last Updated" date above and published with the app's Atlassian Marketplace listing. Continued use constitutes acceptance of the current version.

---

## 10. Contact

📧 **Support, security and billing questions:** metasync.support@gmail.com
📄 **Privacy Policy:** [PRIVACY.md](privacy.md)
📄 **Terms of Service:** [TERMS.md](terms.md)
