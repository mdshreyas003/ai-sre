# Layer 1 Conversation Log (PDF fill-in)

| Questions | Agent | Decision reached | Open unknowns and owner | Artifact section |
|-----------|-------|------------------|-------------------------|------------------|
| Q1.1 | AI SRE + team | Core problem = alert → verified recovery too slow/uncertain | Worst pain mode — Shreyas | 1.1 |
| Q1.2 | AI SRE + team | Owner + on-call; 4 roles; change-history for who touched it | Org ownership map — Shreyas | 1.2, 1.3 |
| Q1.3 | AI SRE + team | User/business/engineer impact; severity by journey importance | Service criticality list — Team | 1.1, 1.6 |
| Q1.4 | AI SRE + team | Ack → impact → signals → changes → people → hypothesis | Timing of each step — Shreyas | 1.3 |
| Q1.5 | AI SRE + team | Automate gather/correlate/hypotheses + quiet-window digest | Known expected patterns — Team | 1.4, 1.5 |
| Q1.6 | AI SRE + team | Automate gather; humans for consequence | Past regret cases — Team | 1.5 |
| Q1.7 | AI SRE + team | Funnel + journey + pipeline stitch + changes + ownership | Completeness of event trail — Team | 1.3, 1.4 |
| Q1.8 | AI SRE + team | Wrong fix deepens harm → verify+auth core | Frequency of bad fixes — Shreyas | 1.1, 1.6 |
| Q1.9 | AI SRE + team | Immediate assemble + notify; no prod change | Speed target — Team | 1.4 |
| Q1.10 | AI SRE + team (B) | Propose + checks; human applies outside | Allowed remediations list — Team | 1.4, 1.5 |
| Q1.11 | Proposed A | Owner/on-call; 2nd if high risk; platform never self-auth | Confirm A vs C — Team | 1.2 |
| Q1.12 | Proposed | Independent recovery checks | Exit criteria examples — Team | 1.4, 1.6 |
| Q1.13 | Proposed | State gaps; no fake root cause | What telemetry is always present — Team | 1.5 |
| Q1.14 | Proposed | Platform investigates, coordinates, tracks verify | Naming in pitch deck — Team | 1.5, 1.7 |
| Q1.15 | Proposed | Evidence, auth, verify, audit, override | Trust pilot plan — Team | 1.6 |
| Q1.16 | Proposed | MVP = assemble→hypothesize→propose | 6-month cut line — Team | 1.4 |
| Q1.17 | Proposed | Config-change demo path | Demo script owner — Shreyas | 1.4 |
| Q1.18 | Proposed | Time-to-understand/recover; bad-fix rate; ownership % | Baseline numbers — Team | 1.6 |
| Q1.19 | Proposed | No self-change / data destroy / fake certainty / silent dismiss | Policy sign-off — Team | 1.7 |
| Q1.20 | Proposed | Full sequence alert→verify | Align with scenario — done | 1.3 |
| Q1.21 | Proposed | Append-only incident timeline | Retention rules — Team | 1.4 |
| Q1.22 | Proposed | Human gates listed in PRD | Train on-call on gates — Team | 1.2, 1.5 |

### Where dual passes / options disagreed
- Q1.1: recovery+ownership vs “debugging speed only” → kept recovery+ownership.  
- Q1.10: A apply-in-platform / B propose-only / C auto safe-playbooks → **chose B**.  
- Q1.11: A owner+2nd / B on-call alone / C always two → **proposed A** (confirm).
