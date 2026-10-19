# Firedrill plugin

Connect your coding agent to [Firedrill](https://firedrill.run/agents), a
simulation platform for AI agents. Your coding agent can prepare and operate
simulations of the AI agent you're building on your behalf. Explore its behavior,
run useful scenarios, and inspect saved evidence. Testing and assessment are optional;
observation and demonstrations are valid simulations too.

**Firedrill is free to use.** Your application's model and runner costs remain
separate. An account and human authorization are required.

## Connect

This repository contains a remote MCP connector and one simulation skill.
It does not install or run a local MCP server, application, or shell hook.

The remote connection is:

```json
{
  "mcpServers": {
    "firedrill": {
      "type": "http",
      "url": "https://mcp.firedrill.run/mcp"
    }
  }
}
```

Install the plugin using your host's plugin installation flow. Cursor reads
`.cursor-plugin/plugin.json` and `mcp.json`; Grok Build reads
`.grok-plugin/plugin.json` and `.mcp.json`. Marketplace approval is separate
from this public source repository; do not assume a listing exists yet.

After installation, use your host's native MCP sign-in action and approve the
intended Firedrill organization in the browser. The host stores OAuth credentials;
no key belongs in this repository or in the agent's conversation.

Try asking:

> Use Firedrill to explore this application's behavior. Inspect its entry point,
> propose useful scenarios, and start with one real simulation. Show me the saved
> report and explain what was actually observed.

Remote MCP can prepare simulations, manage authorized synthetic dependencies,
and inspect reports. It cannot execute your local repository. To run your actual
application, use an authorized customer-owned CLI or SDK runner. The short CLI
setup command, run from the application's repository, is:

```sh
npx firedrill-run init
```

CLI sign-in is separate from the MCP host's OAuth session. Choose the same
intended organization. CI uses its supported noninteractive credential, not an
interactive browser prompt. [Read the setup guide](https://firedrill.run/agents)
and [documentation](https://docs.firedrill.run/).

## Data and permissions

The connector uses `https://mcp.firedrill.run/mcp`. OAuth metadata directs your
host to Firedrill's WorkOS-backed authorization service. No static credentials,
environment-file readers, telemetry scripts, lifecycle hooks, binaries, or
runtime dependencies are included in this plugin.

Actions through the connection access the selected Firedrill account,
organization, project and environment. Publish source/data or start simulations
only within the user's authorization. Your application stays on your laptop,
in CI, or at its existing execution seam. Review Firedrill's
[privacy policy](https://firedrill.run/privacy) and
[terms](https://firedrill.run/terms).

## License

The connector manifests, instructions and skill **in this repository only** are
MIT licensed. Firedrill is a closed-source service. This license does not apply
to its backend, CLI, SDKs, other repositories, or branding. Free service access
and open-source licensing are separate; service access is governed by its terms.

Support: [support@firedrill.run](mailto:support@firedrill.run).
