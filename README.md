# AD264 — Building Enterprise Agent Extensions with SAP Joule Studio

## Description

This repository contains the exercise guide for the SAP TechEd 2026 session **AD264 — Building Enterprise Agent Extensions with SAP Joule Studio**.

## Overview

Pre-delivered SAP agents are powerful out of the box. But the moment you sit down with a real HR team or a real onboarding process, you quickly discover the gaps. In this session, you'll close those gaps yourself — using Joule Studio's Intent-Based Development to describe the behaviour you need in plain language and watch it become a working extension. No boilerplate, no manual configuration, no specialist development skills required.

By the end of the session, you'll have built agent extensions across multiple extension types and have a pattern you can take home and apply to any pre-delivered SAP agent in your landscape.

### How Joule Studio fits into the SAP AI runtime

![Joule Studio Runtime: Agent Flow](exercises/ex1/images/00_runtime_agent_flow.png)

Joule Studio is where you **build**. Once deployed via Custom Artifact Deployment (CAD), your extension runs inside the **Joule Studio Runtime** — the same runtime that powers pre-delivered SAP agents. The Agent Gateway handles outbound calls to MCP servers, LoB systems, and other integrations. Extensions you build in this session slot directly into this architecture.

## Requirements

All system access required for this session will be provided to you. During the hands-on exercises you will be working with:

- **SAP Joule Works** with the pre-delivered Onboarding Task Management Agent
- **SAP Joule Studio** (Intent-Based Development)
- **SAP Ariba** integration via MCP (Exercise 2)

Credentials and tenant URL will be provided at your desk.

## The Agent You Will Extend

All three exercises use the same pre-delivered SAP agent: the **Onboarding Task Management Agent**.

![Task Onboarding Agent](exercises/ex1/images/00_onboarding_agent_overview.png)

This agent transforms onboarding execution from manual tracking to informed decision-making — continuously evaluating and ranking tasks across all hires using a composite risk score. It highlights what needs immediate attention, identifies blockers, and recommends next best actions for Hiring Managers and Onboarding Coordinators.

Out of the box it already does a lot. In this session you will extend it to do more — enforcing compliance prioritization, raising Ariba procurement requests, and adding pre/post execution hooks — all without touching its source code.

### The extensibility opportunity

![Agent Extensibility Use Case: Onboarding](exercises/ex1/images/00_use_case_onboarding.png)

### The extension types you will use

![Add multiple extension points to adapt Joule agents](exercises/ex1/images/00_extension_points_overview.png)

### Where it all fits: reference architecture

![Reference Architecture - Agent Extensions](exercises/ex1/images/00_reference_architecture.png)

## Exercises

- [Exercise 1 — Extend the Onboarding Task Manager Agent: Instruction Extension - Compliance Task Prioritization](exercises/ex1/)
- [Exercise 2 — Extend the Onboarding Task Manager Agent: MCP Extension – SAP Ariba Equipment Ordering](exercises/ex2/)
- [Exercise 3 ★ Bonus — Extend the Onboarding Task Manager Agent: Pre-Hook & Post-Hook](exercises/ex3/)

## Contributing

Please read the [CONTRIBUTING.md](CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct

Please read the [SAP Open Source Code of Conduct](https://github.com/SAP/.github/blob/main/CODE_OF_CONDUCT.md).

## How to Obtain Support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License

Copyright (2026) SAP SE or an SAP affiliate company and contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available via the [REUSE tool](https://api.reuse.software/info/github.com/SAP-samples/teched2026-AD264).
