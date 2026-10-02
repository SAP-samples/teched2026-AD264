# Exercise 3 — Deploy and Invoke the Instructions Extension

## Overview

| Field | Details |
|---|---|
| **Extension** | `onboarding-language-de` (built in Exercise 2) |
| **Goal** | Deploy the extension to the dev runtime and verify it changes the agent's response language |
| **Duration** | ~10 minutes |

---

## Steps

| Step | Phase | What you do |
|---|---|---|
| 1 | Deploy | Click Deploy on the design screen |
| 2 | Wait for deployment | Confirm "Deployment successful" |
| 3 | Test | Return to the agent, start a new chat, and run the test prompts |
| 4 | Compare | Verify the BEFORE vs AFTER difference |

---

### Step 1 — Deploy

From the design screen of the `onboarding-language-de` extension, click **Deploy** in the top right corner.

![Starting deployment](img/01_deploying.png)

---

### Step 2 — Wait for deployment

A progress indicator appears. Wait for the status to show **"Deployment successful"**.

Deployment typically completes within 1–2 minutes.

![Deployment pending](img/02_deployment_pending.png)

> The extension is now registered and will be loaded by Agent Gateway whenever the Onboarding Task Management Agent is invoked in your tenant.

---

### Step 3 — Test the extension

Return to the Onboarding Task Management Agent in Joule Work. **Start a New Chat** — the extension is only active in a fresh session after deployment.

Run the following prompts:

**Prompt 1 — Same as Exercise 1, Prompt 1:**
```
What onboarding tasks are at risk for next week's new hires?
```

Expected: The agent responds **in German**. Task names, status labels, and dates should all appear in German.

**Prompt 2:**
```
Are there any onboarding tasks that could delay Priya's Day 1?
```

Expected: German response. The task status for Priya should be described in German (e.g., "Ausstehend" instead of "Pending").

![Test result — German response](img/03_test_result.png)

---

### Step 4 — Compare BEFORE vs AFTER

| | BEFORE (Exercise 1) | AFTER (Exercise 3) |
|---|---|---|
| Response language | English | German |
| Task data | Unchanged | Unchanged |
| Onboarding logic | Unchanged | Unchanged |
| Base agent code | — | Untouched |

The extension changed only the language. No data, no logic, no base agent code was modified.

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Agent still responds in English | Make sure you started a **New Chat** — existing sessions do not pick up the extension |
| Deployment failed | Check that the Onboarding Task Management Agent is correctly selected as the base agent on the design screen |

---

## Key Takeaway

You have now completed the full extension lifecycle:
**Intent → Design → Deploy → Test**

This is the same lifecycle you will use for the Ariba extension in Exercises 4 and 5 — the difference is that the Ariba extension also adds an MCP tool to connect to an external system.

---

[Back: Exercise 2 — Build the Instructions Extension](../ex2/)
[Next: Exercise 4 — Build the Ariba Agent Extension](../ex4/)
