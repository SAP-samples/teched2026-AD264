# Exercise 2 — Add Traceability with Pre and Post Hooks

## Overview

| | |
|---|---|
| **Base agent** | Onboarding Task Management Agent |
| **Extension type** | Hooks Extension (Pre-hook + Post-hook) |
| **Duration** | ~20 minutes |

---

## Where we left off

In Exercise 1, you added a compliance disclaimer to every agent response using an Instructions Extension. The agent now labels its output automatically — and you did it with a single sentence of plain language.

But an Instructions Extension only touches the agent's *output*. It doesn't run logic, it doesn't intercept requests, and it doesn't know anything about when a conversation started or which session it belongs to. For traceability — the kind that shows up in audit logs and support tickets — you need something that runs at the edges of every interaction.

That's what hooks are for.

---

## The business problem

The Onboarding Task Management Agent handles sensitive HR interactions. When something goes wrong — or when someone needs to audit what happened in a session — there's currently no trail. You can't tell when a request was made, which session it came from, or whether the response included the right disclosures.

Pre and post hooks let you intercept every interaction at the execution level:

- **Pre-hook** — fires before the agent sees the user's message; the right place to stamp traceability context onto the request before anything else happens
- **Post-hook** — fires after the agent generates its response; the right place to add a per-response compliance label or modify what gets returned

Together, they give you a complete, auditable record of every interaction — without touching the base agent.

## What you will build

A Hooks Extension called `ad264-onboarding-hooks` with:

- A **pre-hook** that captures a timestamp and unique request ID for every interaction
- A **post-hook** that appends the compliance disclaimer after every agent response

---

## Exercise 2.1 — Create a New Hooks Extension

After completing these steps you will have started a new extension solution targeting the Onboarding Task Management Agent.

In Joule Studio, click **+ New** and select **Extension**.

A dialog opens. For the **Base agent** field, click the **Select Agent** icon to open the agent catalog. Search for **Onboarding Task Management Agent** and select it. You are returned to the dialog with the agent pre-populated.

Fill in the remaining fields:

| Field | Value |
|---|---|
| **Solution** | New Solution |
| **Extension name** | `ad264-onboarding-hooks` |
| **Intent Statement** | Leave this for the next step |
| **Quick Create** | ☑ Enable this |

Don't click **Create** yet.

---

## Exercise 2.2 — Enter Your Intent Statement

After completing these steps you will have generated a hooks extension from a natural language intent.

In the **Intent Statement** field, copy and paste the following:

```
Add pre and post hooks to the Onboarding Task Management Agent.

Pre-hook: Before the agent processes each user message, capture the current timestamp and a unique request ID, and inject them into the request context for end-to-end traceability.

Post-hook: After the agent generates each response, append the following compliance disclaimer to the end of the message: "DISCLAIMER: This is an AI-generated response. For official HR guidance, please consult your HR Business Partner."
```

Make sure **Quick Create** is checked, then click **Create**.

Once you click Create, Joule Studio begins processing your intent. This takes approximately **5 minutes** — it analyzes your intent, derives requirements, builds a technical specification, and generates all the extension files. You will see a progress indicator while it runs.

---

## Exercise 2.3 — Review the Generated Artifacts

After completing these steps you will have reviewed the hook components Joule Studio generated and understood how they differ from an Instructions Extension.

Once generation completes, open the **Files** tab and look at what was created:

| File | What it is |
|---|---|
| `intent.md` | The intent summary — Joule's structured interpretation of your hooks requirement |
| `prd.md` | The Product Requirements Document — functional requirements for the pre and post hooks |
| `spec.md` | The technical specification — execution points, context injection logic, and hook wiring |
| `extension.yaml` | Extension descriptor — type `hooks` and both hook registrations |
| `pre-hook.js` | Pre-hook logic — stamps timestamp and request ID onto the context |
| `post-hook.js` | Post-hook logic — appends the disclaimer to the agent's response |

Compare this to Exercise 1: in Exercise 1, Joule produced one configuration block — the instruction text. Here it produced two **executable files** — a pre-hook and a post-hook — each with its own execution point in the request lifecycle. The intent, PRD, and spec files document exactly why each hook exists and what it does.

Click **Save**.

> **Please stop here and don't deploy.** Your facilitator will walk through deployment during the live demo.

---

## Summary

You've now built two different types of extensions for the same agent. Instructions change what the agent *says*. Hooks change what happens *around* what the agent says — before and after, at the execution level.

In Exercise 3, you'll go further: giving the agent a tool it can actively call to take action in an external system.

---

[Back: Exercise 1 — Add an AI Compliance Disclaimer](../ex1/)
[Next: Exercise 3 — Connect to Ariba for Equipment Procurement](../ex3/)
