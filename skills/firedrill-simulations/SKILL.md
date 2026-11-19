---
name: firedrill-simulations
description: Use Firedrill to explore or evaluate an AI agent or agentic application with synthetic dependencies, locally executed drills and saved reports.
---

# Firedrill simulations

Inspect the actual application's task entry point, completion signal and reset
boundary. Use an existing command, HTTP endpoint or supported callable rather
than migrating its framework. The application under simulation is distinct from
you, the coding agent operating Firedrill.

Use the connected Firedrill remote MCP and the host's native OAuth sign-in.
Human consent authorizes the intended organization; do not request pasted tokens,
read environment secrets, or reuse credentials from another organization. Inspect
current project/environment context and discover the available tools and schemas.

If the user has no workspace, direct them to the
[Firedrill web app](https://app.firedrill.run/signin) to finish workspace setup.
If a workspace request is already pending, keep that original request and have
the user check its status there. Then use the same organization in the CLI and
MCP sign-ins.

Match the simulation to the user's question. Observation needs no grading;
evaluation may use semantic scoring for valid output variation and exact checks
for hard constraints. Propose realistic situations grounded in the application,
not thousands of renamed copies of the same input. Declare the proposed target,
cases, repetitions and dependency/reset boundaries before execution.

Remote MCP prepares and inspects work; it does not launch the user's repository.
Use the separately authorized Firedrill CLI to run the target on the user's
machine. If the CLI is not set up, point the user to `npx firedrill-run init`.
Use `plan`, `apply` and `run` for new drills; get human approval for the exact
local commands before they start. This plugin does not provide managed CI.
Use installed CLI help and the [quickstart](https://docs.firedrill.run/quickstart)
for the current contract. Do not install packages or change host trust merely
because the plugin was installed.

Select only needed synthetic dependencies and explicitly authorized data.
Keep live vendor credentials and external side effects out of a simulation unless
the user deliberately authorizes them. Resetting Firedrill Tools does not reset
the application's database, process memory, external services or LLM randomness.
Never silently fall back to live production services.
Register the target with metadata only; do not upload its source or credentials.

Reconcile an uncertain operation using its retained recovery handle before
retrying. Queued work, setup success and manual Tool probes are not proof that
the target ran. Keep execution, observed outcome and assessment distinct;
an evaluator error is not an agent failure and a score is not a
calibrated probability. Never fabricate screenshots, Tool calls, scores or runs.

Finish with the retained report link, important observations, evidence gaps and
next action. For repetitions or comparisons, show distributions and meaningful
failure/interruption/unknown counts, not a cherry-picked score. Preserve the
the cloud resource IDs and original request keys for recovery. Do not publish
credentials, target input or customer evidence in the repository.
