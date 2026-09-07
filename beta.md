---
title: "Beta Programme"
---

<!-- Source: metasync/docs/BETA_PROGRAM.md with the placeholders filled in. Update the source, then this copy. -->

[← Documentation home](index.md)

# MetaSync for Confluence — Beta Programme

## What MetaSync does

MetaSync documents a Salesforce org into Confluence, on a schedule. It reads your org's **configuration metadata** — objects, fields, record types, validation rules, flows, Apex, profiles, permission sets, roles, layouts, reports, dashboards, and more — and publishes it as a living page tree in a Confluence space you choose, with an ERD, change-impact analysis, and access-review reports.

Three promises, and they are enforced in code, not just in prose:

- **One-way and read-only.** Salesforce → Confluence, never back. MetaSync never writes to Salesforce.
- **Metadata, not records.** It never queries or stores business records (no Accounts, Contacts, Opportunities, custom object rows). It does read limited *administrative* personal data for the access-review reports — user names, emails, last logins, permission assignments, Setup Audit Trail entries — and that is disclosed in the [Privacy Policy](privacy.md).
- **Least privilege.** The connection uses only the `api` and `refresh_token` OAuth scopes; what MetaSync can see is defined by the Salesforce permissions of the integration user you sign in as.

## What the beta needs from you

| You need | Notes |
|---|---|
| **Confluence Cloud** with site-admin rights | Forge apps are Cloud-only. Install is via a private link we send you; installing takes about a minute. |
| A **Salesforce org** with API access | Enterprise / Unlimited / Performance / Developer editions include it; Professional needs the Web Services API add-on; Essentials/Group cannot connect. A sandbox is fine to start; production metadata gives the most useful feedback. |
| An **External Client App** in that org | ~10 minutes; the [Getting started](getting-started.md) guide walks through it, with a recipe for each connection method. (New *Connected Apps* can no longer be created in most orgs since Spring '26 — External Client Apps replace them; an existing Connected App also works.) |
| A **dedicated integration user** | Least privilege, user permissions only: API Enabled, View Setup and Configuration, View Roles and Role Hierarchy, plus View All Profiles (required from Salesforce Winter '27, whose Profile Filtering update otherwise hides other users' profiles) and optional Modify Metadata Through Metadata API Functions and Author Apex for wider coverage. **No object permissions at all** — no read, create, edit or delete on any object, standard or custom; the permission set's Object Settings list stays empty. |
| A **dedicated Confluence space** for the output | MetaSync creates and updates pages under a home page it owns; give it its own space during the beta. |
| **About 30 minutes a week**, plus two 30-minute calls | Week 1 (onboarding, live) and week 4 (feedback). |

## What we promise during the beta

- **Response time:** next business day (Australian Eastern Time, Mon–Fri) for anything; same day for a sync that is failing for everyone.
- **A named person:** you are talking to the developer, not a queue.
- **Weekly notes** every Friday — what changed, known issues, what to try next.
- **No surprises with your data:** everything in the [Privacy Policy](privacy.md) applies in beta exactly as at general availability. Uninstalling purges all app data (credentials, snapshots, history) from Forge storage; your Confluence pages remain yours.
- **Honesty about maturity:** it's a beta. There is no uptime SLA, features may change, and pages may occasionally re-publish while we tune churn suppression. The [Beta Terms Addendum](#beta-terms-addendum) below sets this out.

## What we ask of you

1. Run it against a **real org** on the schedule (not just once).
2. Leave **app log sharing enabled** in Confluence (Manage apps → MetaSync (Beta) → app logs) so we can see errors for your site — logs never contain your Salesforce metadata, credentials, or record data.
3. Use **Report a problem** in the app (it pre-fills the diagnostics we need) or email support.metasync@maashive.app.
4. Two calls (week 1, week 4) and honest answers to the week-4 questions, including what this would be worth to your team.
5. Permission to quote you (anonymised if you prefer) and, if you find it useful, an **honest review** on the Atlassian Marketplace at launch — never conditioned on being positive, never incentivised.

## Dates and what happens after

- **Beta runs until 29 November 2026.**
- **General availability:** the Marketplace listing goes live once the exit criteria below are met (target: week of 30 November 2026).
- **Founding-customer price:** beta orgs get 50 % off for 12 months from GA.
- **Migration:** the beta app and the Marketplace app are two separate app registrations. At GA you uninstall **MetaSync (Beta)**, install **MetaSync for Confluence** from the Marketplace, update the Callback URL in your External Client App (it is per-installation), reconnect, and choose the same space — existing pages are adopted by title. Change-impact baselines and sync history start fresh; the pages don't. We'll do it with you on a call.

## Exit criteria (how we decide it's ready)

- ≥ 5 orgs syncing on schedule for ≥ 4 consecutive weeks; ≥ 90 % scheduled-sync success over the trailing 30 days.
- 0 open critical issues; every known limitation disclosed on the page or run row it affects.
- ≥ 3 testers connected an org from the docs alone, in under 30 minutes.
- Marketplace listing approved and pricing set.
- Median first response under one business day, held for four weeks.

---

## Beta Terms Addendum

*These beta terms sit alongside the [Terms of Service](terms.md), [Privacy Policy](privacy.md) and [Support Policy](support.md). They narrow our promises for the beta period; they do not widen data use.*

1. **Beta status.** MetaSync (Beta) is pre-release software provided for evaluation and feedback. It is supplied **as is** and **as available**, without warranty of any kind, and without the support response targets in the [Support Policy](support.md); the response commitments on this page apply instead.
2. **Changes and discontinuation.** Features, page structure and behaviour may change during the beta. We may suspend or end the beta, or any participant's access, at any time; we will give at least 14 days' notice of the planned end date except where security requires otherwise.
3. **Data.** The Privacy Policy applies in full. MetaSync (Beta) reads Salesforce configuration metadata and limited administrative personal data, stores it in Atlassian Forge storage for your installation only, and deletes it on uninstall. Uninstalling MetaSync (Beta) does not delete pages it published in Confluence.
4. **Feedback.** You grant us a perpetual, royalty-free licence to use suggestions, bug reports and other feedback you provide, without obligation to you. We will not name you or your organisation publicly without your consent.
5. **Confidentiality.** Non-public information about the beta (unreleased features, roadmap, pricing plans) is confidential until general availability. Your own data is yours; we ask nothing beyond the Privacy Policy.
6. **Liability.** To the fullest extent permitted by law, our aggregate liability arising out of the beta is limited to AUD 100. Nothing here excludes liability that cannot be excluded by law.
7. **Term.** These beta terms end on the beta end date or when you uninstall MetaSync (Beta), whichever is first. Continuing with the Marketplace release is governed by the standard [Terms of Service](terms.md).

---

Questions before you install? Email **support.metasync@maashive.app**.
