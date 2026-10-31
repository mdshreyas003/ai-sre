# Artifact 1 — Product Requirements Document
**Product:** AI SRE (alert → verified recovery)  
**Layer:** 1 — Problem Discovery  
**Built from:** none (worksheet start)  
**Focus:** people, behaviour, outcomes (no technology, vendor, or stack names)  
**Date:** 2026-10-31 (Asia/Calcutta)  
**Team notes:** Breakout discussion + approved Q1.1–Q1.10; Q1.11–Q1.22 filled from discussion (confirm before Layer 2)

---

## Reference scenario (fixed for all later layers)
1. An organization runs a web service.  
2. An engineer deploys a new version.  
3. That deploy changes a configuration value.  
4. The service starts failing for users.  
5. Monitoring detects the incident.

---

## 1.1 Problem statement
**Questions answered:** Q1.1, Q1.3, Q1.8

When services fail, engineers cannot move from alert to verified recovery quickly and confidently. Evidence lives in many places. Ownership is often unclear. People spend most of the time gathering context, not deciding.

That delay hurts users (blocked actions), the business (trust, support load, sometimes revenue — worse when a core journey is broken), and engineers (especially overnight: low context and fatigue raise the chance of a weak or unnecessary fix that can make things worse or hide the real cause).

**We are solving:** get the right people a clear, shared picture fast, support good judgment, propose safe next steps, and prove recovery — without the platform silently changing production.

---

## 1.2 Target users
**Questions answered:** Q1.2, Q1.11

| Role | Job in an incident |
|------|--------------------|
| Service accountable owner | Owns the service outcome; often authorizes production-affecting fixes |
| On-call / investigator | Acknowledges, investigates, may be delegated to authorize |
| Second approver (high blast radius) | Extra human when the change could hurt many users or shared systems |
| Communicator | Updates users / stakeholders |
| Teammates who recently changed the area | Provide “what changed / why” context |

**Rule:** Every service should map to an owner and on-call. If mapping is missing, record that as an open gap. Check that on-call is actually reachable.

---

## 1.3 User journey
**Questions answered:** Q1.2, Q1.4, Q1.7, Q1.9, Q1.20

1. **Detect** — Monitoring raises an incident.  
2. **Acknowledge** — Right role is notified and accepts.  
3. **Judge impact** — How bad for users and business right now? (Core journey vs something that can wait.)  
4. **Assemble context** — Impact, symptoms, recent deploys/config (what/who/when), ownership, similar past cases.  
5. **Stitch the user/incident path** — Funnel for that incident, user event journey (where it broke), related event pipeline; align with change timing.  
6. **Hypothesize** — Ranked causes; mark uncertainty and missing evidence.  
7. **Propose** — Concrete fix steps + how to verify recovery.  
8. **Authorize** — Owner/on-call (and second person if high risk).  
9. **Apply (human, outside the platform)** — Person carries out the change.  
10. **Verify** — Independent checks that users and the service recovered.  
11. **Close & keep history** — Outcome stored on the incident timeline.

---

## 1.4 Core use cases
**Questions answered:** Q1.5, Q1.7, Q1.9, Q1.10, Q1.12, Q1.16, Q1.17, Q1.21

1. **Open a shared incident record** when an alert arrives.  
2. **Auto-assemble context** (impact, symptoms, changes, ownership, past similar incidents).  
3. **Stitch funnel + user event journey + event pipeline** to find where the failure appeared.  
4. **Draft ranked hypotheses** and list missing evidence.  
5. **Quiet expected warnings** for a defined time window and send a short digest (team chat or email).  
6. **Propose remediation + verify checklist**; human applies outside; record result.  
7. **Independently check recovery** (do not trust a “fixed” claim alone).  
8. **Preserve the full timeline** for learning after the incident.

**Smallest useful product (MVP):** use cases 1–7 for the reference scenario (config change → user failures), without the platform applying changes.

**Demo story:** detect → assemble → “config change” hypothesis → propose rollback/fix + checks → human applies → verify users recovered → close with record.

---

## 1.5 Product boundaries
**Questions answered:** Q1.5, Q1.6, Q1.10, Q1.13, Q1.14, Q1.19

### In scope
- Investigation support: gather, align, stitch, hypothesize.  
- Coordination: notify roles, one shared record.  
- Proposals and verify guidance.  
- Expected-warning digests with an explicit quiet window.  
- Honest behaviour when evidence is incomplete (state gaps; do not invent root cause).

### Out of scope / non-goals (see also 1.7)
- Platform applying production changes itself.  
- Replacing human severity judgment or business communication.  
- Acting as a general chatbot with no incident structure.

### Assistant vs this product
| Suggestions-only assistant | This platform |
|----------------------------|---------------|
| Explains an error | Runs structured investigation |
| One-off advice | Shared incident lifecycle |
| No ownership of verify | Tracks propose → authorize → human apply → verify |

---

## 1.6 Success definition
**Questions answered:** Q1.1, Q1.3, Q1.8, Q1.15, Q1.18

We succeed when:
- Time from alert to a shared understanding drops.  
- Time from alert to verified recovery drops for the reference class of incidents.  
- Unnecessary or harmful fixes drop.  
- Incidents more often start with a clear owner/on-call.  
- Engineers trust the system because evidence, uncertainty, authorization, and verify steps are visible.

**Trust requirements:** evidence trail; known vs unknown; human authorization for production-affecting actions; independent recovery checks; audit of recommendations; human can override or stop; no silent production changes by the platform.

---

## 1.7 Explicit non-goals
**Questions answered:** Q1.14, Q1.16, Q1.19

The product will **not**:
1. Change production by itself.  
2. Delete or destroy data.  
3. Bypass human authorization.  
4. Claim a root cause when evidence is missing.  
5. Hide uncertainty.  
6. Silently treat real user-impacting failures as “expected” without a defined quiet window and digest.  
7. Try to be every team’s full ops org chart or a generic coding assistant.

---

## When humans must step in
**Questions answered:** Q1.6, Q1.11, Q1.22

| Moment | Why |
|--------|-----|
| Severity unclear | Business/user tradeoff |
| Any production-affecting fix | Consequence / irreversibility |
| High blast radius | Need second person |
| Incomplete evidence + ongoing user harm | Judgment call |
| Competing hypotheses | Choose direction |
| External communication | Speak for the business |
| Bad-looking recommendation | Override / stop |

---

## Incomplete evidence behaviour
**Questions answered:** Q1.13

Say what is missing. Mark hypotheses as uncertain. Ask people for the gap. Keep helping with what is known. Escalate if users are still hurt. Never invent a confident root cause.

---

## Conversation log (summary)

| Q | Status | Decision (short) | Artifact section |
|---|--------|------------------|------------------|
| 1.1 | Approved | Alert→recovery is the real problem | 1.1 |
| 1.2 | Approved | Owner + on-call + four roles | 1.2, 1.3 |
| 1.3 | Approved | User / business / engineer impact; severity by journey | 1.1, 1.6 |
| 1.4 | Approved | Ack→impact→signals→changes→people→hypothesis | 1.3 |
| 1.5 | Approved+ | Automate gather/correlate/hypotheses + quiet-window digest | 1.4, 1.5 |
| 1.6 | Approved | Consequence gate: automate gather, humans decide risky acts | 1.5 |
| 1.7 | Approved+ | Funnel + event journey + pipeline stitch | 1.3, 1.4 |
| 1.8 | Approved | Wrong fix worsens harm → verify + auth are core | 1.1, 1.6 |
| 1.9 | Approved | Immediate assemble + notify; no prod change | 1.4 |
| 1.10 | Approved B | Propose + checks; human applies outside | 1.4, 1.5 |
| 1.11 | Proposed A | Owner/on-call auth; 2nd for high risk | 1.2 |
| 1.12 | Proposed | Independent recovery checks | 1.4, 1.6 |
| 1.13 | Proposed | State gaps; no fake root cause | 1.5 |
| 1.14 | Proposed | Platform = investigate + coordinate + verify track | 1.5, 1.7 |
| 1.15 | Proposed | Evidence, auth, verify, audit, override | 1.6 |
| 1.16 | Proposed | MVP = assemble→hypothesize→propose→human apply | 1.4 |
| 1.17 | Proposed | Config-change demo end-to-end | 1.4 |
| 1.18 | Proposed | Time-to-understand, time-to-recover, bad-fix rate, ownership % | 1.6 |
| 1.19 | Proposed | No self-change, no data destroy, no fake certainty | 1.7 |
| 1.20 | Proposed | Full alert→verify sequence | 1.3 |
| 1.21 | Proposed | Append-only incident timeline | 1.4 |
| 1.22 | Proposed | Human gates listed above | 1.2, 1.5 |

### Disagreements / choices that mattered
- Dual pass on Q1.1: do not shrink the problem to “faster debugging” only — keep ownership and recovery.  
- Q1.5 team add: expected-warning quiet window + digest.  
- Q1.7 team add: funnel / event journey / event pipeline stitch.  
- Q1.10 team chose **B** (propose only; humans apply outside) over apply-in-platform or auto safe-playbooks.  
- Q1.11 proposed **A** from breakout (owner/on-call + second for high risk).

---

## Provisional assumptions
| Assumption | Owner | Validate when |
|------------|-------|----------------|
| Costly pain is slow understand/recover, not alert count alone | Shreyas | 2–3 real incident timelines |
| Every service can be mapped to owner + on-call | Shreyas | Current ownership list |
| Severity should follow core user journeys | Team | Write severity examples |
| Humans apply changes outside the platform (lasting) | Team | Stakeholder confirm before Layer 2 |
| Quiet windows for expected warnings are definable | Team | List 3 known patterns |

---

## Acceptance checklist (Layer 1 PDF)
- [x] 1.1 Problem statement  
- [x] 1.2 Target users  
- [x] 1.3 User journey  
- [x] 1.4 Core use cases  
- [x] 1.5 Product boundaries  
- [x] 1.6 Success definition  
- [x] 1.7 Explicit non-goals  
- [x] Every section lists questions; all Q1.1–Q1.22 covered  
- [x] Assumptions marked provisional with owner + validation  
- [x] Major decision forks recorded  
- [ ] Team confirms Q1.11–Q1.22 proposed rows  
- [ ] Saved in team repository  

**Reviewed by:** _________________ **Date:** _________________
