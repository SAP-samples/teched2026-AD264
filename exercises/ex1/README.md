# Exercise 1 — Add an AI Compliance Disclaimer

## Overview

| | |
|---|---|
| **Base agent** | Onboarding Task Management Agent |
| **Extension type** | Instructions Extension |
| **Duration** | ~20 minutes |

---

## The business problem

When someone asks the Onboarding Task Management Agent a question, they get an answer. What they don't get is any indication that the answer came from an AI system. For most enterprise use cases — and increasingly, for regulatory ones — that's a problem. Teams need to know when they're reading AI-generated output, and automated responses need to carry that label by default.

Today, nothing in the standard agent handles this. There's no disclaimer, no label, no indication of AI origin. And because it's a pre-delivered agent, you can't just edit its source code to add one.

An Instructions Extension solves this cleanly. It injects a plain-language rule into the agent's prompt at runtime — the agent reads it like any other instruction and follows it on every response. No code, no deployment complexity, no changes to the base agent.

## What you will build

A single Instructions Extension called `ad264-ai-disclaimer` that appends the following to every agent response:

> *"DISCLAIMER: This is an AI-generated response. For official HR guidance, please consult your HR Business Partner."*

---

## Exercise 1.1 — Open Joule Studio and Create a New Extension

After completing these steps you will have opened Joule Studio and initiated a new extension project targeting the Onboarding Task Management Agent.

Log in to SAP Joule Works using the credentials provided at your desk. In the left navigation panel, select **Develop** to open Joule Studio.

On the Joule Studio home screen, click **+ New** and select **Extension**.

In the dialog that appears, fill in the following:

| Field | Value |
|---|---|
| **Solution** | New Solution |
| **Extension name** | `ad264-ai-disclaimer` |
| **Base agent** | Onboarding Task Management Agent |
| **Intent Statement** | Leave this for the next step |
| **Quick Create** | ☑ Enable this |

> **Why Quick Create?** With Quick Create on, Joule Studio generates your extension immediately from the intent you provide — no clarifying questions, no structured review flow. For a focused instruction like a disclaimer, it produces accurate output in one step. In Exercise 3, you'll see the difference when the intent is more complex.

Don't click **Create** yet — add the intent statement first.

---

## Exercise 1.2 — Enter Your Intent Statement

After completing these steps you will have submitted your business requirement as a natural language intent statement and generated your first extension.

The intent statement is how you tell Joule Studio what your extension should do. You don't need to describe the technical implementation — describe the business behaviour, and Joule Studio works out what to build.

In the **Intent Statement** field, copy and paste the following:

```
Always include the following disclaimer at the end of every response: "DISCLAIMER: This is an AI-generated response. For official HR guidance, please consult your HR Business Partner."
```

Make sure **Quick Create** is checked, then click **Create**.

Joule Studio analyzes your intent and generates the extension. This takes a few seconds.

---

## Exercise 1.3 — Review the Generated Artifacts and Explore Joule Studio

After completing these steps you will have reviewed everything Joule Studio produced and got familiar with the key areas of the interface you'll use throughout all three exercises.

### Review the generated extension

Before saving, look at what Joule Studio produced:

- An **Instructions component** containing the disclaimer text, formatted as a system-level instruction the agent will follow at runtime
- The extension linked to the **Onboarding Task Management Agent** as its base

Click **Save**. The status changes to **Saved**.

> The extension now exists on the tenant but isn't active yet — it hasn't been deployed. Your facilitator will handle deployment live so you can see the result in action. Stop here and don't deploy.

### Explore the generated files

Open the **Files** tab in the solution view.

| File | What it is |
|---|---|
| `extension.yaml` | The extension descriptor — name, type, and which agent it targets |
| Instructions content | The disclaimer text, stored as a system instruction |

Notice there's no code here — just configuration. That's what makes an Instructions Extension lightweight: one text block is enough to change how the agent behaves at runtime.

### Explore the interface — Monitoring, Deploy, and Versions

Take a few minutes to explore the three areas you'll see referenced across all exercises:

**Monitoring tab** — Select this from the top navigation. This is where you see how often the agent has been invoked, which extensions are active per session, and any runtime errors. It gives you live visibility into agent behaviour without needing backend access.

**Deploy tab** — This is where an extension moves from Saved to active on the tenant. Deployment is an admin-level action — your facilitator will handle it during the live demo. Take a look at the flow, but don't click Deploy.

**Versions tab** — Open the extension detail view and select Versions. Every save creates a new version. You can compare versions, roll back to any previous state, and see who changed what when working in a team. Extensions can also be packaged here for transport across tenants (DEV → TEST → PROD).

---

## Summary

You've built your first agent extension. Starting from a one-sentence business requirement, Joule Studio produced a complete, deployable artifact — and you didn't write a single line of code.

More importantly, you've seen the core pattern: describe the behaviour you need, let Joule Studio handle the translation. The same approach applies to every extension type, and you'll use it twice more in the next two exercises.

---

[Next: Exercise 2 — Add Traceability with Pre and Post Hooks](../ex2/)

