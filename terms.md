---
title: "Terms of Service"
---

<!-- Generated copy of TERMS.md — edit the root file, then `npm run docs:export`. -->

[← Documentation home](index.md)

# Terms of Service

**Last Updated:** July 31, 2026

These terms govern your use of **MetaSync for Confluence** ("MetaSync", "the app"). By installing or using the app, you agree to them. If you are accepting on behalf of an organisation, you confirm you have authority to bind it.

---

## 1. Licence and Use

MetaSync is a **commercial application distributed through the Atlassian Marketplace under a paid subscription**, billed by Atlassian ("Paid via Atlassian"). Your subscription grants a non-exclusive, non-transferable, revocable right to install and use the app in your own Confluence Cloud site for the duration of the subscription.

You may:
- Use the app in your Confluence Cloud site while your subscription is active
- Configure it for your organisation's needs
- Retain and use the documentation it produces, during and after the subscription

You may not:
- Reverse-engineer, decompile or disassemble the app, except to the extent that restriction is unenforceable under applicable law
- Redistribute, resell, sublicense or host the app for third parties
- Circumvent security, administrator gating, or licensing measures
- Use the app in breach of Salesforce's or Atlassian's terms of service

## 2. Requirements

To use MetaSync you need:

- An active **Confluence Cloud** site with an active MetaSync subscription
- An active **Salesforce** organisation (Developer Edition or higher) with API access enabled
- **Salesforce:** a connected integration user with *View Setup and Configuration*, API Enabled, and read access to the metadata entities MetaSync queries (see the Privacy Policy, section 1)
- **Confluence:** site administrator rights to install, and to manage who may use the app. Sync, configuration and access-report actions are restricted to Confluence site administrators and to users an administrator nominates with the *App admin* role under *Additional access*; users nominated without that role have read-only access to the app's dashboards and reports. Access to the documentation pages MetaSync publishes into Confluence is governed by Confluence space permissions, not by this nomination. Only site administrators can change who has access or which role they hold.

## 3. Subscription, Billing and Licence Status

- Billing, invoicing, pricing tiers, trials, taxes and refunds are handled by **Atlassian** under the Atlassian Marketplace Terms of Use. We do not process your payment details.
- **If your licence lapses or is cancelled**, MetaSync pauses syncing and report generation. Documentation already published to your Confluence space **remains in place and remains yours**. Settings are retained so a renewed subscription resumes where you left off; uninstalling deletes them (see section 9).
- We may change pricing with the notice period required by Atlassian's Marketplace policies.

## 4. Nature of the Service — Important

MetaSync produces **documentation and compliance evidence artifacts derived from your Salesforce configuration**. You must understand the following before relying on them:

- Output is **only as complete and accurate as the permissions of the integration user you connect.** If that user cannot read a component, MetaSync labels it "Not captured" rather than guessing — but the resulting documentation is a partial view of your org.
- Output is a **point-in-time snapshot**, refreshed on the schedule you configure. It is not a live view.
- Governance reports, access matrices, posture scores and audit packs are **informational tooling, not legal, audit, security or compliance advice**, and are not certified by any standards body or auditor. Their fitness for any specific audit, regulator or framework is your assessment to make.
- MetaSync is one input to your compliance process, not a substitute for it. **Do not use its exports as your sole source of truth.**

## 5. Disclaimers

MetaSync is provided **"AS IS" and "AS AVAILABLE"**, without warranties of any kind, whether express, implied or statutory, including any implied warranty of merchantability, fitness for a particular purpose, accuracy, or non-infringement.

We do not warrant that:
- The app will be uninterrupted, timely, error-free, or achieve any uptime figure
- Documentation or reports it generates will be complete, accurate or current
- It will remain compatible with future Salesforce or Atlassian releases
- Any defect will be corrected within a particular time

Support commitments are set out in the accompanying **Service Level Agreement (SLA)**, which forms part of these terms. Nothing in this section limits rights that cannot be excluded under applicable consumer law, including the Australian Consumer Law.

### Your responsibilities
- Review synced documentation for accuracy before relying on it
- Do not use exports as your sole source of truth for compliance
- Maintain independent backups of critical documentation
- Test in a sandbox or non-critical space before production use
- Keep your OAuth credentials secure and scope the integration user tightly
- Control who can view the destination Confluence space

## 6. Intellectual Property

- **The app.** MetaSync's code, design and documentation are the property of the MetaSync author. All rights reserved. Your subscription is a right to use, not a transfer of ownership and not a redistribution licence.
- **Your Confluence pages.** Yours, including the documentation MetaSync generates into your space.
- **Your Salesforce metadata and source code.** Remains your property at all times. MetaSync claims no rights in it and does not retain it after uninstall.
- **Feedback.** If you send us suggestions, we may use them without obligation or compensation.

## 7. Data Protection

- You are the **data controller**; MetaSync acts as a **data processor** for the administrative personal data it handles; **Atlassian is a sub-processor** for all hosting and storage.
- MetaSync reads Salesforce **metadata only** — never business records — and stores it in Atlassian Forge storage within your Confluence site's infrastructure. It runs no servers of its own.
- The full detail of what is accessed, stored, for how long, who can see it, and how deletion works is set out in the **Privacy Policy**, which forms part of these terms.
- A **Data Processing Addendum (DPA)** is available on request.
- You are responsible for having a lawful basis for processing the administrative personal data of your Salesforce users through the app, and for informing them where your own obligations require it.

## 8. Acceptable Use

You agree not to use MetaSync to:
- Access any Salesforce org you are not authorised to access
- Circumvent access controls in Salesforce, Confluence or the app itself
- Publish administrative personal data to a Confluence space where its audience is inappropriate for that data
- Conduct unlawful activity, or place unreasonable load on the Atlassian or Salesforce platforms

## 9. Termination

Either party may terminate at any time; you do so by uninstalling the app or cancelling the subscription through Atlassian. We may suspend or terminate access if you materially breach these terms, breach Salesforce's or Atlassian's terms, or use the app unlawfully.

On termination or uninstall:
- Syncing stops immediately
- All data MetaSync holds for your site is deleted automatically — credentials, snapshots, caches and configuration (see the Privacy Policy, section 9)
- Documentation pages already published **remain in your Confluence space** and remain yours
- Any refund is governed by Atlassian's Marketplace refund policy

## 10. Limitation of Liability

To the maximum extent permitted by law, the MetaSync author is not liable for indirect, incidental, special, consequential or punitive damages, nor for loss of profits, revenue, data, goodwill or business interruption, arising out of or relating to the app — including reliance on documentation, reports or compliance artifacts it produces — whether in contract, tort or otherwise, and whether or not we were advised of the possibility.

**Total aggregate liability is capped at the total subscription fees you paid for MetaSync in the twelve months preceding the event giving rise to the claim.**

Nothing here excludes liability that cannot be excluded by law.

## 11. Third-Party Services

MetaSync runs entirely on **Atlassian Forge**; there is no separate MetaSync-operated server or third-party host. It integrates with:

- **Salesforce** — your own org, read-only. Your use of Salesforce is governed by your agreement with Salesforce.
- **Atlassian / Confluence Cloud** — hosting, storage and distribution, governed by your agreement with Atlassian.
- **Slack and Microsoft Teams** — optional, off by default, only if you configure a webhook. Delivery to those services is governed by your agreement with them.

We are not responsible for third-party outages, changes or discontinuations.

## 12. Changes to These Terms

We may update these terms. Material changes will be reflected in the "Last Updated" date and published with the app's Marketplace listing. Continued use after a change constitutes acceptance.

## 13. Governing Law

These terms are governed by the laws of New South Wales, Australia, without regard to conflict-of-law principles. The courts of New South Wales have non-exclusive jurisdiction.

## 14. Contact

- 📧 **Email:** metasync.support@gmail.com

---

## Summary

**MetaSync is a paid Atlassian Marketplace app provided "as is."** It documents your Salesforce configuration into your own Confluence site and stores nothing outside Atlassian's infrastructure. Its reports are useful compliance *input*, not compliance *proof* — review them, keep backups, and don't make them your sole source of truth.

**By installing MetaSync, you agree to these terms and to the accompanying Privacy Policy and SLA.**
