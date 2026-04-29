# Meet-Me

> **Pattern 1 of 2.** This repo sketches the *public, manual* version of agent-to-agent meeting coordination. The *authenticated, sandboxed* version lives in [The-Lobby](https://github.com/danielrosehill/The-Lobby). They're two halves of the same idea.

The setup: an AI agent is reading email on behalf of its human. It opens a message from someone whose signature ends with:

> 🤖 **AI Agent?** [joesoap.com/agents.md](https://joesoap.com/agents.md)

The agent realises *"wait — I'm an agent, and the sender has published a skill telling me how to book on behalf of my human."* It fetches the file, follows the meeting-coordination skill, books a time, reports back. No human touches a Calendly link. No "does Tuesday work?" email thread.

That's it. That's the pattern.

## Why bother

The pain point isn't novel — it's the same one Calendly, Doodle, group polls, and "let me check with my team" threads have all swung at. The bet here is that **agents reading email on the recipient's behalf are about to become common**, and the cleanest place to give them instructions is a structured file the sender already owns.

## What's in this repo

| File | What it is |
|---|---|
| [`index.html`](./index.html) | Wireframe of Joe Soap's email with the new signature line. Open it in a browser. |
| [`agents.md`](./agents.md) | The skill definition Jane's agent fetches — calendar links, working hours, travel windows, delegated inboxes, hard rules. |
| [`agents.json`](./agents.json) | Same content, structured. Easier for an agent to parse deterministically. |

## The nested-skill pattern

`agents.md` doesn't have to be one giant file. The sane shape is a **hub at the top level** that lists the principal's skills and links to a dedicated file per skill:

```
joesoap.com/
├── agents.md                          ← hub: who Joe is, what skills exist
└── agents/
    ├── meeting-coordination.md        ← how to book a meeting
    ├── press-inquiry.md               ← how to route a press request
    ├── intro-request.md               ← how to ask for an introduction
    └── support-routing.md             ← how to route customer support
```

The hub `agents.md` then says, in effect:

> "If you want to book a meeting with Joe, read `/agents/meeting-coordination.md`. If you have a press inquiry, read `/agents/press-inquiry.md`. Otherwise, here's a default email."

This is `robots.txt` for inbound human coordination, with a directory of sub-files for specific tasks.

## The shape of the idea

1. A site publishes `/agents.md` (or `/.well-known/agents.md`) describing the owner's bookable skills.
2. Email signatures, business cards, and profile pages link to it.
3. Any agent acting on the recipient's behalf can fetch, parse, and act — without scraping calendar UIs or guessing availability from old threads.
4. The same convention extends to other delegated tasks: support routing, press inquiries, intro requests, etc.

## Known weakness: it's public

The pattern in this repo is **public** — anyone can read `agents.md`, including bots that probably shouldn't. That has a few sharp edges worth flagging up front:

- **Reconnaissance leakage.** A public manifest can hand a scraper Joe's working hours, travel schedule, delegated inboxes, and routing rules in one fetch. That's a gift to anyone running spear-phishing or competitive-intel pipelines.
- **No identity on the requester.** Anyone — human, well-meaning agent, abusive agent — can follow the calendar links. The pattern relies entirely on whatever protection already sits behind those links.
- **No audit trail.** If a booking shows up that Joe doesn't recognise, there's no signed record of *which agent* read the manifest and acted on it.

### Reasonable mitigations for the public pattern

You don't have to jump to the authenticated version to make this safer. Two practical layers help a lot:

1. **WAF / bot-management in front of `agents.md`.** Treat the manifest like any other endpoint that attracts scrapers: rate-limit per IP, challenge headless browsers, and serve a stripped-down version (or nothing) to known-bad ASNs. The cost of getting the file should be trivial for legit agents and annoying for scrapers.
2. **Human-in-the-loop confirmation on the booking action.** The manifest can advertise availability freely, but the *act of booking* should still require Joe's confirmation — push notification, email approval, or just a held "pending" slot until Joe taps yes. This caps the blast radius: even if someone does scrape and abuse the manifest, the worst they get is a confirmation prompt Joe ignores.

Combine those two and the public pattern is fine for most people most of the time. When you need stronger guarantees — verified identity on the requester, scoped one-shot capability, a signed transcript — that's where Pattern 2 comes in.

## The authenticated cousin

The authenticated version — where the email signature carries a *pre-authenticated, single-use link* into an ephemeral sandbox in which the two agents meet, the inviting principal grants scoped access (e.g. *read availability* + *write exactly one booking*), and both sides walk away with a signed receipt — lives in **[The-Lobby](https://github.com/danielrosehill/The-Lobby)**.

## Status

Notes and a working wireframe. **Not a spec.** I haven't done a full prior-art sweep — there may already be something close to this, and if so I'd genuinely like to hear about it. The idea felt worth writing down to spark conversation; pull requests, issues, and "this already exists, it's called X" corrections all welcome.
