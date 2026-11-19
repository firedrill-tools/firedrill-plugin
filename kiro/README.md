# Firedrill power

Connect Kiro to Firedrill to prepare and inspect simulations of the AI agent
you're building. Open **Powers → Add Custom Power → Import power from GitHub**:

```text
https://github.com/firedrill-tools/firedrill-plugin/tree/main/kiro
```

Review the remote connection, then complete Kiro's native MCP browser sign-in
for the intended Firedrill organization. No token or model key belongs in chat.
This power declares one Streamable HTTP remote and contains no executable,
install hook, bundled credential or automatic tool-approval rule.

You can start on Firedrill's Free plan; your application's model costs are separate.
The remote connector prepares simulations and inspects reports. Execution of
your application uses the separately authorized Firedrill CLI on your machine.
See the [quickstart](https://docs.firedrill.run/quickstart) for the
`plan`, `apply` and `run` workflow and exact local-plan approval.

Direct import is separate from acceptance into Kiro's curated registry.

Support: [support@firedrill.run](mailto:support@firedrill.run).
[Privacy](https://firedrill.run/privacy) · [Terms](https://firedrill.run/terms).

The thin power is covered by this repository's [MIT license](../LICENSE).
Firedrill's service, CLI and SDKs remain separately licensed and closed source.
