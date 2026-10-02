# Exercise 2 — Build an Instructions Extension

## Overview

| Field | Details |
|---|---|
| **Base Agent** | Onboarding Task Management Agent |
| **Extension Type** | Instruction Extension |
| **Business Context** | HR / Onboarding |
| **Complexity** | Simple |
| **Joule Studio Scope** | Agent Extension creation, Instruction Extension configuration |

> **Why start here?** An Instruction Extension requires no code, no APIs, and no external systems. It teaches you the full extension authoring lifecycle — intent, design, review — in the simplest possible way. You will apply the same lifecycle to the Ariba extension in Exercise 4.

---

## The Problem

The Onboarding Task Management Agent responds in English only. Your HR team onboarding new hires in Germany wants responses in **German** to avoid switching context.

**The gap:** The base agent has no language preference configured. No matter what language you write in, it responds in English.

**Instruction Extension closes this gap** — a single instruction injected into the agent prompt is enough to change the response language without touching any code.

---

## Extension Prompt

Paste this into the Joule Studio intent box:

```
I want the Onboarding Task Management Agent to always respond in German,
regardless of the language the user writes in.
All task names, status labels, and dates should also be presented in German.
Do not change any underlying data or task logic.
```

**Additional context to inject:**

```
Language Convention:
Always respond in German (Deutsch), regardless of the input language.
Translate all status labels, task names, and response text to German.
Keep all proper nouns (names, system names) unchanged.
Do not alter any onboarding task data, dates, or computed statuses.
```

---

## Steps

| Step | Phase | What you do |
|---|---|---|
| 1 | Open Joule Studio | Navigate to Develop → Agent Extension |
| 2 | Enter extension details | Name the extension and paste the intent prompt |
| 3 | Review the design screen | Confirm the Instruction Extension configuration |
| 4 | Save | Save the extension (do not deploy yet — that is Exercise 3) |

---

### Step 1 — Open Joule Studio

In the left navigation of Joule Work, select **Develop** to open Joule Studio.

On the Joule Studio home screen, select the **Agent Extension** tile.

![Joule Work — select Develop](img/01_joule_studio_home.png)

---

### Step 2 — Create the extension

A dialog appears. Fill in:

| Field | Value |
|---|---|
| **Extension name** | `onboarding-language-de` (or any unique name) |
| **Base agent** | Onboarding Task Management Agent |
| **Intent** | Paste the **Extension Prompt** from above |

Make sure **Quick Create is unselected** — this allows Joule Studio (IBD) to guide you through clarifying questions and generate the full extension design.

![Create Extension dialog — filled](img/02_create_extension_dialog.png)

Click **Create**.

---

### Step 3 — Review the design screen

IBD will ask clarifying questions to confirm your intent. Answer:
- Extension type: **Instruction Extension**
- Base agent: **Onboarding Task Management Agent**
- No tools or hooks needed

The design screen appears with:
- **Base Agent** field showing the Onboarding Task Management Agent
- **Additional context** section (empty by default)
- **Pre Hooks** and **Post Hooks** sections — leave these empty

Click **Edit** on the "Additional context" section. Paste the **Language Convention** text from above. Click the checkmark to save.

![Design screen — Additional Context filled](img/03_design_screen.png)

---

### Step 4 — Save

Your extension is configured. Do not deploy yet — you will deploy and test it in Exercise 3.

> **Checkpoint:** The design screen should show the Language Convention text in the Additional context section, and no tools or hooks.

---

## What This Extension Does

| Component | What it does |
|---|---|
| **Instruction Extension** | Injects the Language Convention into the agent prompt — the agent responds in German at runtime |

No code changes. No API connections. No hooks. The base agent's task data, logic, and connectivity are untouched.

---

[Back: Exercise 1 — Explore the Agent](../ex1/)
[Next: Exercise 3 — Deploy and Invoke the Instructions Extension](../ex3/)
