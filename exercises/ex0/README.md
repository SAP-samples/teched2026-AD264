# Exercise 0 — Log In and Try the Onboarding Assistant Agent

Before you build any extensions, you need two things: access to the system and a baseline feel for how the Onboarding Task Manager Agent behaves **before** it has been extended. You will come back to this same agent after Exercise 1 and compare what changed.

> **Time:** ~10 minutes

---

## Exercise 0.1 — Log In to Joule Work

1. Open the browser and navigate to the Joule Work URL printed on the card at your desk.

2. Enter the **username** provided at your desk and click **Continue**.

3. **Wait for the facilitator to confirm the password before typing it.** The password will be announced to the room — do not attempt to log in before it is given.

4. Once logged in, confirm you can see the Joule Work home screen with the navigation panel on the left.

   > **Shared tenant:** Everyone in this session is using the same tenant. Do not change any settings, roles, or configurations. Do not attempt to deploy anything at this stage.

---

## Exercise 0.2 — Open the Onboarding Assistant Agent

1. In the Joule Work interface, look for the **chat** or **agents** entry point. This may appear as a chat icon or a "Start conversation" button depending on your layout.

2. In the agent selector or search bar, find and select **Onboarding Task Manager Agent**.

3. A new conversation opens — you should see a blank chat input at the bottom. The agent is ready.

   > If the agent does not appear, ask a session guide for help — it may need to be activated for your user.

---

## Exercise 0.3 — Try the Agent (Baseline — Before Any Extension)

You will send four prompts to get a feel for the agent's default behavior. The goal is to **observe** how the task list is structured right now — specifically, whether compliance tasks are sorted or labeled in any way.

### Pick a new hire

Use any name from the table below. The assignee column shows who manages that new hire in the demo data — it does not affect which one you choose. Just pick one and use the same name consistently across all three prompts, and again after Exercise 1 when you compare the before/after behavior.

| New Hire | Assignee |
|---|---|
| Mike Ross | Juana Yap |
| Sarah Diaz | Zander Lloyd |
| Adam Miles | Zander Lloyd |
| Peter Harris | Zoe McIlveen |
| Alisa Tyler | Zander Lloyd |
| Luke Williams | Jada Baker |
| David Brown | Zoe McIlveen |

### Send these four prompts

Replace `[New Hire]` with your chosen new hire's name. For Prompt 4, pick a **different** new hire from the table above to see how the agent handles progress tracking across multiple people.

**Prompt 1**
```
Show tasks for [New Hire]
```

**Prompt 2**
```
Show today's priority for [New Hire]
```

**Prompt 3**
```
Which new hires are at risk?
```

**Prompt 4**
```
Show progress for [Different New Hire]
```

### What to look for

As you read each response, note:

- Are compliance tasks (contract signing, data privacy, security training) listed first — or are they mixed in with IT setup, access requests, and equipment tasks?
- Is there any visual label or marker on compliance items?
- Does the agent mention urgency or risk level unprompted?

You do not need to write anything down. Just form a mental picture of the baseline so you have something to compare when you return to the agent after Exercise 1.

---

## Summary

You have logged in and seen the Onboarding Task Manager Agent as it ships — unextended. In Exercise 1 you will use Joule Studio to build a compliance prioritization instruction extension. After the facilitator deploys it, you will return here with the same prompts and see the difference.

Continue to — [Exercise 1 — Extend the Onboarding Task Manager Agent: Instruction Extension](../ex1/README.md)
