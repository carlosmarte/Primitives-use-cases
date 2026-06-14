# analyze-use-case-primitives

## Description
Breaks down system requirements and interactions into fundamental Context, State, and Flow primitives to guarantee deterministic, bounded, and testable use case scenarios.

## Trigger
Use this skill when presented with raw user stories, feature requests, or system requirements that need to be formalized into technical specifications, or when auditing an existing workflow for missing edge cases.

## Execution Steps

### 1. Extract Context Primitives
Identify the "who," "what," and "where" of the interaction before any action takes place:
* **Actor:** Identify the entity interacting with the system. Categorize as *Primary* (initiates the goal) or *Secondary* (assists the system).
* **System Boundary:** Define the explicit scope of what is being designed, separating internal mechanics from external actors.
* **Goal (Intent):** State the business or operational objective the primary actor is trying to achieve.

### 2. Define State Primitives
Establish the environmental requirements and guarantees (the contractual boundaries):
* **Trigger:** Identify the specific, discrete event that initiates the use case.
* **Preconditions:** List the mandatory state the system must be in *before* the trigger can be processed.
* **Postconditions (Guarantees):** Define the verifiable state of the system after conclusion. Include *Success Guarantees* (if the goal is met) and *Minimal Guarantees* (what is true even if the scenario fails, like rollbacks or logs).

### 3. Map Flow Primitives
Define the step-by-step execution timeline between the actor and the system:
* **Main Success Scenario (Happy Path):** Detail the optimal sequence of interactions from trigger to successful postcondition. Use a ping-pong format (e.g., "Actor does X," "System validates X and returns Y").
* **Extensions (Exception Flows):** Map all conditional branches, edge cases, and failures back to specific steps in the main flow (e.g., "Step 3a: Validation fails. System prompts for retry."). Define exact recovery or abort paths.

## Guardrails
* **Version Control:** If committing formalized use cases or specifications to the repository, always use standard `git` commands and the native `gh` CLI (e.g., `gh pr create`, `gh issue create`).
* **No MCP Connectors:** You are strictly forbidden from using the `github-create_pull_request` tool or any MCP connectors for version control operations.
