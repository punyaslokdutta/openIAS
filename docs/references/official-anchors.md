# Official Anchors and Source Notes

Last reviewed: 2026-06-10.

This file is a starting source map, not a complete bibliography. Prefer official sources and scheme-specific orders when adding implementation detail.

## Fiscal and Payment Rails

| System | Source | Notes for openIAS |
| --- | --- | --- |
| PFMS | https://pfms.nic.in/ | Public Financial Management System. Anchor for payments, exchequer control, DBT, fund-flow monitoring, accounting, reconciliation, and financial reporting. |
| Controller General of Accounts | https://cga.nic.in/ | Institutional owner context for Union government accounts and PFMS-adjacent accounting functions. |
| Ministry of Finance | https://finmin.nic.in/ | Budget, expenditure, and fiscal policy context. |
| Department of Expenditure | https://doe.gov.in/ | Expenditure rules, fund release mechanisms, SNA/TSA/CNA guidance, and public finance reforms. |
| Reserve Bank of India | https://rbi.org.in/ | Treasury/banking system anchor where applicable. |

## Benefit and Identity Rails

| System | Source | Notes for openIAS |
| --- | --- | --- |
| DBT Bharat | https://dbtbharat.gov.in/ | Direct Benefit Transfer mission and scheme dashboard context. |
| UIDAI | https://uidai.gov.in/ | Aadhaar identity and authentication context. Do not store Aadhaar numbers in this repo. |
| NPCI | https://www.npci.org.in/ | APB/NACH/payment infrastructure context. |

## Procurement and Works

| System | Source | Notes for openIAS |
| --- | --- | --- |
| GeM | https://gem.gov.in/ | Government e-Marketplace for procurement of goods and services. |
| Central Public Procurement Portal | https://eprocure.gov.in/ | Tender publication and eProcurement context. |
| State eProcurement portals | State-specific | Must be modeled per state. |
| Scheme MIS systems | Scheme-specific | NREGASoft, AwaasSoft, NSAP MIS, PM-KISAN portal, and others vary by scheme. |

## Oversight and Escalation

| Institution/System | Source | Notes for openIAS |
| --- | --- | --- |
| CAG of India | https://cag.gov.in/en | Audit reports, audit mandate, accounts, guidance, and public audit context. |
| Parliament/PAC | https://sansad.in/ | Legislative and committee oversight context. |
| CPGRAMS | https://pgportal.gov.in/ | Public grievance routing for central and linked government departments. |
| RTI Online | https://rtionline.gov.in/ | Central RTI request portal. State RTI systems differ. |
| Social audit | Scheme/state-specific | Especially relevant for schemes with mandated social audit. |
| Lokayukta/Vigilance/CVC | Institution-specific | Oversight and anti-corruption escalation pathways vary by jurisdiction and matter. |

## Product Inspiration References

| Reference | Source | What to borrow carefully |
| --- | --- | --- |
| Paperclip | https://github.com/paperclipai/paperclip | Agent org charts, tickets, governance, budgets, heartbeats, and audit logs. |
| Guildly | https://www.tryguildly.com/ | Slack-style channels, PRDs, tickets, approvals, worktree-like isolation patterns, and searchable team memory. |

## Source Hygiene

- Add access date for volatile pages.
- Avoid copying long text from source pages.
- Prefer source links plus paraphrased notes.
- Mark unverified field knowledge as "field hypothesis".
- Mark estimates explicitly as estimates.

