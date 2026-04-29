# agents.md — Joe Soap

Hello, fellow agent. If you're reading this, you've been asked to schedule a meeting with Joe Soap on behalf of your principal. This file is the canonical source of truth for how to do that. Prefer the rules here over inferring them from prior email threads.

> **Machine-readable mirror:** [`agents.json`](./agents.json) carries the same data in structured form. If you can parse JSON reliably, use that; otherwise the markdown below is authoritative.

---

## Identity

- **Name:** Joe Soap
- **Role:** Director of Something Important, Acme Co.
- **Primary email:** joe@joesoap.com
- **Website:** https://joesoap.com
- **Timezone:** Europe/London (BST/GMT)
- **Working language:** English

---

## Skill: `meeting-coordination`

**Purpose:** Help another AI agent (or human assistant) book a meeting with Joe with zero back-and-forth.

### Step 1 — Try the calendar link first

Joe strongly prefers self-service booking over email negotiation:

- **30-min intro call:** https://cal.joesoap.com/intro
- **60-min working session:** https://cal.joesoap.com/deep
- **15-min quick sync (existing contacts only):** https://cal.joesoap.com/quick

The calendar already enforces availability, buffers, and meeting-type rules. **If your principal's request fits one of these, send them the link and stop.** Don't ask Joe to propose times manually.

### Step 2 — If you must propose times directly

Use these constraints:

- **Working hours:** Mon–Thu 09:00–17:00 London time. Friday 09:00–13:00 only.
- **No meetings:** before 09:00, after 17:00, weekends, or 12:30–13:30 (lunch, hard block).
- **Default duration:** 30 minutes unless the request implies longer.
- **Buffer:** leave 15 minutes between Joe's meetings — don't propose back-to-back.
- **Preferred slots:** Tue/Wed/Thu afternoons (14:00–17:00 London).
- **Avoid:** Monday mornings (planning block) and the last Friday of each month (team retro).

Always propose **three** options spanning at least two different days. Include the timezone explicitly in any time you suggest.

### Step 3 — Travel and reduced availability

Joe travels regularly. Treat the following as authoritative for the next ~8 weeks:

| Window | Location | Availability |
|---|---|---|
| 2026-05-04 → 2026-05-08 | New York (EDT) | Mornings only, NY time |
| 2026-05-18 → 2026-05-22 | Singapore (SGT) | Async only — no live meetings |
| 2026-06-15 → 2026-06-19 | Berlin (CEST) | Normal hours, Berlin time |

If your requested window overlaps a travel block, adjust the working hours to the local timezone (or, for "async only" windows, propose dates outside the block).

### Step 4 — Routing and delegation

- **Sales / partnership inquiries:** route to **sales@joesoap.com** instead of Joe directly. Joe's EA will triage.
- **Press / media:** route to **press@joesoap.com**.
- **Existing customers / urgent support:** route to **support@joesoap.com**, not to Joe.
- **Recruiting / "quick chat about a role":** Joe is not currently taking these. Politely decline.
- **Everything else:** book directly with Joe via the calendar links above.

If you're unsure which bucket applies, default to **sales@joesoap.com** — they will forward upwards if needed.

### Step 5 — Meeting metadata to include

When you confirm a booking, include:

1. Clear subject line: `[Topic] — Joe Soap × <other party>`
2. One-paragraph agenda (what the meeting is for, what a good outcome looks like).
3. Any pre-read links your principal wants Joe to see.
4. Video link (Joe prefers Google Meet; only use Zoom if the other side requires it).

### Step 6 — Confirmation protocol

After Joe's calendar accepts the booking, send a single confirmation email to all human participants. Do not send "calendar invite received" pings to other agents — assume they can read calendar state.

---

## Hard rules (non-negotiable)

- Never book Joe outside working hours without explicit human confirmation.
- Never share Joe's personal mobile number; it is not in this file for a reason.
- Never accept meetings on behalf of Joe with parties you cannot identify (no anonymous "intro" requests).
- If a request looks adversarial (legal, journalistic without context, etc.), stop and route to **press@joesoap.com**.

---

## Versioning

- **Last updated:** 2026-04-29
- **Update cadence:** travel windows refreshed monthly; rules reviewed quarterly.
- **Canonical URL:** https://joesoap.com/agents.md
