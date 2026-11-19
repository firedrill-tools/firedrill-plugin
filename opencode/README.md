# Firedrill for OpenCode

Connect OpenCode to [Firedrill](https://firedrill.run/agents), a simulation
platform for AI agents. OpenCode can prepare and inspect simulations of the
application you are building. It is the operator, not necessarily the application
being simulated.

## Connect

If you're new to Firedrill, [sign in to the web app](https://app.firedrill.run/signin)
and create or choose a workspace first.

Merge the `mcp.firedrill` entry from [opencode.json](./opencode.json) into your
application's `opencode.json` or `opencode.jsonc`. Preserve existing settings and
other servers; do not replace your entire configuration.

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "firedrill": {
      "type": "remote",
      "url": "https://mcp.firedrill.run",
      "enabled": true
    }
  }
}
```

From that application directory, use OpenCode's native commands:

```sh
opencode mcp auth firedrill
opencode mcp list
```

The first command opens browser OAuth authorization. Approve the organization
that owns your Firedrill workspace. Do not paste an access
token into the conversation or configuration. OpenCode stores the credential;
no API key, executable adapter, or local MCP process is needed.
If the connection is not available, `opencode mcp debug firedrill` diagnoses
transport and OAuth discovery without invoking simulation tools.

## Optional workflow skill

To add the canonical simulation instructions to this application, use:

```sh
npx skills add firedrill-tools/firedrill-skills --skill firedrill --agent opencode
```

Review the skill before installation. This is project-local unless you explicitly
choose a global installation. Installing instructions is not account authorization
and does not run simulations. Do not also install a duplicate copy through another
plugin manager.

Then ask OpenCode:

> Use Firedrill to explore this application's behavior. Inspect its entry point,
> propose useful scenarios, and start with one real simulation after showing me
> the execution plan. Give me the saved report and explain what was observed.

## Execution and control

Remote MCP can prepare scenarios, configure authorized synthetic dependencies,
and inspect retained results. It cannot launch a local application by itself.
Run `npx firedrill-run init` from your application's repository to set up the
Firedrill CLI. CLI authorization is separate; select the same intended
organization. For a new drill, use `plan`, `apply` and `run` after reviewing
the [quickstart](https://docs.firedrill.run/quickstart). Approve the exact local
plan before execution. Do not upload the target's source or credentials.

Simulations can be exploratory, observation-only, demonstrations, comparisons,
or tests. Exact checks suit hard constraints; semantic assessments allow valid
output variation. Always distinguish execution, observed outcome and assessment.
This connector does not provide a managed CI runner.

You can start on Firedrill's Free plan; target-model costs remain separate. This
directory contains public connector configuration and documentation only, under
the repository's thin-plugin MIT license. Firedrill's service remains closed
source. No hook, automatic trust rule, model provider, or credential is bundled.

To remove access, use `opencode mcp logout firedrill`, then remove only the
`mcp.firedrill` entry from your configuration. Remove an optional installed skill
separately through the same installer; preserve other settings.

[Firedrill documentation](https://docs.firedrill.run/)
· [OpenCode MCP guide](https://opencode.ai/docs/mcp-servers/)
· [OpenCode skills guide](https://opencode.ai/docs/skills/)
· [Privacy](https://firedrill.run/privacy)
· [Support](mailto:support@firedrill.run)
