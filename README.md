<p align="center">
  <img src="assets/kleap-logo.svg" alt="Kleap" width="180">
</p>

# Kleap for Grok Bot

Build, edit, publish, and maintain websites, apps, internal tools, and other web products from Grok Bot through Kleap's hosted Model Context Protocol server.

The plugin connects to:

```text
https://kleap.co/api/mcp
```

Authentication uses Kleap OAuth in the browser. No API key or bearer token needs to be copied into the plugin.

## What it provides

- Create websites, web apps, dashboards, and internal tools.
- Inspect projects, source files, credits, and deployment state.
- Apply targeted source edits while preserving unrelated content.
- Publish through Kleap hosting and verify the observed live deployment.
- Read analytics, Search Console performance, and saved form submissions.
- Connect domains the user already owns after explicit authorization.

## Install in Grok Bot

After marketplace approval, open **Plugins** in the Grok Bot sidebar, find **Kleap**, and select **Install**. Grok Bot and Cursor use the same account and installed plugins.

On first use, complete the Kleap OAuth flow in your browser. Start with a read-only request:

> Using Kleap, list my projects and show the publishing status of the project I choose. Do not modify or publish anything.

## Grok Build compatibility

The same repository also includes a native Grok Build manifest. It can be installed directly from GitHub while its separate xAI marketplace review is pending:

```sh
grok plugin install kleaphq/kleap-grok-plugin --trust
```

After xAI marketplace approval, open `/marketplace` in Grok Build and install **Kleap**.

## Validation

The package follows Cursor's plugin structure and includes a native Grok Build package. Before release, validate the Grok Build package with:

```sh
grok plugin validate .
```

Then test one read-only workflow and one targeted edit on a dedicated demo project. Publishing remains a separate, explicitly authorized action, and the result is described as live only after deployment verification.

## Safety

- Existing files are read before editing.
- Precise changes use the smallest exact replacement.
- Credit-consuming creation and every publication, domain connection, or deletion require clear authorization.
- Credentials stay in the OAuth flow and never belong in prompts, source files, or logs.
- Read-only analytics and form-submission requests do not modify the project.

## Documentation and support

- Product and connector guide: https://kleap.co/mcp
- Documentation: https://docs.kleap.co
- Privacy policy: https://kleap.co/privacy-policy
- Support: hello@kleap.co

## License

MIT. See [LICENSE](LICENSE).
