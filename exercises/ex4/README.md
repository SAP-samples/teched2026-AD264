# Exercise 4 — Build the Ariba Agent Extension

## Overview

| Field | Details |
|---|---|
| **Base Agent** | Onboarding Task Management Agent |
| **Extension Types** | Tool Extension (MCP) + Instruction Extension |
| **Business Context** | HR Onboarding / Procurement |
| **Complexity** | Moderate |
| **System Dependencies** | Onboarding Task Management Agent, Agent Gateway, SAP Ariba Procurement API |
| **Joule Studio Scope** | Agent Extension creation, MCP tool creation, Instruction Extension, deployment |

---

## The Problem

The Onboarding Task Management Agent can identify that a new hire's equipment provisioning task is pending — but it can do nothing about it. A HR coordinator still has to leave Joule, open Ariba, and manually create a procurement request.

**The gap:** The agent is informational only. It surfaces the problem but cannot act on it.

| What the agent can do today | What the agent cannot do |
|---|---|
| Identify Priya's equipment task as pending | Create a procurement request in Ariba |
| List required equipment (laptop, monitor, headset) | Track requisition status from Ariba |
| Flag Day 1 readiness risk | Close the loop on the onboarding task |

**This extension closes the gap.** A new MCP tool exposes the Ariba Procurement API, and an instruction policy tells the agent when and how to use it.

---

## Extension Prompt

Paste this into the Joule Studio intent box:

```
I want the Onboarding Task Management Agent to be able to create
equipment procurement requests in SAP Ariba for new hires whose
equipment provisioning task is pending.

The agent should confirm the equipment list and estimated cost with
the user before submitting the request.
```

**Additional context to inject (Instruction Extension):**

```
Equipment Procurement Policy:
When a new hire's equipment provisioning task is identified as pending AND
the user asks to initiate procurement, follow this process:

1. Confirm the equipment list with the user before submitting:
   "A [equipment list] is required for [name]. Estimated cost: [cost].
   Create the procurement request?"

2. Only proceed after explicit user approval ("yes", "go ahead", "confirm").

3. Call the create-procurement-request tool with:
   - new_hire_name: the new hire's full name
   - equipment_list: the confirmed list of items
   - justification: "Day 1 equipment for new hire [name]"

4. On success: Report the requisition number and status.
   "The equipment request has been created in Ariba.
   Requisition #[number] is now pending fulfillment."

5. On error: Surface the error and offer to retry or escalate to the
   procurement team.
```

---

## MCP Tool Definition

When Joule Studio prompts you to define the MCP tool, use the following:

| Field | Value |
|---|---|
| **Tool name** | `create-procurement-request` |
| **Description** | Creates an equipment procurement request in SAP Ariba for a new hire |
| **Input: new_hire_name** | string — Full name of the new hire |
| **Input: equipment_list** | string — Comma-separated list of equipment items |
| **Input: justification** | string — Business justification for the request |
| **API endpoint** | SAP Ariba Procurement API (provided in the session landscape) |

---

## Steps

| Step | Phase | What you do |
|---|---|---|
| 1 | Open Joule Studio | Navigate to Develop → Agent Extension |
| 2 | Enter extension details | Name and paste the intent prompt |
| 3 | Create the MCP tool | Define `create-procurement-request` and connect to the Ariba API |
| 4 | Add the instruction policy | Paste the Equipment Procurement Policy into Additional context |
| 5 | Save | Save the extension (deploy in Exercise 5) |

---

### Step 1 — Open Joule Studio

Select **Develop** in the left navigation of Joule Work. On the home screen, select **Agent Extension**.

---

### Step 2 — Create the extension

| Field | Value |
|---|---|
| **Extension name** | `onboarding-ariba-procurement` |
| **Base agent** | Onboarding Task Management Agent |
| **Intent** | Paste the **Extension Prompt** from above |

Make sure **Quick Create is unselected**. Click **Create**.

![Create Extension dialog — filled](img/02_create_extension_dialog.png)

IBD will ask clarifying questions. Confirm:
- You need a **new MCP tool** to create procurement requests in Ariba
- You also need an **Instruction Extension** (policy for when to use the tool)

---

### Step 3 — Create the MCP tool

On the design screen, in the **Tools / MCP** section, click **+ Create MCP**.

Fill in the tool definition using the values from the **MCP Tool Definition** table above.

![Generating intent](img/06_generating_intent.png)
![Intent generated with clarifying questions](img/08_intent_generated.png)
![Design screen — MCP section](img/09_design_screen.png)

Save the MCP tool. It will appear in the agent's available tools at runtime.

---

### Step 4 — Add the instruction policy

Click **Edit** on the "Additional context" section of the design screen.

Paste the **Equipment Procurement Policy** text from above. Click the checkmark to save.

Verify the preview shows:
- The confirmation step (user must approve before submission)
- The `create-procurement-request` tool call
- The success and error response formats

---

### Step 5 — Save

Your extension is configured with two components:

| Component | What it adds |
|---|---|
| **MCP Tool Extension** | `create-procurement-request` — writes a procurement request to SAP Ariba |
| **Instruction Extension** | Equipment Procurement Policy — enforces user confirmation and defines the agent's response format |

Do not deploy yet — that is Exercise 5.

> **Checkpoint:** The design screen should show the MCP tool listed under Tools and the policy text in Additional context.

---

## What This Extension Does

The extension adds two things that work together:

- The **MCP tool** gives the agent the ability to write to Ariba — without it, the agent has no API connection
- The **instruction policy** tells the agent *when* to use the tool and *how* to behave — confirmation before submission, structured success/error responses

Neither component works without the other.

---

[Back: Exercise 3 — Deploy and Invoke the Instructions Extension](../ex3/)
[Next: Exercise 5 — Deploy and Invoke the Ariba Extension](../ex5/)
