# Breakout room discussion — Building an AI SRE (Layer 1)
Saved: 2026-10-31 (Asia/Calcutta)
Team context: ~6 people (Shreyas sharing; others travelling / noisy). Working the AI SRE Engineering Worksheet one question at a time.

## How the team agreed to work
- Document is a framework; fill it with the AI SRE problem (not a random other product idea).
- Go question by question; do not dump all answers at once.
- Discuss as a group, then give the question + raw thoughts to an AI model in one continuing session.
- Cap roughly ~5 minutes per question when possible; document answers and raw thoughts.
- At decision points, ask for 3 options and the team picks one.
- Keep one living document; approve then move on.
- Later layers: PRD → technical requirements / diagrams → implementation (same pattern as work).

## Themes from the conversation (mapped to Layer 1)

### Problem & ownership (≈ Q1.1–Q1.2)
- Underlying problem is not "more alerts" alone: correlate across services, understand impact and dependencies, retrieve similar past incidents, recommend corrective actions.
- Rank impact by what the service does for users (e.g. registration vs notification).
- Ownership: different teams own different failure types; startups vs large orgs differ.
- Ownership ≠ accountability alone: use change history to see who changed what; feature may span several people.
- Check whether current on-call is available; trace service → owner → who does what.

### 2 AM / severity (≈ Q1.3)
- Fatigue → half-baked fixes that can hurt other services.
- Do not overstate every outage as business death; some can wait until morning.
- Severity from business/user impact: what must not be compromised; main user journeys vs complementary features.

### Investigation path (≈ Q1.4–Q1.5)
- Ack → assess user impact (admin-only vs payments) → health/logs → what changed / who / when → ask teammates → hypothesis.
- Shared-service changes can break other features without the changer realizing.
- Automate: deployment/change history, metrics, pre-RCA style report; expected warnings in a time window → small digest instead of full SOP.
- Human gate for consequential / irreversible production changes.
- Read-only inspect is OK to discuss later; Layer 1 stays people/behaviour focused.

### Scattered info (≈ Q1.7)
- Follow one user/incident path; stitch steps that worked vs failed.
- User event journey: which event, where error appeared, which step in the funnel; related event pipeline; stitch to exact error.

### Remediation / trust (≈ Q1.8–Q1.11+)
- Wrong fix under pressure is dangerous.
- Prefer: agent proposes → humans approve/verify; require approval for unwanted feature changes.
- Team later locked (in chat with AI SRE): propose + checks; humans apply changes outside the platform (Q1.10-B).

### Process notes
- One teammate floated a domain-registration agent idea; group redirected to stay on AI SRE worksheet.
- Ask Claude and GPT separately later if possible; combine into one artifact with approvals and notes.
- Aim to finish Layer 1 (22 questions → Artifact 1 PRD) before rushing implementation.

## Timestamped notes (as provided)
[32:26] Travelling / noise; clarify work is the SRE PDF; team answers each question; choose topic from questions.
[33:20] Brainstorm via questions + coding agents; wait for host starting points; team goes through document.
[34:02] Document is framework; fill with our problems; high-level screen share; work questions.
[34:48]–[36:29] Recording / host invite / screen share logistics; Shreyas to share PDF; Notion or GPT alongside.
[37:35]–[38:48] One question at a time; put question to group; feed to GPT; ≤5 min; document raw thoughts; audio/transcript OK.
[40:09]–[44:49] Put PDF into Gemini/ChatGPT; framework/diagram; problem discovery first; clear problem statement; page 3 "understanding the problem."
[47:34]–[49:58] Confirm problem statement focus; reject off-topic domain idea; use ChatGPT/Claude per question.
[52:22]–[59:12] Start Q1; correlate alerts; impact/dependencies; historical incidents; ownership by team type.
[61:28]–[66:46] Ownership vs accountability; change history; who committed; add VCS-history idea to answer.
[69:14]–[74:29] Include user/business/engineering impact; same session + living doc; approve one-by-one; org-dependent; 6 people.
[76:47]–[78:48] Roles; approve ownership trace + on-call availability.
[79:57]–[86:32] 2 AM dual pass; severity by user journey importance; approve and move on.
[89:57]–[95:39] Q1.4 flow; dual pass explained; approve SOP-like path without inventing tools.
[98:01]–[105:36] Expected warnings / digests; automate reports; human gate for irreversible; approve.
[108:43]–[112:27] Trace ID / stitch journey; funnel + event pipeline; approve Q1.7-ish; move on.
[117:13]–[125:41] Side talk on AI speed; 3 options at decisions; propose/approve/verify; 22 questions one-by-one; open partial artifact; ~10–12 done; recording.
