# Exercise 3 — Connect the Agent to Ariba for Equipment Procurement

## Overview

| | |
|---|---|
| **Base agent** | Onboarding Task Management Agent |
| **Extension type** | MCP Tool Extension |
| **Duration** | ~25 minutes |

---

## Where we left off

In Exercises 1 and 2, you extended the Onboarding Task Management Agent with instructions and hooks. Both of those extension types work *around* the agent's existing capabilities — they add labels, inject context, and run logic at the edges.

In this exercise, you'll go further. You'll give the agent an entirely new capability: the ability to reach into Ariba, check whether a new hire's equipment has been ordered, and create a procurement request if it hasn't — all from within the conversation.

---

## The business problem

When a new hire's equipment isn't ordered in time, they arrive on Day 1 without what they need. The Onboarding Task Management Agent can identify when a provisioning task is at risk — but today it stops there. It can tell you there's a problem; it can't do anything about it.

That gap exists because the agent has no connection to Ariba. It doesn't know what procurement requests exist, it can't create new ones, and it has no way to confirm whether equipment will arrive on time.

An MCP Tool Extension closes that gap. It registers a tool the agent can call at runtime — a direct line into Ariba's APIs. When the agent determines that equipment needs to be ordered, it invokes the tool, presents the proposed request for approval, and executes it after the user confirms. The entire flow — detection, proposal, approval, execution, confirmation — happens inside one conversation.

## What you will build

An MCP Tool Extension called `ad264-ariba-procurement` that connects the Onboarding Task Management Agent to Ariba, with:

- An **MCP tool** that queries Ariba for existing procurement requests and creates new ones
- An **approval gate** that surfaces the proposed order to the user before anything is submitted
- A **status handler** that returns the requisition number back to the agent so it can update the onboarding task status

---

## Exercise 3.1 — Create a New MCP Tool Extension

After completing these steps you will have started a new solution targeting the Onboarding Task Management Agent for an MCP tool extension.

In Joule Studio, click **+ New** and select **Extension**.

A dialog opens. For the **Base agent** field, click the **Select Agent** icon to open the agent catalog. Search for **Onboarding Task Management Agent** and select it. You are returned to the dialog with the agent pre-populated.

Fill in the remaining fields:

| Field | Value |
|---|---|
| **Solution** | New Solution |
| **Extension name** | `ad264-ariba-procurement` |
| **Intent Statement** | Leave this for the next step |
| **Quick Create** | ☑ Enable this |

Don't click **Create** yet.

---

## Exercise 3.2 — Enter Your Intent Statement

After completing these steps you will have submitted a multi-step business scenario as an intent statement and triggered generation of an MCP tool extension.

This intent is more complex than the previous two — it describes a full workflow with a procurement request, an approval step, and a status update. Even so, the approach is exactly the same: describe what you need in business language, and Joule Studio works out the structure.

In the **Intent Statement** field, copy and paste the following:

```
Create an MCP tool extension for the Onboarding Task Management Agent that connects to Ariba to handle equipment procurement for new hires.

The extension should:
1. Identify onboarding equipment provisioning tasks that are at risk for upcoming new hires.
2. Determine the required equipment for each new hire based on their onboarding context — for example, laptop, monitor, and headset.
3. Invoke the Ariba MCP tool with the new hire's name and equipment list to create or identify an existing procurement request.
4. Before executing, present the proposed action to the user for approval:
   "A laptop, monitor and headset are required for [Name]. Estimated cost: $X. Create the procurement request?"
5. After user approval, execute the order in Ariba.
6. Return the requisition number and fulfillment status from Ariba to the agent.
7. Use the returned status to inform the user whether the onboarding task is on track for Day 1 readiness.
```

Make sure **Quick Create** is checked, then click **Create**.

Once you click Create, Joule Studio begins processing your intent. This takes approximately **5 minutes** — it analyzes the full workflow, derives requirements for the procurement flow and approval gate, builds a technical specification, and generates all the extension files including the MCP tool schema and connector logic.

---

## Exercise 3.3 — Review the Generated Artifacts and Run the Scenario

After completing these steps you will have reviewed what Joule Studio produced for an MCP tool extension and understood how the agent uses it at runtime.

### Review the generated project

Once generation completes, open the **Files** tab and explore the full project:

| File | What it is |
|---|---|
| `intent.md` | The intent summary — Joule's interpretation of the procurement workflow |
| `prd.md` | The Product Requirements Document — functional requirements for the Ariba integration, approval gate, and status tracking |
| `spec.md` | The technical specification — MCP tool schema, Ariba API contract, approval flow logic |
| `extension.yaml` | Extension descriptor — type `mcp-tool`, MCP server registration, tool manifest |
| `tool-schema.json` | The tool definition the agent calls — input parameters and output structure |
| `ariba-connector.js` | The MCP server logic — authenticates to Ariba, constructs the request, returns the result |

Notice how much richer this project is compared to Exercises 1 and 2. The PRD and spec capture the full procurement workflow — including the approval gate and the status mapping back to the onboarding task — before a single line of extension code is written. This is the value of intent-based development: structured, documented, traceable from business requirement all the way through to deployable code.

Click **Save**.

### The conversation this enables

Once deployed, here's the kind of conversation the agent can have:

```
User:   "What onboarding tasks are at risk for next week's new hires?"

Agent:  "Priya's equipment provisioning task is still pending and could
         impact her Day 1 readiness."

User:   "Can you do something about it?"

Agent:  "Yes. A laptop, monitor and headset are required for Priya.
         Estimated cost: $2,400. Should I create the procurement
         request in Ariba?"

User:   "Go ahead."

Agent:  "Done. Requisition #12345 has been created in Ariba and is
         now pending fulfillment. Priya's equipment should arrive
         before her start date."
```

That's the full loop — detection, proposal, approval, execution, confirmation — inside a single conversation. No switching between systems, no manual Ariba navigation, no email chains.

> **Please stop here and don't deploy.** Your facilitator will walk through the full deployment and demonstrate the running extension live. Deployment can take a few minutes, so it will be shown rather than completed individually.

---

## Summary

You've now built all three extension types: an Instructions Extension that shapes what the agent says, a Hooks Extension that intercepts every interaction at the execution level, and an MCP Tool Extension that gives the agent the ability to act in an external system.

Every one of them started with a plain language description. Every one produced a complete project — intent, requirements, specification, and working extension files. Joule Studio handled the translation.

That's the pattern — and it works for any pre-delivered SAP agent in your landscape.

**Happy TechEd 🎉**

---

[Back: Exercise 2 — Add Traceability with Pre and Post Hooks](../ex2/)
[Back to Overview](../../README.md)
