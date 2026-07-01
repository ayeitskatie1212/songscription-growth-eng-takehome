# Songscription — Growth Engineer Take-Home

**Time budget: 4–5 hours.** Due within 5 days of receiving it.

A few notes before you start:

- **The data isn't real.** The user profiles are made up for this exercise.
- **Use of AI:** Please feel free to use AI throughout, but always be sure to sense check the output, as you will be responsible for explaining it. Please submit the prompts you used for AI models too, as part of your assignment.
- **Confidentiality:** By taking this assignment, you agree to not share the details or answers outside the confines of the work. You agree to full confidentiality.

Good luck.

## Background

Songscription turns any audio into playable sheet music. Think Shazam, but you get a score you can play.

We have over 500K registered users across 180+ countries, thousands of paying subscribers, and we're growing fast. Our core problem: free-to-paid conversion sits under 1%, and our top churn reason is "transcribed one song and left."

One thing worth knowing. Our users don't only transcribe songs they already know. A real chunk of them upload their own recordings, compositions, demos, improv sessions, and use us to get sheet music of their own work.

You've got a dataset of around 460 users. Figure out what's actually going on, then build something about it.

## The dataset

`data/songscription_users.csv`

| Field | Description |
| --- | --- |
| `user_id` | Unique user identifier |
| `signup_date` | Date of account creation |
| `plan` | free, plus, or pro |
| `transcription_count` | Total transcriptions completed |
| `last_active_date` | Last date the user was active |
| `acquisition_channel` | How they found us: google_search, ai_search, direct, social, referral |
| `cancellation_reason` | Why they left (null if still active or converted) |
| `converted_to_paid` | Boolean — did they ever upgrade? |
| `second_transcription_within_48h` | Boolean — did they complete a second transcription within 48 hours of signup? |
| `has_recording_upload` | Boolean — did they ever upload an original recording (vs. a known song)? |
| `songs_transcribed` | Pipe-separated list of songs or recordings they transcribed |

## Part 1: Diagnose (1 to 1.5 hours)

Dig into the dataset and find two or three key insights. Then, prioritize the insights to identify the most important one (the one thing that, if you acted on it, would move conversion or retention the most).

Deliver:

- The code or queries you used (Python or SQL whatever you prefer, just make it runnable)
- The prompts you used to interact with AI models (if relevant)
- The output including any data visualizations 
- 2–3 sentences: what you found, why it matters, what you'd do with it and your next steps based on the analysis

One rule: don't summarize the dataset. We want key insights, not a tour of the data.

One more thing. Flag anything that doesn't fit your model. Outliers, anomalies, things that should be true but aren't. If you can't explain something, say so. We'd take honest uncertainty over a confident wrong answer.

## Part 2: Propose, rank, and build (about 3 hours)

Now do something about what you found. This part shows us how you go from a finding to a thing a real user sees.

Our site is live at [songscription.ai](https://songscription.ai). Use it as your reference for how we look. You do not need to rebuild any of our existing screens. You're only building the new thing you come up with, the banner or nudge or landing page or email, as a standalone piece that could sit inside our product or be sent to our users.

**First, propose a set of interventions and rank them.**

List the changes you'd make to the site or the flow as a result of your findings in Part 1. Give us a handful, ranked, with a sentence or two on each: what it is, where it sits in the funnel, and why it's ranked where it is. Tell us what would change your mind about the order.

Levers can live anywhere in the funnel. Here are some examples of levers you can pull:

- An in-app prompt after a user's first transcription, nudging them toward a second.
- A landing page aimed at the segment that converts best.
- A referral program.
- Programmatic SEO landing pages.
- A new email campaign.
- An A/B test on the pricing page.

**Then build one.**

Pick the one you'd ship first and build it for real, enough that we can click through it and understand it. Show the thinking, not just the final output:

- If it's a nudge, or a set of them: how each one looks, when it fires, and how the wording or the surrounding context shifts based on what the user's been doing.
- If it's an email: the email itself, and who gets it when, and the code to send them at scale.
- If it's an A/B test, or two: what each variant is, what you're measuring, and what result would make you ship it.

Make sure it's clear where this would go in the product, either by describing it or by showing us in screenshots of our existing product. If your change needs new features to support it, explain those too.

If your intervention is one piece of a bigger change to the user journey, walk us through that fuller journey and what impact you'd expect it to have.

Then, wire up a backend to track how your change performs. Fire an event on the key user action, capture something like click-through rate, and store it in a small endpoint, PostHog's free tier, or a Supabase table.

Wrap up with a few sentences: what you'd measure to know it worked, roughly how much lift you'd expect, and how you'd run the test.

**Note:** We are looking for a fully wired frontend and backend here. The build itself doesn't have to be large, but it must showcase both coding and UX/UI skills grounded in user insights. 

### What we care about

The choice and the ranking matter as much as the build. Why this one over the rest, and why in that order? That tells us how you think about where to spend effort.

The copy has to be clear and land with the people you're aiming at. We want something polished, not a rough sketch.

The output has to include a fully developed front end and backend (not just a front end wireframe)

It's a real product surface, so make it look right. Match the look and feel of our site. Think about the empty state, the hover, what happens while something loads or when it breaks. A CTA should make someone want to click, not scare them off.

### What you can skip

- **Login.** Don't build auth, it's a time sink. One user. Mock any user data you need.
- **Our existing screens.** Don't rebuild what's already on the site. Just build your new piece and show where it slots in.
- **Trying to build too many things.** We'd rather see a polished version of one thing, and clear thinking behind it.

### Getting started

The starter is **Next.js 15 (App Router) + TypeScript + Tailwind**.

```bash
npm install
npm run dev
```

Runs at [http://localhost:3000](http://localhost:3000). Rip out the starter page and build over it.

Push it to [Vercel](https://vercel.com) for free and send us the live link. Do whatever you want with the project: move it around, swap Tailwind for something else, pull in shadcn / MUI / Mantine, add any library you'd like.

## How to submit

Create a **private** GitHub repo and add **`ayeitskatie1212`** and **`AndrewCarlins`** as collaborators. Then email **[andrew@songscription.ai](mailto:andrew@songscription.ai)** with the repo link, including:

- Your Part 1 analysis: code, output, and written finding.
- Your ranked list of interventions and which one you built.
- Your Part 2 build: runnable, plus the live link and screenshots.
- The prompts you used for AI models.

We'll schedule a call to go over the take-home and your thought process within 48 hours of submission.

## What we're looking for

We're not grading on perfection. We want:

- A specific, non-obvious finding in Part 1. Not "free users transcribe less than paid users."
- A ranked set of interventions that follows from that finding, with a clear reason for the order.
- A build that runs, reflects your Part 1 finding, and shows real design judgment.
- Honest uncertainty where the data is ambiguous.
