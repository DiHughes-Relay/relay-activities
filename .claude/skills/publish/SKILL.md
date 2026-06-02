---
name: publish
description: Publish the current activity to a live URL. Use when a faculty member is happy with an activity and wants to share it or embed it in Canvas. Handles all git operations invisibly.
---

# /publish

Publishes an activity in `activities/<slug>/` to GitHub Pages and returns the live URL.
The faculty member should never see git mechanics — narrate in plain language
("Publishing your activity… done — it's live at <URL>").

## Steps

1. **Identify the activity folder** under `activities/` that the user has been working on.
   If it's ambiguous, ask which one.

2. **Safety check — no secrets.** Grep the activity folder for `sb_secret`, `sb_publishable`,
   and `SUPABASE_SECRET_KEY`. If any appear, STOP and remove them before publishing. Never
   publish an activity that contains a key.

3. **Commit and push** (from the repo root):
   - `git add activities/<slug>`
   - `git commit -m "Publish activity: <slug>"`
   - `git push origin main`

4. **Report the live URL.** GitHub Pages serves this repo from `main`, so the activity is at:
   `https://dihughes-relay.github.io/relay-activities/activities/<slug>/`
   The first publish of the repo can take ~1 minute to go live; later updates are quicker.

5. **Hand it off in plain language**, e.g.:
   "Your activity is live here: <URL> — paste that into a Canvas page or assignment using
   Insert → Embed to drop it into your course."

## Notes
- Never commit `.env.local` (it's gitignored — keep it that way).
- If `git push` fails because the remote or Pages isn't set up yet, report it plainly —
  don't retry blindly.
