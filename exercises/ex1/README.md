# Exercise 1 — Explore the Onboarding Task Management Agent

## Overview

| Field | Details |
|---|---|
| **Agent** | Onboarding Task Management Agent (Onboarding Assistant) |
| **Extension** | None — base agent only |
| **Goal** | Understand what the agent can and cannot do out of the box |
| **Duration** | ~10 minutes |

> This exercise establishes the **BEFORE state**. You will compare these results against the extended agent in later exercises.

---

## The Agent

The **Onboarding Task Management Agent** helps HR and operations teams track new-hire onboarding tasks. It has access to onboarding task data in SAP S/4HANA Cloud and can:

- List open onboarding tasks for upcoming new hires
- Identify tasks that are overdue or at risk
- Report on a specific new hire's onboarding status

**What it cannot do out of the box:**
- Respond in a language other than English
- Initiate actions in external systems (e.g., place a procurement order in Ariba)

---

## Try These Prompts

Work through the prompts below in order. Note the agent's response each time — you will refer back to these in later exercises.

### Prompt 1 — General status

```
What onboarding tasks are at risk for next week's new hires?
```

Expected: The agent lists new hires with pending or overdue tasks. Look for **Priya** in the list — her equipment provisioning task should be flagged.

---

### Prompt 2 — Drill into a specific new hire

```
Are there any onboarding tasks that could delay Priya's Day 1?
```

Expected: The agent identifies the equipment provisioning task as pending. It may suggest that action is needed but cannot take that action itself.

---

### Prompt 3 — Ask about equipment

```
What equipment does Priya need for Day 1?
```

Expected: The agent returns a list of required items (laptop, monitor, headset) based on the onboarding context. It provides information but takes no action.

---

### Prompt 4 — Ask for an action the agent cannot perform

```
Please create a procurement request in Ariba for Priya's equipment.
```

Expected: The agent declines or says it cannot perform that action — it has no connection to Ariba. **This is intentional.** You will fix this in Exercise 4.

---

### Prompt 5 — Language test

```
Beantworte meine nächste Frage auf Deutsch.
What is Priya's onboarding status?
```

Expected: The agent will likely respond in English regardless of the instruction. **This is intentional.** You will fix this in Exercise 2.

---

## What to Note

Before moving on, make a mental note of:

1. The agent's default response language
2. The fact that it cannot initiate Ariba procurement requests
3. Priya's pending equipment provisioning task — you will use this in Exercises 4 and 5

---

[Back: Exercise 0 — Getting Started](../ex0/)
[Next: Exercise 2 — Build an Instructions Extension](../ex2/)
