In systems analysis and software engineering, a **Use Case** scenario defines how a system interacts with its environment to achieve a specific goal. To build a robust use case, it is broken down into fundamental building blocks, or "primitives."

These primitives guarantee that the scenario is deterministic, bounded, and testable. They can be categorized into three main groups: **Context**, **State**, and **Flow**.

### Context Primitives

These define the "who," "what," and "where" of the interaction before any action takes place.

- **Actor:** The entity interacting with the system. This is usually a human user, but can also be an external API, a scheduled cron job, or another hardware component. Actors are categorized as *Primary* (initiates the goal) or *Secondary* (assists the system in completing the goal).
- **System Boundary:** The explicit scope of what is being designed or discussed. It separates the internal mechanics of the system from the external actors interacting with it.
- **Goal (Intent):** The business or operational objective the primary actor is trying to achieve by executing the scenario.

### State Primitives

These define the environmental requirements and guarantees of the system, acting as the strict contractual boundaries of the scenario.

- **Trigger:** The specific, discrete event that initiates the use case. This could be a user clicking a button, a message arriving in a queue, or a specific time being reached.
- **Preconditions:** The mandatory state the system must be in *before* the trigger can be processed. If the preconditions are not met, the use case cannot execute.
- **Postconditions (Guarantees):** The verifiable state of the system after the scenario has concluded. This includes **Success Guarantees** (what is true if the goal is met) and **Minimal Guarantees** (what is true even if the scenario fails, such as a rolled-back database transaction or a logged error).

### Flow Primitives

These define the actual step-by-step execution timeline between the actor and the system.

- **Main Success Scenario (The Happy Path):** The optimal sequence of interactions from the trigger to the successful postcondition. It assumes nothing goes wrong and no edge cases are hit. Steps are typically written as a ping-pong interaction (e.g., "Actor does X," "System validates X and returns Y").
- **Extensions (Alternate / Exception Flows):** The conditional branches off the Main Success Scenario. These handle all variations, edge cases, and failures. Every extension maps back to a specific step in the main flow (e.g., "Step 3a: Validation fails. System prompts for retry."). Extensions define how the system recovers or gracefully aborts.
