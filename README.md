# Relay Activities

Faculty-built interactive learning activities, grounded in the Relay teacher-skills
taxonomy and published to live URLs for embedding in Canvas.

Faculty work in the Claude Code desktop app: they describe an activity, Claude builds it
(pulling real content from the taxonomy), and `/publish` ships it to a live URL. No git or
command line required.

## Layout

```
relay-activities/
├── CLAUDE.md                     Authoring guide Claude follows when building activities
├── bin/taxonomy-fetch            Read-only access to the Relay taxonomy (authoring-time)
├── .claude/skills/publish/       The /publish skill (commit → push → live URL)
├── activities/<slug>/index.html  One self-contained activity per folder
├── .env.local.example            Template for the taxonomy credentials
└── .env.local                    Real credentials (gitignored — never committed)
```

## Setup

1. Copy `.env.local.example` to `.env.local` and paste the taxonomy secret key
   (Supabase → Project Settings → API Keys → `sb_secret_...`).
2. Test the connection: `bin/taxonomy-fetch skills`

## Status

Phase −1 demo scaffold: taxonomy connection + build-in-Claude + `/publish` to a live URL.
SDK/event contract, accessibility validation, and Canvas LTI come in later phases.
