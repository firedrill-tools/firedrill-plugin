# Firedrill

Connect Claude to [Firedrill](https://firedrill.run/agents), a simulation platform
for AI agents. Use the included skill to inspect your application's entry point,
prepare useful scenarios and controlled dependencies, and review retained reports
and evidence. Observation, demonstrations, comparisons and testing are valid
simulation goals; assessment is optional.

This plugin includes one remote MCP connection and one simulation skill. It
contains no local server, executable, lifecycle hook, package-install script,
credential or telemetry script. Install with Claude Code's native plugin manager:

```sh
claude plugin install firedrill --marketplace firedrill-tools/firedrill-plugin
```

Restart Claude Code, open `/mcp`, and use the native sign-in action for Firedrill.
Review the intended organization in the browser. Installation alone does not
authorize an account, approve tool calls or run a simulation. The host stores
OAuth credentials; never paste credentials into chat.

Try asking Claude to inspect the agent you are building, propose a small set of
useful scenarios, and show the saved report from one real simulation.

The MCP connection prepares and inspects simulations; your application executes
through an authorized customer-owned CLI or SDK runner on your laptop, in CI,
or through its existing execution seam. Publishing source or data and starting
work require your authorization. Keep live vendor credentials and real external
side effects outside synthetic simulations unless you deliberately authorize them.

**Firedrill is free to use.** Your application's model and runner costs remain
separate. An account and human authorization are required.

The connection uses `https://mcp.firedrill.run/mcp`, whose OAuth metadata directs
your host to Firedrill's WorkOS-backed authorization service. Actions are scoped
to the selected account, organization, project and environment. The content sent
depends on the operations you authorize, including recipes, selected data,
source and evidence. Review the [privacy policy](https://firedrill.run/privacy),
[terms](https://firedrill.run/terms) and [documentation](https://docs.firedrill.run/).

Only this thin plugin's connector, instructions and skill are MIT licensed.
Firedrill is a closed-source service; the license does not apply to its backend,
CLI, SDKs, other repositories or branding. Support: support@firedrill.run.
