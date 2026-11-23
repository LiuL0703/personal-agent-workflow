---
name: personal-agent-workflow
description: "Run a confirmation-first workflow for planning or implementing changes. Use when the user invokes personal-agent-workflow or their instructions require agreement on the request before planning or implementation."
---

# Personal agent workflow

## Confirm the request

For a new request that needs planning or implementation, read the bundled [in-your-own-words](references/pstack/in-your-own-words.md) and respond in the user's language. Restate the problem, the intended result, and the scope in your own words. Surface only assumptions or unresolved decisions that could change the outcome. Ask the user to confirm or correct your understanding, then end the turn. Planning and implementation start in a later turn after the user explicitly confirms the restatement.

If the user corrects the restatement, incorporate the correction and ask for confirmation again. If an agreed request changes materially, restate the revised scope and wait again. Continue within the confirmed scope for status requests and routine implementation decisions. Answer standalone questions and read-only information requests directly.

## Plan and implement

After confirmation, inspect the relevant workspace and its instructions. Write a plan proportionate to the request that names the changes and how to verify them. If the user asked for a plan only, deliver the plan and stop. If implementation is in scope, proceed with the plan and preserve unrelated work. Follow the project's authorization requirements for actions such as publishing or deployment.

## Verify and report

Before reporting completion, read the bundled [Prove It Works](references/pstack/principle-prove-it-works.md). Check the outcome against the confirmed scope using the feature's normal entry point or the actual deliverable when available. Report what changed, which checks ran, and any behavior you could not verify.
