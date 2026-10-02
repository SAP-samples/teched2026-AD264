# Exercise 5 — Deploy and Invoke the Ariba Extension

## Overview

| Field | Details |
|---|---|
| **Extension** | `onboarding-ariba-procurement` (built in Exercise 4) |
| **Goal** | Deploy the extension and run the full onboarding equipment procurement flow end-to-end |
| **Duration** | ~15 minutes |

---

## Steps

| Step | Phase | What you do |
|---|---|---|
| 1 | Deploy | Click Deploy on the design screen |
| 2 | Wait for deployment | Confirm "Deployment successful" |
| 3 | Run the E2E flow | Start a new chat and work through the procurement scenario |
| 4 | Verify in Ariba | Confirm the requisition was created in SAP Ariba |
| 5 | Compare | Review the BEFORE vs AFTER state |

---

### Step 1 — Deploy

From the design screen of the `onboarding-ariba-procurement` extension, click **Deploy** in the top right corner.

![Starting deployment](img/01_deploying.png)

---

### Step 2 — Wait for deployment

Wait for **"Deployment successful"**.

Both components — the MCP tool and the instruction policy — deploy as a single extension unit. They are registered in ORD and loaded by Agent Gateway at runtime.

![Deployment pending](img/02_deployment_pending.png)

> The SAP Ariba Procurement API must be reachable from Agent Gateway for the extension to function. If deployment succeeds but the tool call fails at runtime, check the API connectivity with your facilitator.

---

### Step 3 — Run the end-to-end flow

Return to the Onboarding Task Management Agent in Joule Work. **Start a New Chat.**

Work through the following conversation:

**Turn 1 — Identify the risk:**
```
Are there any onboarding tasks that could delay Priya's Day 1?
```

Expected: The agent identifies the equipment provisioning task as pending and mentions it can use the Ariba extension to initiate an order.

---

**Turn 2 — Initiate the procurement:**
```
Go ahead.
```

Expected: The agent calls the `create-procurement-request` tool and presents a confirmation:

> *"A laptop, monitor, and headset are required for Priya. Estimated cost: $X. Create the procurement request?"*

---

**Turn 3 — Confirm:**
```
Yes, confirm.
```

Expected: The agent submits the request to Ariba and reports back:

> *"The equipment request has been created in Ariba. Requisition #12345 is now pending fulfillment."*

![Full E2E conversation](img/03_e2e_conversation.png)

---

### Step 4 — Verify in Ariba

Open SAP Ariba (URL provided on your exercise card). Navigate to **Procurement → Requisitions**.

Search for the requisition number returned by the agent (e.g., `#12345`).

Verify:
- Requester name matches Priya
- Equipment list matches what the agent confirmed
- Status is **Pending Fulfillment** (or equivalent)

![Requisition in Ariba](img/04_ariba_requisition.png)

---

### Step 5 — Compare BEFORE vs AFTER

| | BEFORE (Exercise 1) | AFTER (Exercise 5) |
|---|---|---|
| Identify pending equipment task | ✅ | ✅ |
| Determine equipment required | ✅ | ✅ |
| Confirm with user before acting | ❌ | ✅ |
| Create requisition in Ariba | ❌ | ✅ |
| Return requisition number | ❌ | ✅ |
| Base agent code changed | — | No |

---

## Demo Story: "Priya's Day 1"

### BEFORE — Agent identifies the problem, can't solve it

**Prompt:** `Are there any onboarding tasks that could delay Priya's Day 1?`

- Agent correctly identifies the equipment provisioning task as pending
- Agent cannot initiate any action — no Ariba connection
- HR coordinator must leave Joule, open Ariba, and create the request manually

### AFTER — Onboarding Agent + Ariba Extension

**What changed (zero code changes to the base agent):**
- New MCP tool: `create-procurement-request` — writes procurement requests directly to SAP Ariba
- Instruction Extension: Equipment Procurement Policy — enforces user confirmation and formats responses

**Result:**
- Agent identifies the risk, explains it, and offers to act
- User approves with a single message
- Requisition created in Ariba — requisition number returned to Joule
- HR coordinator never leaves the conversation

**Key talking points:**
- Zero code changes to the Onboarding Task Management Agent
- Connected to live SAP Ariba — real requisition created, not a simulation
- Human-in-the-loop by design: the agent confirms before submitting
- Same extension lifecycle as the Instructions Extension — intent, design, deploy, test

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Agent does not offer to create a procurement request | Start a **New Chat** to load the extension |
| Tool call fails at runtime | Check Ariba API connectivity with your facilitator |
| Requisition not visible in Ariba | Check that you are logged into the correct Ariba tenant (exercise card) |

---

[Back: Exercise 4 — Build the Ariba Agent Extension](../ex4/)
[Back to Start: Exercise 0 — Getting Started](../ex0/)
