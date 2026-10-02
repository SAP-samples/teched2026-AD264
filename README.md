# AD264 - Build and Extend AI Agents with SAP Joule Studio

## Description

This repository contains the material for the SAP TechEd 2026 session **AD264 - Build and Extend AI Agents with SAP Joule Studio**.

## Overview

This session shows how to build and extend AI agents using SAP Joule Studio — specifically the **Agent Extension** feature. You will work with a pre-built **Onboarding Task Management Agent** and extend it with a custom Ariba integration to automate equipment procurement for new hires.

### Use Case: Onboarding Task Management

HR and operations teams managing new-hire onboarding face a recurring problem: equipment is not ordered in time, and Day 1 readiness slips. Manually tracking pending tasks across systems takes time and is error-prone.

The **Onboarding Task Management Agent** (Onboarding Assistant) solves this by giving users a conversational interface to monitor onboarding tasks and act on blockers — directly from within Joule.

### End-to-End Flow

```
User asks: "What onboarding tasks are at risk for next week's new hires?"
```

1. The agent identifies new hires with pending tasks that could impact Day 1 readiness.
2. For a flagged hire (e.g., *Priya*), the agent determines required equipment — laptop, monitor, headset — from onboarding context.
3. The agent invokes the **Ariba Agent Extension** with the new hire's details and equipment requirements.
4. The Ariba extension identifies or creates the required procurement request.
5. If approval is required, the agent presents a confirmation to the user:

   > *"A laptop, monitor, and headset are required for Priya. Estimated cost: $X. Create the procurement request?"*

6. After user approval, the Ariba extension submits the order.
7. Ariba returns the requisition/order status (e.g., *Requisition #12345*).
8. The agent reports back and updates the onboarding task status accordingly.

**Sample conversation:**

| | |
|---|---|
| **User** | "Are there any onboarding tasks that could delay Priya's Day 1?" |
| **Agent** | "Yes. Her equipment provisioning task is still pending. I can use the Ariba extension to initiate the equipment order." |
| **User** | "Go ahead." |
| **Agent** | "The equipment request has been created in Ariba. Requisition #12345 is now pending fulfillment." |

### Agent Extensions

This session focuses on building two types of **Agent Extensions** in Joule Studio — a capability that lets you modify agent behaviour or connect agents to external LOB systems.

| Extension | Type | Purpose |
|---|---|---|
| **Language Extension** | Instructions Extension | Changes the agent's response language — a simple, self-contained introduction to the extension development and deployment lifecycle |
| **Ariba Extension** | LOB Integration Extension | Creates and tracks procurement requests for new-hire equipment in SAP Ariba |

> The session is deliberately sequenced: you build the instructions extension first to learn *how* extensions work, then apply the same pattern to the more complex Ariba integration.

### Systems Used

| System | Access Type |
|---|---|
| SAP S/4HANA Cloud Public Edition | Read & Write (onboarding task data) |
| SAP Ariba | Read & Write (procurement requests) |

## Requirements

To follow the exercises in this repository you need:

- Access to an SAP BTP subaccount with Joule Studio enabled
- Access to SAP S/4HANA Cloud Public Edition (provided in the session landscape)
- Access to SAP Ariba (provided in the session landscape)
- Basic familiarity with SAP BTP and REST APIs

## Exercises

The exercises follow a deliberate progression — from exploring an existing agent, to building a simple extension, to wiring up a real LOB system.

| # | Exercise | What you learn |
|---|---|---|
| 0 | [Getting Started](exercises/ex0/README.md) | Access the session landscape, open Joule Studio, verify connectivity |
| 1 | [Explore the Onboarding Task Management Agent](exercises/ex1/README.md) | Understand the agent's capabilities and limits by trying sample prompts *without* any extensions |
| 2 | [Build an Instructions Extension](exercises/ex2/README.md) | Create an extension that changes the agent's response language — learn the extension authoring lifecycle end-to-end with minimal complexity |
| 3 | [Deploy and Invoke the Instructions Extension](exercises/ex3/README.md) | Deploy the extension to the agent, invoke it, and verify the changed behaviour |
| 4 | [Build the Ariba Agent Extension](exercises/ex4/README.md) | Create an extension that connects to SAP Ariba to initiate equipment procurement for a new hire — artifacts (requisition) are created in the system |
| 5 | [Deploy and Invoke the Ariba Extension](exercises/ex5/README.md) | Deploy the Ariba extension, run the onboarding equipment procurement flow end-to-end, and verify the requisition in Ariba |

**IMPORTANT**

Your repo must contain the .reuse and LICENSES folder and the License section below. DO NOT REMOVE the section or folders/files. Also, remove all unused template assets(images, folders, etc) from the exercises folder.

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (20xx-)20xx SAP SE or an SAP affiliate company and <your-project> contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool](https://api.reuse.software/info/github.com/SAP/<your-project>).
