# Layer 1 — Decisions (Q1.1–Q1.22)
Source: team approvals in chat (Q1.1–Q1.10) + breakout discussion used to fill Q1.11–Q1.22.
Status: Q1.1–Q1.10 = team-approved. Q1.11–Q1.22 = proposed from discussion (team should confirm).
Focus rule: people, behaviour, outcomes only.

## Q1.1 — Underlying problem
Engineers cannot get from alert to verified recovery quickly and confidently. Alerts are frequent; information and ownership are fragmented; time to understand and recover stays high.

## Q1.2 — Who is responsible
Map each service to an accountable owner and on-call. Separate roles: acknowledge, investigate, authorize change, communicate. Use change history to see who recently changed the failing area. If on-call is unavailable, escalate. Missing ownership is an open item, not a guess.

## Q1.3 — 2 AM outage impact
Users: blocked on important actions. Business: trust, support load, possible revenue — severity depends on how central the journey is (some issues can wait until morning). Engineers: woken, low context, fatigue → higher chance of weak fixes that can hurt more.

## Q1.4 — What engineer does before knowing cause
Acknowledge → judge user impact → pull health signals → check recent deploys/config (what/who/when) → ask teammates (shared services) → narrow/reproduce → form hypothesis. Waiting and context-switching dominate delay.

## Q1.5 — What can be automated
Automate: gather and align signals, recent changes, similar past incidents, draft hypotheses, short pre-incident report. Automate known/expected warnings for a defined quiet window and send a small digest (team chat or email). Do not automate irreversible production changes.

## Q1.6 — Repetitive vs human expertise
Repetitive: gather/align evidence without changing production. Human expertise: severity, choosing among risky options, authorizing a production change, speaking for the business. Gate on consequence and irreversibility.

## Q1.7 — Information needed for root cause
In one place: user impact + start time; funnel for that user/incident; user event journey (where the issue appeared); related event pipeline; aligned symptoms; recent deploys/config + who changed them; ownership; similar past incidents. Stitch these to pin the exact error; start with change-vs-symptom timing.

## Q1.8 — Wrong diagnosis + unnecessary fix
Can prolong or deepen user failure, create new errors, hide the real cause, waste on-call time, and hurt trust. So verification and human authorization before change are part of the product problem.

## Q1.9 — Immediate capabilities after incident
Open a shared incident record; assemble impact, symptoms, changes, funnel/journey/pipeline, ownership; draft ranked hypotheses; flag missing evidence; notify the right roles. No production change yet.

## Q1.10 — Explain → remediate (TEAM CHOICE B)
Platform proposes a concrete fix and how to check recovery. Humans apply changes outside the platform. Record the outcome (worked / did not).

## Q1.11 — Who authorizes (PROPOSED from discussion → Option A)
Service accountable owner or delegated on-call authorizes a production-affecting fix. High blast radius → second person. Platform never authorizes itself. (Matches breakout: propose then humans approve; check owner/on-call available.)

## Q1.12 — Prove repair worked (PROPOSED)
Do not trust the system’s claim alone. Independently check: user journey works again, error rate/symptoms back to normal, and the incident exit criteria the team set. If checks fail, keep the incident open.

## Q1.13 — Incomplete telemetry (PROPOSED)
Say clearly what is missing; do not invent a root cause; continue with best-effort hypotheses marked uncertain; ask humans for the missing evidence; escalate if user harm is high.

## Q1.14 — Assistant vs engineering platform (PROPOSED)
Suggestions-only assistant: explains and advises. Platform: runs investigation, keeps one incident record, coordinates roles/notifications, proposes remediation, tracks verification of recovery, preserves history. (Apply still human-outside per Q1.10-B.)

## Q1.15 — Trust (PROPOSED)
Engineers need: visible evidence trail; clear “what we know / don’t know”; human authorization for production-affecting actions; independent recovery checks; audit of recommendations; ability to override or stop; no silent production changes by the platform.

## Q1.16 — Smallest useful product in 6 months / small budget (PROPOSED)
MVP: on alert → shared incident record → assembled context (impact, changes, journey stitch) → ranked hypotheses + gaps → short digests for expected warnings → proposed fix + verify checklist for a human to apply outside. Out of MVP: platform applying changes; broad multi-org features.

## Q1.17 — End-to-end demo (PROPOSED)
1) Deploy changes a config → users fail. 2) Monitoring detects → platform opens incident. 3) Assembles timeline + journey stitch + ownership. 4) Ranks “bad config change” hypothesis. 5) Proposes rollback/fix steps + verify checks. 6) Human applies outside. 7) Platform (or human with platform checks) confirms users recovered → close with record.

## Q1.18 — Measurable outcomes (PROPOSED)
Time from alert to shared understanding; time from alert to verified recovery; rate of unnecessary or rolled-back fixes; % incidents with clear owner at start; % incidents with complete evidence pack; engineer satisfaction / trust score after use.

## Q1.19 — Explicitly prohibit (PROPOSED)
Platform must not: change production by itself; delete or destroy data; bypass human authorization; claim root cause when evidence is missing; hide uncertainty; silently dismiss real user-impacting alerts as “expected” without a defined quiet window and digest.

## Q1.20 — Full sequence alert → recovery (PROPOSED, reference scenario)
Receive alert → create incident → map owner/on-call → assemble impact + symptoms + recent config/deploy change + user journey/pipeline stitch → draft hypotheses → notify roles → propose remediation + verify steps → human authorizes and applies outside → run independent recovery checks → if good, close and preserve record; if not, reopen investigation with new evidence.

## Q1.21 — Preserve information (PROPOSED)
Keep one incident timeline that appends: alerts, assembled evidence, hypotheses, decisions, proposed actions, who authorized, what human applied, verify results, final outcome. Do not overwrite; mark updates. Exportable for later learning.

## Q1.22 — When humans must step in (PROPOSED)
Human required at: severity call when impact unclear; authorizing any production-affecting fix; high blast radius (second person); incomplete evidence with ongoing user harm; disagreement between hypotheses; communication to users/business; stopping the platform if recommendations look wrong.
