# Checkout.com MCP Server

**Give your AI agent a working knowledge of Checkout.com** — the current API reference, the
integration guides, and the ability to act on real payments, without leaving your editor.

[![Install in VS Code](https://img.shields.io/badge/Install%20in-VS%20Code-0098FF?style=for-the-badge)](https://insiders.vscode.dev/redirect/mcp/install?name=checkout&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.checkout.com%22%7D)
[![Install in Cursor](https://img.shields.io/badge/Install%20in-Cursor-000000?style=for-the-badge)](https://cursor.com/install-mcp?name=checkout-mcp&config=eyJ1cmwiOiJodHRwczovL21jcC5jaGVja291dC5jb20iLCJhdXRoIjp7IkNMSUVOVF9JRCI6ImNoZWNrb3V0LW1jcCJ9fQ%3D%3D)

Or, in Claude Code:

```bash
claude mcp add --transport http checkout-mcp https://mcp.checkout.com
```

Then sign in with your Checkout.com Dashboard account. It's a remote server — nothing to install,
host, or keep updated, and no API keys to paste into a config file.

## Why use it

Ask a general-purpose coding agent to integrate a payments API and it will improvise: invented
fields, endpoints that no longer exist, request bodies that look right and fail in testing. This
server replaces that guesswork with grounded answers.

- **It reads our actual documentation.** The technical docs, the complete API reference, and the
  support knowledge base — the live versions, not a stale snapshot from a training run.
- **It recommends a real integration path.** Describe your use case and stack, and get a route
  matched to it, rather than the one generic tutorial that happened to rank highest.
- **It acts, not just advises.** Check a payment, refund it, void an authorization, or create a
  payment link — from a plain-language request against your own account.
- **It costs less per answer.** Purpose-built, AI-optimized context instead of scraped HTML means
  fewer tokens burned and faster replies.

## What you can ask

Your MCP client shows the full tool list the moment it connects.

**Build and debug your integration**

> Which API operations and fields do I need to take a payment with PayPal?

**Operate live payments**

> What's the status of payment `pay_xxxxx`?

> Refund payment `pay_xxxxx`.

## Environments

| Environment | URL |
|---|---|
| Production | `https://mcp.checkout.com` |
| Sandbox | `https://checkout.mcp.sbox.cko.tech` |

## Access and permissions

You need an active [Checkout.com Dashboard](https://dashboard.checkout.com) account. Authentication
is OAuth 2.0: your client discovers the authorization server and opens a browser for you to sign in. 
No API keys are involved.

The agent inherits your permissions and nothing more. It can only perform an operation your
Dashboard user is already allowed to perform — to refund a payment, for instance, your user needs
the **Refund payments**
[permission](https://www.checkout.com/docs/business-operations/use-the-dashboard/manage-users/user-permissions).

<details>
<summary><b>Manual setup</b></summary>

**Claude Desktop / Claude Code** — add the server, then run `/mcp` to trigger the sign-in flow:

```bash
claude mcp add --transport http checkout-mcp https://mcp.checkout.com
```

**VS Code** — open the Command Palette, run `MCP: Open User Configuration`, and add:

```json
{
  "servers": {
    "checkout-mcp": {
      "url": "https://mcp.checkout.com"
    }
  }
}
```

Save, then run `MCP: List Servers`, select the Checkout MCP, and choose **Start** to sign in.

**Cursor** — add to `~/.cursor/mcp.json`, or your project's `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "checkout-mcp": {
      "url": "https://mcp.checkout.com",
      "auth": {
        "CLIENT_ID": "checkout-mcp"
      }
    }
  }
}
```

To disconnect, disable the server in your client's MCP settings or delete it from the config file.

</details>

## Documentation and support

- [Setup guide](https://www.checkout.com/docs/developer-resources/checkout-com-mcp-server)
- [Checkout.com documentation](https://www.checkout.com/docs) 
- [API reference](https://api-reference.checkout.com)
- Questions or feedback: talk to your account manager or [contact support](https://support.checkout.com)

---

<sub>This repository holds the `server.json` metadata that lists the server in the
[official MCP Registry](https://registry.modelcontextprotocol.io). The server itself is
hosted and operated by Checkout.com</sub>
