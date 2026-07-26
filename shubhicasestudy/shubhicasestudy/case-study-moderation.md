# Moderation – Trust & Safety Redesign

**Role:** Product Designer (Lead)
**Company:** Genuin
**Scope:** End-to-end UX for the moderation experience across the Brand Control Center
**Timeline:** ~2–3 weeks

---

## Context & Challenge

B2B video communities face a unique tension: maintaining platform-wide safety while allowing individual brands to enforce custom policies, and empowering local communities to filter for relevance. As I looked at how the existing three-stage moderation system worked, I identified a key risk for the interface layer: without a deliberate design response, moderators would face a "black box" experience — content getting flagged or removed with no visible reasoning, and no way to know whether AI or a real user had made the call.

This wasn't a stated requirement — it was a UX problem I identified early, and one that shaped a specific ask I brought to the data science team: every flag needed to carry its evidence and reasoning forward into the interface, not just a verdict.

The system needed to scale across three very different stakeholders, each with different needs and levels of technical context:

- **Platform Admins** — enforcing baseline safety (nudity, violence, hate speech, self-harm).
- **Brand Ops** — enforcing brand-specific guidelines (tone, messaging, self-promotion rules).
- **Community Moderators** — enforcing relevance and community-specific standards.

The underlying system moderates content across two channels simultaneously: **visual** (analyzing video frames for nudity, violence, and other imagery violations) and **audio/transcript** (analyzing spoken content for hate speech, harassment, and brand-guideline violations). A single video could be flagged on either channel, both, or neither — and the interface needed to represent that clearly rather than collapsing it into one generic "flagged" state.

## Goals

1. Make moderation decisions scalable without requiring a human to review every piece of content from scratch.
2. Eliminate the "black box" experience — moderators and brands needed to understand *why* something was flagged, not just that it was.
3. Support three distinct stakeholder groups with one coherent system, rather than three disconnected tools.

## Design Process

**Framing the problem**

This module started from a system-level requirement — support platform, brand, and community-level moderation without overwhelming three different stakeholders. My first move was recognizing that the underlying AI logic (hierarchical, three-stage: Platform → Brand → Community) could easily produce a black-box experience if exposed carelessly. I pushed for the data science team's flagging system to carry structured evidence — which clip, which frame, which transcript excerpt, and why — specifically so the interface could show it, rather than just showing a verdict. That requirement shaped how I then designed the actual review screens: evidence-first, reasoning visible, human judgment always the final step.

**Balancing automation with human judgment**

Every piece of content is flagged automatically — the system runs a moderation pass every 24 hours — but the final decision to keep or remove content always stays with a human. AI never auto-removes; it surfaces, explains, and queues. I designed the review popup to show a moderator exactly what the AI saw and why: a timestamped clip of the flagged moment, a thumbnail of the specific frame (for visual flags) or the highlighted transcript excerpt (for audio flags), and the specific violation reasoning underneath (e.g. "Contains language promoting discrimination or hate against individuals or groups").

**Severity communicated through guideline tags, not a hidden score**

Rather than giving moderators an opaque confidence number, I represented severity through color-coded tags tied directly to the three-layer framework — Platform, Brand, Community — shown right on the flagged item. A moderator can tell at a glance which layer of judgment triggered the flag, and content flagged at multiple layers shows multiple tags stacked together.

## Solution

**The queue.** Moderators land on a table of flagged content — post, comment, user, group, or community — showing reported time, who or what flagged it (AI or specific users), content type, report count, a thumbnail, the guideline violated, and the stated reason. Everything is scannable without opening anything; a persistent banner reminds moderators that AI moderation runs every 24 hours, so they understand the rhythm of what they're reviewing.

**The review popup.** Clicking a flagged item opens the video with a side panel split into Post Report, Comment Report, and Video Details tabs (only showing the tabs relevant to that piece of content). Inside, an "AI flagged this video" section — expanded by default — walks through each flagged moment chronologically, with evidence attached to each one — each flagged moment is labeled by which channel triggered it (visual or audio), since a nudity flag on-screen and a hate-speech flag in the transcript require the moderator to look at completely different evidence to make a judgment call. A separate "User flagged this video" section shows what real users reported, so a moderator can see whether AI and human judgment agree or conflict before deciding. The action itself is a simple binary: Keep Post or Delete Post, with a confirmation step on delete.

**Bulk actions.** For moderators facing real volume, I added bulk-select with the same Keep/Delete actions applied across multiple flagged items at once — a direct response to the decision-fatigue problem, since not every flagged item needs individual deep review.

**History, without duplicate noise.** If a single post was reported multiple times — by AI and several users — taking one action clears all associated reports at once, and History shows a single consolidated entry rather than one row per report. This mattered because without it, a popular flagged post could clutter the queue with what looks like several separate decisions when it's really one.

## Reflection

The AI detection layer isn't perfect, and I designed with that assumption rather than around it. Brand guidelines are collected as free text, so vague guidelines can be under-enforced; sarcasm, irony, and coded language can slip past both the transcript and visual analysis; and subtle or indirect violations — like disguised competitor promotion — are the hardest category to catch automatically.

Because I couldn't design around perfect detection, the interface leans on **transparency over automation** — showing moderators exactly what evidence triggered a flag mattered more than trying to make the AI's judgment invisible or infallible. If I extended this further, I'd want a feedback loop where a moderator overriding an AI flag helps refine brand guideline specificity over time, rather than the same ambiguous guideline producing the same missed or over-flagged content indefinitely.

---

*Open items — fill in once available: usage/impact data (review time, moderator feedback, adoption), supporting screens/visuals for the case study layout.*
