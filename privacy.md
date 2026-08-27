---
title: "Privacy Policy"
---

<!-- Generated copy of PRIVACY.md — edit the root file, then `npm run docs:export`. -->

[← Documentation home](index.md)

# Privacy Policy

**Last Updated:** August 25, 2026

## Overview

MetaSync for Confluence is a one-way, read-only Salesforce-to-Confluence **metadata** documentation connector. It reads configuration and access metadata from your Salesforce org and publishes it as documentation pages in your Confluence site. This policy explains what data the app accesses, what it stores, where it is stored, how long it is kept, who can see it, and how it is protected.

MetaSync never writes back to Salesforce and never reads your customer **business records** (accounts, contacts, opportunities, cases, attachments, etc.).

## Roles Under Data Protection Law

- **You are the data controller.** You decide which Salesforce org is connected, which permissions the integration user holds, which metadata is in scope, and which Confluence space the documentation is published to.
- **MetaSync is a data processor**, acting on your instructions, for the administrative personal data described in section 1.3.
- **Atlassian is a sub-processor** for all storage and compute (see section 8).

A Data Processing Addendum (DPA) is available on request from the contact address at the end of this policy.

### Frameworks this policy is written against

MetaSync is built to support your obligations under the **EU/UK GDPR**, the **Australian Privacy
Act 1988 (APP 11 — security of personal information)**, and the **California Consumer Privacy Act
(CCPA/CPRA)**. Because MetaSync processes configuration metadata rather than customer business
records, the personal data in scope is limited to the administrative data listed in section 1.3.

- **Data-subject / consumer requests** — access, correction, deletion and export requests for that
  administrative data are handled under *Personal data requests* in section 9.
- **Data residency** — processing and storage location is Atlassian's, and is stated in section 3.
- **Security of processing** — the measures relied on are listed in section 10.
- **No sale or sharing** — MetaSync does not sell or share personal information, and runs no
  analytics, advertising or telemetry (section 8).

MetaSync's governance reports are designed to produce evidence useful for **SOC 2**, **ISO 27001**,
**SOX** and **APRA CPS 234** access reviews. That is an evidence-gathering aid: MetaSync is not
itself certified against those frameworks, and using it does not by itself make your org compliant.

---

## 1. What Data MetaSync Accesses

MetaSync reads from Salesforce using the **Metadata API**, **Tooling API** and **REST API** at pinned API version **67.0**, over the OAuth `api` scope, as the integration user you connect.

### 1.1 Configuration metadata

MetaSync documents **41 Salesforce metadata types**:

Objects · Fields · Record Types · Validation Rules · Flows · Apex Classes · Apex Triggers · Profiles · Permission Sets · Permission Set Groups · Muting Permission Sets · Roles · Reports · Report Types · Dashboards · Workflow Rules · Approval Processes · Assignment Rules · Sharing Rules · Custom Labels · Custom Settings · Custom Metadata Types · Global Value Sets · Field Sets · List Views · Layouts · Lightning Pages · Quick Actions · Custom Tabs · Custom Applications · Auth Providers · Connected Apps · External Client Apps · Named Credentials · Remote Site Settings · Queues · Public Groups · Email Templates · Lightning Web Components · Aura Components · Setup Audit Trail.

Most of these can be enabled or disabled individually on the **Metadata types** tab in the
MetaSync admin. Two are published as part of the sync and have no toggle of their own: Custom
Settings and Global Value Sets. Setup Audit Trail has no toggle under its own name either, but
it is not untoggleable: it is controlled by the **Change Timeline** toggle, which is the only
thing that reads it. Turning Change Timeline off stops MetaSync reading the Setup Audit Trail.

Alongside them it publishes **4 further documentation pages**: Data Dictionary, Coverage Score
and Data Security, which aggregate the types above rather than mapping to a Salesforce type;
and Change Timeline, which does map to one — it is the published form of the Setup Audit Trail
type named in the list above, not an aggregate of the others. All four appear as toggles on the
Metadata types tab.

The Metadata types tab therefore shows **43 toggles**: 39 Salesforce metadata keys plus those
4 documentation pages. The 43 and the 41 count different things and neither is a typo. Of the
41 documented types, 38 have a key of their own; the 39th key (Flow Definitions) drives
inactive-flow detection rather than publishing pages of its own. The three types without a key
of their own are Custom Settings and Global Value Sets, which have no toggle at all, and Setup
Audit Trail, which is toggled by the Change Timeline page named below.

**Installed Packages** is not a page type and has no scope toggle — it is one of the
governance reports, built only when you build a governance snapshot.

The underlying Salesforce entities read include `CustomObject`, `CustomField`, `EntityDefinition`, `FieldDefinition`, `ValidationRule`, `RecordType`, `Flow`, `FlowDefinition`, `ApexClass`, `ApexTrigger`, `ApexCodeCoverageAggregate`, `Profile`, `PermissionSet`, `PermissionSetGroup`, `MutingPermissionSet`, `ObjectPermissions`, `FieldPermissions`, `Report`, `ReportType`, `Dashboard`, `Folder`, `WorkflowRule`, `ProcessDefinition`, `AssignmentRule`, `SharingRules`, `Layout`, `FlexiPage`, `QuickAction`, `CustomTab`, `CustomApplication`, `FieldSet`, `ListView`, `GlobalValueSet`, `ExternalString` (custom labels), `AuthProvider`, `ConnectedApplication`, `ExternalClientApplication`, `ExtlClntAppOauthSettings`, `ExtlClntAppGlobalOauthSettings`, `ExtlClntAppOauthConfigurablePolicies`, `NamedCredential`, `RemoteSiteSetting`, `EmailTemplate`, `Group`, `GroupMember`, `QueueSobject`, `AuraDefinitionBundle`, `LightningComponentBundle`, `InstalledSubscriberPackage`, `MetadataComponentDependency` (for change-impact analysis) and `Organization`.

### 1.2 Source code and template content (please read)

To document automation and UI components fully, MetaSync reads and **publishes into Confluence** the following content from your org:

- **Apex class and trigger source code** (`ApexClass.Body`, `ApexTrigger.Body`)
- **Lightning Web Component files** — JavaScript, HTML and CSS
- **Aura bundle files** — markup, controller, helper, renderer, style, design, SVG and documentation
- **Email template bodies** — HTML and plain text
- **Formula definitions, validation-rule formulas, flow logic, field descriptions and help text**

Individual files larger than 6,000 characters are truncated, and the page states that it has truncated them. If your Apex, components, email templates or field descriptions contain confidential logic or personal data, that content will appear on the Confluence pages MetaSync creates. Scope the integration user's permissions and choose the destination space accordingly.

### 1.3 Administrative personal data

To produce access-review and governance artifacts, MetaSync reads a limited set of **administrative personal data** about the users and administrators *of your Salesforce org*. This is configuration and access metadata about who can do what — it is **not** customer business data:

- **User records** (`User`): username, display name, email where exposed by the record, active/inactive status, and **last-login activity** (`LastLoginDate`)
- **Role, profile and permission-set assignments** (`UserRole`, `PermissionSetAssignment`, `PermissionSetGroupComponent`): which users hold which roles, profiles and permission sets
- **Access grants** (`SetupEntityAccess`, `PermissionSetTabSetting`, `AppMenuItem`): which Apex classes, applications and tabs each profile or permission set can reach
- **Licence consumption** (`UserLicense`, `PermissionSetLicense`, and the REST `/limits` resource): licence totals, used and remaining counts, and org storage utilisation
- **Audit-trail actors** (`SetupAuditTrail`): who changed what configuration, and when
- **Group and queue membership** (`Group`, `GroupMember`, `QueueSobject`)

This data is used solely to compute and document effective access (the User Access Matrix and FLS/PII reports), the governance reports listed in section 5, and change history. It is persisted as part of access and governance snapshots so that point-in-time reports can be reproduced.

MetaSync also reads and stores **Confluence account identifiers** for users and group names you explicitly add under **Additional access**, together with the role you assign each nominated user, so that non-administrators you nominate can view reports — or, where you assign them the **App admin** role, configure and operate MetaSync.

### 1.4 What MetaSync does NOT access

- ❌ Customer business records (accounts, contacts, opportunities, cases, etc.)
- ❌ File or document attachments in Salesforce
- ❌ Field *values* from business objects
- ❌ Salesforce secrets, consumer keys or stored credentials (masked, never read for display, never published)

### 1.5 Confluence

Within the site where MetaSync is installed, the app:

- Creates, updates and reads documentation pages in the space you select
- Uploads generated **SVG diagrams** (flow diagrams and entity-relationship diagrams) as page attachments
- Creates and then deletes a temporary "MetaSync access check" page when verifying it can write to the destination space
- Reads space and page metadata so re-syncs update existing pages rather than duplicating them
- Reads the invoking user's identity and group memberships for authorisation, and — only when an administrator opens the **Additional access** picker — searches the site's user directory and group list

---

## 2. What MetaSync Stores

MetaSync stores data durably in **Atlassian Forge storage** (`storage:app`), scoped to your Confluence site. This is persistent storage that survives restarts; it is not in-memory or temporary.

| Stored data | Notes | Retention |
|---|---|---|
| Salesforce OAuth refresh token, consumer key and secret | Forge **encrypted secrets** (`storage.setSecret`); excluded from exports; never logged | Until overwritten by a reconnect, or uninstall |
| In-flight OAuth connection attempts (PKCE verifier, connected-app key/secret) | Encrypted secrets | **Auto-expire after 10 minutes** |
| Sync state, queue, and Confluence page-ID mappings | Enables idempotent re-sync | Until uninstall |
| Sync run history | Status, counts, duration, truncated error text | Rolling, **most recent 20 runs** |
| Metadata snapshots and content hashes | Drives change detection and removal detection | Until uninstall |
| Change-impact baselines and dependency graph | Attribute-level before/after values, plus per-component and per-field content hashes used to detect that something changed | Until uninstall |
| Access snapshots (per-user effective access) | Includes usernames, full names, active status, last login | Until uninstall or rebuild |
| Governance report snapshots | Point-in-time compliance evidence | Rolling, **most recent 4 snapshots** |
| Data-dictionary, link-registry, object-hub and component-count caches | Derived counts and mappings; reduces repeat Salesforce calls | Until uninstall |
| App configuration | Destination space, sync schedule, metadata selection, timezone, page structure | Until uninstall |
| Notification webhook URLs and per-channel delivery state | See section 6 | Until cleared or uninstall |
| Additional-access allow-list | Confluence account IDs and group names | Until changed or uninstall |
| Licence state | Last explicit Atlassian licence verdict, so scheduled runs can be gated | Until uninstall |

**No Salesforce business records are ever stored.**

---

## 3. Where Your Data Is Processed and Stored

MetaSync runs **entirely on Atlassian Forge**. There is no MetaSync-operated server, database, log aggregator or analytics service. Consequently:

- All app storage lives in Atlassian's infrastructure and inherits Atlassian's encryption at rest.
- All app compute runs in Atlassian's serverless runtime.
- **Data residency:** because MetaSync stores customer data only in Forge storage, it follows the data-residency configuration of your Confluence Cloud site. MetaSync does not replicate your data to any other region or provider.
- The documentation MetaSync produces is stored in **your own Confluence site**.

The only outbound connections MetaSync makes are to your Salesforce org and, if you configure them, your Slack or Microsoft Teams webhooks (section 6).

---

## 4. Who Can See What

Access inside the app is tiered, and it matters because the content includes administrative personal data:

- **Confluence site administrators** — full access: sync, configuration, governance reports, the User Access Matrix, and all exports.
- **Users you nominate as viewers** under Additional access — can view reports and download the access matrix and audit pack.
- **Users you nominate as App admins** under Additional access — can additionally do everything an administrator can do inside the app: connect or replace the Salesforce org, change the destination space and metadata scope, manage schedules, run syncs, change notification settings (which includes seeing any webhook URL already stored) and build every report. They cannot see or change who has access, including their own role — that stays with Confluence site administrators.
- Grant either role deliberately: both permit export of org-wide access and PII data.
- **Anyone who can view the documentation space** — can read the published documentation pages, and can use the **MetaSync Live View macro** when it is placed on that space. The macro exposes the synced field dictionary (including PII and data-classification flags), flow logic, the entity-relationship diagram, documentation coverage and the change timeline. The first time each viewer opens the macro, Atlassian asks them once to allow access.
- The macro is authoritative **only** on the documentation space you configured. Placed anywhere else, it falls back to the administrator/nominated-user allow-list.

**The pages MetaSync publishes are readable by anyone with view access to them, not only administrators.** Choose the destination space accordingly and restrict it if the content warrants it.

---

## 5. Reports and Exports

MetaSync generates twelve governance reports: Permission Set & Profile Assignment, Elevated Access / Risk Register, Inactive Users with Active Access, Field-Level Security / PII Access, Sensitive Data Discovery, Data Security Posture, Sharing & Visibility Summary, Documentation Coverage, Change History (Setup Audit Trail), Orphaned / Unused Config, Installed / Managed Packages, and Org Licenses & Storage.

Administrators and nominated users can download:

- **Per-user access CSV / Excel exports**, which contain `Username`, `FullName`, `IsActive`, `LastLogin`, profile, permission sets, role, and per-object and per-field permissions
- **A ZIP audit pack**, bundling the governance reports and an access review into a single evidence file

These downloads are generated on demand and delivered to the requesting user's browser (administrators, and any non-administrator you have nominated under Additional access). **Once downloaded, the file leaves MetaSync's control and becomes your responsibility to store, transmit and dispose of appropriately.** MetaSync does not transmit these files anywhere else.

---

## 6. Notification Webhooks (optional)

MetaSync can notify you when a sync fails, recovers or completes, when the Salesforce connection expires, and on an optional weekly summary. This is **opt-in and off by default**: no outbound notification request is made unless an administrator pastes a webhook URL under **Connections → Notifications**.

- **Destinations:** Slack incoming webhooks (`hooks.slack.com`) and Microsoft Teams via Power Automate "Workflows" incoming webhooks (`*.logic.azure.com`, `*.powerplatform.com`). These are the only outbound destinations besides Salesforce and the Confluence Cloud API.
- **Payload:** a status-only summary — org name, sync status, a truncated error message, run id, page counts, per-type counts and duration. It never contains Salesforce record data, credentials or documentation content. The truncated error text may include Salesforce **metadata API names** (for example an object or field name that failed to extract) — never field *values*.
- **Storage:** webhook URLs are stored in Forge storage for as long as they are configured. Clearing a URL removes it immediately; uninstalling deletes it with everything else. Webhook URLs are never written to logs. Per-channel delivery state (timestamp, ok/failed, a short error snippet) is stored so the admin UI can show failed deliveries.
- **Control:** you choose which events notify, per event, and can disable either channel at any time by clearing its URL. Delivering a message to Slack or Microsoft is a disclosure to that third party under their terms; MetaSync sends nothing further.

---

## 7. Authentication and Permissions

### Salesforce

OAuth 2.0 Authorization Code flow with PKCE (S256) and a cryptographically random state parameter. The resulting **refresh token** is stored as a Forge encrypted secret and exchanged for short-lived access tokens as needed. JWT bearer-token auth is not used.

Requested OAuth scopes are `api` and `refresh_token` / `offline_access` — nothing else. Salesforce offers no metadata-only OAuth scope, so the real safeguard is the permission set you grant the **integration user**: API Enabled, View Setup and Configuration and View Roles and Role Hierarchy, plus View All Profiles from Salesforce Winter '27 — user permissions only, with **no object permissions at all** (no read, create, edit or delete on any object, standard or custom), which is what keeps the metadata entities in section 1 the limit of what MetaSync can reach.

### Confluence

Forge `asApp()` and, for the macro access check only, `asUser()`. The app declares exactly these scopes and uses all of them:

| Scope | Why it is needed |
|---|---|
| `storage:app` | The Forge key-value store and encrypted secrets described in section 2 |
| `read:page:confluence` | Read existing documentation pages so re-syncs update rather than duplicate |
| `write:page:confluence` | Create and update documentation pages |
| `delete:page:confluence` | Remove the temporary write-verification probe page after the destination check |
| `read:space:confluence` | Resolve the destination space and its homepage |
| `read:content-details:confluence` | Required alongside the attachment scope by the create-or-update attachment endpoint |
| `write:attachment:confluence` | Upload generated flow and ERD diagrams as page attachments |
| `read:user:confluence` | Read the invoking user's identity, and search the directory for the Additional access picker |
| `read:group:confluence` | Read the invoking user's group memberships to enforce administrator gating |

No Atlassian API tokens are used in the shipped app. All connections use HTTPS/TLS in transit.

---

## 8. Sub-processors and Third Parties

| Party | Role | What reaches them |
|---|---|---|
| **Atlassian** | Sub-processor — hosting, storage, compute, logs | All app data (Forge storage), all published documentation |
| **Salesforce** | Your own system, read-only source | Nothing is sent; MetaSync only reads. Salesforce receives the API requests themselves |
| **Slack** (optional) | Recipient, only if you configure it | The status-only payload in section 6 |
| **Microsoft** (optional) | Recipient, only if you configure it | The status-only payload in section 6 |

There is no analytics provider, advertising network, error-reporting service or telemetry of any kind. MetaSync does not sell, rent or share customer data.

---

## 9. Retention and Deletion

- **While installed:** credentials, sync state, snapshots and configuration are retained so the app can keep your documentation current and reproduce point-in-time reports. Rolling caps apply as noted in section 2 (20 sync runs, 4 governance snapshots).
- **Incomplete connection attempts:** if you begin connecting a Salesforce org and never finish — for example you close the authorization tab — the connected-app key and secret held for that attempt expire after **10 minutes** and are deleted automatically, whether or not you return.
- **On reconnect:** there is deliberately no Disconnect button — a Salesforce connection is only ever **replaced, or removed entirely**. Completing the reconnect flow, against the same org or a different one, **overwrites the stored credentials in place**; the previous refresh token, consumer key and secret are not retained. To cut MetaSync's access immediately, act **in Salesforce**: revoke the app's tokens under *Connected Apps OAuth Usage*, deactivate the integration user, or delete the OAuth app you created. The refresh token is the only Salesforce credential MetaSync holds, so its next sync fails to authenticate and stops. To delete the stored credentials themselves, uninstall the app.
- **On uninstall:** MetaSync deletes all data it holds for that site — Salesforce credentials, in-flight connection attempts, sync state and page mappings, access and governance snapshots, change-impact baselines, dependency graph, caches, notification settings and configuration. This runs automatically via a Forge `preUninstall` handler.
- **Confluence pages** MetaSync has already created remain in your space after uninstall; you control their deletion.
- **Logs** generated by the Forge platform are retained under Atlassian's platform retention and used only for debugging. MetaSync writes no credentials, tokens or webhook URLs to logs.

### Personal data requests

Because MetaSync only mirrors access metadata that already exists in your Salesforce org, the authoritative record is always Salesforce. To action an access, correction or erasure request affecting an individual:

1. Make the change in Salesforce (or Confluence, for account identifiers under Additional access).
2. Run a sync, or rebuild the access snapshot, so MetaSync's stored snapshots and published pages reflect it.
3. To remove all trace immediately, uninstall the app — which deletes every stored snapshot — and delete or edit any published Confluence pages containing the data.

For help with a request, contact us at the address below.

---

## 10. Security Measures

- ✅ **Encryption at rest** — Salesforce credentials stored as Forge encrypted secrets; all other data encrypted at rest by Atlassian
- ✅ **HTTPS/TLS only** — all connections encrypted in transit
- ✅ **One-way, read-only to Salesforce** — no write-back path exists in the code
- ✅ **Metadata only** — no access to customer business records
- ✅ **Least privilege** — only the granular Confluence scopes listed in section 7, all of which are used
- ✅ **Administrator gating** — sync, configuration and access-report actions require Confluence site administrator group membership, verified server-side on every call
- ✅ **Licence gating** — background scheduled work is gated on the stored Atlassian licence verdict, not only the UI
- ✅ **Secret masking** — Salesforce consumer keys, secrets and credentials are never published to Confluence and never logged
- ✅ **Injection defence** — all Salesforce-derived content is escaped before it reaches Confluence storage format; CQL input is sanitised; SOQL takes no free-text client input
- ✅ **No third-party tracking** — no analytics, advertising or telemetry

---

## 11. Your Responsibilities

By using MetaSync, you agree to:

1. Maintain control of the Salesforce OAuth credentials you connect
2. Grant the connected Salesforce integration user only the user permissions it needs (API Enabled, View Setup and Configuration, View Roles and Role Hierarchy, plus View All Profiles — required from Salesforce Winter '27, which otherwise hides other users' profiles — and optionally Modify Metadata and Author Apex) — and no object permissions at all: MetaSync needs no read, create, edit or delete on any object
3. Choose and restrict the Confluence space documentation is published to — it will contain administrative personal data about your org's users, and may contain your Apex and component source code
4. Grant **Additional access** deliberately, understanding it permits export of org-wide access and PII data
5. Handle downloaded exports (CSV, Excel, ZIP audit packs) in line with your own data-handling policies
6. Comply with your organisation's data governance obligations, and with Salesforce's and Atlassian's terms
7. Notify us promptly of any suspected security issue

---

## 12. Changes to This Policy

We may update this policy as the app changes. Material changes are reflected in the "Last Updated" date above, and the current version is published with the app's Atlassian Marketplace listing.

## 13. Contact

Questions about privacy, security, or to request a DPA:

- 📧 **Email:** support.metasync@maashive.app

---

**In short:** MetaSync reads Salesforce *metadata* — including limited administrative data about your org's users, roles, permissions and configuration-change history, and the source of your Apex and Lightning components — and publishes it as Confluence documentation. It stores credentials encrypted and snapshots durably in Atlassian Forge storage, runs no servers of its own, never touches your business records, never writes back to Salesforce, and deletes everything it holds when you uninstall.
