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

For Gemini CLI, use its native extension manager:

```sh
gemini extensions install https://github.com/firedrill-tools/firedrill-plugin
```

Review the extension's remote MCP connection before confirming. Reload Gemini
CLI, then use `/mcp auth firedrill` to complete browser authorization. The extension
uses Streamable HTTP and includes the simulation skill; it has no executable,
install hook, bundled credential, or blanket tool-approval rule. Gallery indexing
is separate from direct installation and is not guaranteed by this command.

For Kimi Code, use its native plugin manager:

```text
/plugins install https://github.com/firedrill-tools/firedrill-plugin
/reload
```

The plugin declares one remote MCP connection and the same simulation skill.
Use `/mcp-config login firedrill` to complete browser sign-in when prompted.
Review and approve the intended Firedrill organization; never paste a token into
chat. Direct installation is separate from Kimi's curated marketplace approval.

For Kiro, open **Powers → Add Custom Power → Import power from GitHub** and use:

```text
https://github.com/firedrill-tools/firedrill-plugin/tree/main/kiro
```

The `kiro/` power uses the Agent Plugins format. Its Streamable HTTP manifest
is separate from the other hosts' configuration formats.
Review the remote connection and complete Kiro's MCP browser authorization.
Direct import does not mean the power has been accepted into Kiro's registry.

For OpenCode, merge the native remote entry in
[`opencode/opencode.json`](./opencode/opencode.json) into your application's
configuration, then run `opencode mcp auth firedrill` from that application
directory. The [OpenCode guide](./opencode/README.md) includes safe setup,
optional skills, inspection and removal. This uses OpenCode's native remote
support, not an executable hook plugin.

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
