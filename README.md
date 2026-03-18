<p align="center">
  <img src="lolfsaas_logo.png" alt="LOLFSaaS" width="100">
</p>

<h1 align="center">LOLFSaaS</h1>
<h3 align="center">Living off Free SaaS</h3>

<p align="center">
  A curated directory of <b>125 SaaS platforms</b> with free tiers, documenting abuse surface, OPSEC profiles, detection patterns, C2 framework mappings, and operational limits for security research.
</p>

<p align="center">
  <a href="https://lolfsaas.github.io"><img src="https://img.shields.io/badge/Live_Site-lolfsaas.github.io-10b981?style=for-the-badge" alt="Live Site"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platforms-125-3b82f6?style=flat-square" alt="Platforms">
  <img src="https://img.shields.io/badge/C2_Frameworks-124-dc2626?style=flat-square" alt="C2">
  <img src="https://img.shields.io/badge/Exfil_Tools-122-f97316?style=flat-square" alt="Exfil">
  <img src="https://img.shields.io/badge/References-284-a78bfa?style=flat-square" alt="References">
  <img src="https://img.shields.io/badge/Categories-11-eab308?style=flat-square" alt="Categories">
</p>

---

[lolfsaas.github.io](https://lolfsaas.github.io/)

## Why LOLFSaaS?

Threat actors increasingly abuse legitimate SaaS platforms for phishing, C2, exfiltration, and payload hosting because the traffic blends with normal business activity. Defenders need to know which services are abused and how. Red teamers need to pick the right platform for the job without guessing.

LOLFSaaS provides structured, per-platform intelligence across **30+ fields** so you can answer questions like:

- Which platforms let me sign up with no email, no credit card, nothing?
- Which trusted domains support C2 with known framework implementations?
- What rate limits constrain my beacon interval on Telegram vs Discord vs Slack?
- Does the platform log my activity? Will a SOC flag it? How fast will I get banned?
- Can I bring my own domain? Does it support domain fronting or CDN redirection?

Every entry is cross-referenced with [lolc2](https://lolc2.github.io), [lolexfil](https://lolexfil.github.io), and the [LOTS Project](https://lots-project.com), and backed by **284 references** from threat intelligence reports and security research.

---

## Quick Stats

| Metric | Count |
|:---|---:|
| Total platforms | 125 |
| Trusted domains | 79 |
| Zero-signup services | 19 |
| Custom domain support | 42 |
| Domain fronting / CDN redirection | 6 |
| C2 framework implementations linked | 124 |
| Exfiltration tool mappings | 122 |
| Platforms with detection patterns | 69 |
| MITRE ATT&CK mappings | 125 |
| Threat intel references | 284 |

---

## Coverage

### 11 Categories

| Category | Count | Examples |
|:---|---:|:---|
| C2 Channel | 43 | Telegram, Discord, Slack, Teams, Graph API, Notion, Airtable, OpenAI |
| Cloud | 19 | AWS, Azure, GCP, Cloudflare, Vercel, Netlify, Render, Firebase, Supabase |
| Phishing | 17 | Google Forms/Sites, DocuSign, Canva, Loom, Calendly, LinkedIn, Figma |
| Storage | 14 | Mega, Box, Wasabi, Backblaze B2, GoFile, Mediafire, iCloud, Filebin |
| Paste | 7 | Pastebin, Rentry.co, ZeroBin/PrivateBin, Termbin, paste.ee, Sprunge |
| DevOps | 6 | GitHub, GitLab, Bitbucket, Azure DevOps, Gitee, Codepen |
| Business App | 6 | Salesforce, ServiceNow, HubSpot, ClickUp, Trello, Evernote |
| Email | 5 | SendGrid, Amazon SES, Twilio, Mailgun, Mailchimp |
| Website Builder | 3 | Wix, WordPress.com, Webflow |
| Redirector | 3 | Bitly, TinyURL, Rebrandly |
| SSO Target | 2 | Okta, Azure AD / Entra ID |

### Top C2 Framework Counts (via lolc2)

| Platform | Frameworks |
|:---|---:|
| Discord | 12 |
| Telegram | 10 |
| Slack | 10 |
| Microsoft Graph API | 7 |
| Azure | 5 |

### Top Exfil Tool Counts (via lolexfil)

| Platform | Tools |
|:---|---:|
| AWS (S3/Lambda/SES) | 16 |
| Azure (Functions/Blob/CDN) | 14 |
| Wasabi | 11 |
| Backblaze B2 | 10 |
| Google Cloud | 8 |

---

## Data Model

Every entry carries **30+ fields** across these groups:

### Identity & Access

`name` · `url` · `category` · `provider` · `signup` · `signupTime` · `verification` · `domains[]` · `trustedDomain` · `lastVerified`

### Abuse Surface

`abuse.phishing` · `abuse.c2` · `abuse.exfil` · `abuse.payload` · `abuse.creds`

### OPSEC Profile

`opsec` (low/medium/high) · `opsecNotes` · `socDetection` (likely/moderate/unlikely) · `banRisk` (low/medium/high) · `banNotes` · `trust` (high/medium/low/none)

### Infrastructure

`domainFronting` · `domainFrontingNotes` · `customDomain` · `customDomainNotes` · `apiEndpoints[]`

### Operational Limits

`rateLimits` · `maxFileSize` · `dataRetention` · `logging`

### Free Tier

`freeTier.type` (free/trial/none) · `freeTier.devAccount` · `freeTier.trialDays` · `freeTier.limits`

### Auth Protocols

`sso.saml` · `sso.oidc` · `sso.scim` · `sso.oauth` · `sso.mfa` · `sso.notes`

### Cross-References

`knownC2[]` (name + url from lolc2) · `exfilTools[]` (name + url from lolexfil) · `mitre[]` · `refs[]` (title + url) · `detection[]`

---

## Features

**Search** - full-text across all fields: names, domains, notes, MITRE techniques, SSO details

**Filters** - category chips, abuse type toggles, OPSEC level, signup type, auth protocols, trusted domain only, domain fronting only, has C2 frameworks

**Sorting** - ordinal sorting for risk columns (HIGH > MED > LOW), alphabetical for text, count-based for C2 frameworks and exfil tools

**Detail overlay** - click any row to open a full-screen view with all fields, shareable via unique URL hash (e.g. `#Cloudflare-(Workers%2FPages%2FR2%2FTunnels)`)

**Share links** - every service has a direct URL you can share or bookmark

**Contribute** - pre-filled GitHub issue template per service for community updates


---
## Data Sources

| Source | Contribution |
|:---|:---|
| [lolc2](https://lolc2.github.io) | 35 services with 124 C2 framework implementations |
| [lolexfil](https://lolexfil.github.io) | 122 tool-to-service links across 35 platforms |
| [LOTS Project](https://lots-project.com) | 19 trusted domain entries cross-referenced |
| Vendor documentation | Pricing pages, SSO docs, API docs per platform |
| Threat intelligence | Reports from Symantec, Fortinet, NVISO, Cofense, Check Point, CYFIRMA, Intel 471, SANS ISC, HC3/HHS, Dark Reading, Proofpoint, Darktrace, Microsoft, AdGuard, and others |

---

## License

MIT

---

<p align="center">
  <sub>Community contributions welcome.</sub>
</p>
