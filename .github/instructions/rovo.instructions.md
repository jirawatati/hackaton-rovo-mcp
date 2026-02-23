---
description: Install and configure the Atlassian Rovo MCP Server on VS Code
---

# Install Atlassian Rovo MCP Server on VS Code

This workflow guides an AI Agent through installing and configuring the Atlassian Rovo MCP Server for VS Code, enabling integration with Jira, Confluence, and Compass.

> **Reference**: https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/

---

## Prerequisites

Before starting, verify the following:

1. **Check Node.js version** (must be v18+):
// turbo
```bash
node --version
```
If Node.js is not installed or below v18, install it via `brew install node` or from https://nodejs.org.

2. **Check npx is available**:
// turbo
```bash
npx --version
```

3. **Confirm access to an Atlassian Cloud site** with Jira, Compass, and/or Confluence.

4. **Ensure VS Code is installed** with GitHub Copilot extension (for MCP support).

---

## Installation (Choose ONE Option)

### Option A: VS Code MCP Directory (Recommended)

1. Open a browser and navigate to https://code.visualstudio.com/mcp
2. Search for the **Atlassian Rovo MCP provider** and install it from the marketplace.
3. This will automatically add the MCP server configuration to VS Code.

### Option B: VS Code Command Palette

1. Open VS Code.
2. Open the **Command Palette** (`Cmd+Shift+P` on macOS).
3. Run the command: `MCP: Add Server`
4. Select **Http** or **Server-sent Events** as the connection type.
5. Enter the server URL:
   ```
   https://mcp.atlassian.com/v1/mcp
   ```
6. Provide a name for the server:
   ```
   atlassian-mcp-server
   ```

### Option C: Manual `mcp.json` Configuration

1. Create or edit the `mcp.json` file in your workspace root (`.vscode/mcp.json`) or user-level settings:

```json
{
  "servers": {
    "atlassian-mcp-server": {
      "url": "https://mcp.atlassian.com/v1/mcp",
      "type": "http"
    }
  },
  "inputs": []
}
```

2. Save the file and reload VS Code (`Cmd+Shift+P` → `Developer: Reload Window`).

---

## Authentication

After adding the server, VS Code will trigger the **OAuth 2.1 authorization flow**:

1. A browser window will open automatically requesting Atlassian authorization.
2. **Sign in** with your Atlassian account.
3. **Grant permissions** for the MCP server to access Jira, Confluence, and/or Compass.
4. Return to VS Code — the connection should now be active.

> [!NOTE]
> - If using **API token** authentication instead of OAuth, generate one at:
>   https://id.atlassian.com/manage-profile/security/api-tokens?autofillToken&expiryDays=max&appId=mcp&selectedScopes=all
> - The first user to complete the OAuth flow on your Atlassian site must have access to all requested apps (e.g., both Jira and Confluence).

---

## Verification

After setup, verify the connection works by testing these commands in GitHub Copilot Chat:

1. **Test Jira**: Ask Copilot: `"Find all issues assigned to me in the last 7 days"`
2. **Test Confluence**: Ask Copilot: `"What Confluence spaces do I have access to?"`
3. **Test Compass**: Ask Copilot: `"What depends on the api-gateway service?"`

If the MCP server is working, you should receive real Atlassian data in the response.

---

## Fallback: Using mcp-remote Proxy

If the direct HTTP/SSE connection doesn't work, use the `mcp-remote` proxy:

1. Run the proxy in your terminal:
// turbo
```bash
npx -y mcp-remote@latest https://mcp.atlassian.com/v1/mcp
```

2. Complete the OAuth flow in the browser when prompted.

3. Update your VS Code `mcp.json` to use the proxy:
```json
{
  "servers": {
    "Atlassian-Rovo-MCP": {
      "command": "npx",
      "args": ["-y", "mcp-remote@latest", "https://mcp.atlassian.com/v1/mcp"]
    }
  }
}
```

4. **Keep the terminal session running** while using the IDE.

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **"Your site admin must authorize this app"** | A site admin must complete the OAuth flow first before other users can connect. |
| **"Your organization admin must authorize access from a domain"** | An org admin must add the domain in Atlassian Rovo MCP server settings. See [Control settings](https://support.atlassian.com/security-and-access-policies/docs/control-atlassian-rovo-mcp-server-settings/). |
| **"You don't have permission to connect from this IP"** | IP allowlisting is enabled — ask admin to add your IP/VPN range. |
| **Token expired** | Re-run the `mcp-remote` command or re-authenticate via the OAuth flow. |
| **App not appearing in Connected apps** | Verify you're using the correct Atlassian account and site with proper permissions. |
| **MCP tools not showing in Copilot** | Ensure VS Code MCP support is enabled in settings and restart VS Code. |

---

## Security Notes

- All traffic is encrypted via **HTTPS (TLS 1.2+)**.
- OAuth 2.1 ensures secure authentication; all actions respect existing Atlassian user permissions.
- Data access follows Jira/Confluence/Compass project and space-level roles.
- IP allowlisting rules are honored by the MCP server.

---

## Example Workflows After Setup

| Category | Example Prompt |
|----------|----------------|
| **Jira - Search** | "Find all open bugs in Project Alpha" |
| **Jira - Create** | "Create a story titled 'Redesign onboarding'" |
| **Jira - Bulk** | "Make five Jira issues from these notes" |
| **Confluence - Read** | "Summarize the Q2 planning page" |
| **Confluence - Create** | "Create a page titled 'Team Goals Q3'" |
| **Compass - Query** | "What depends on the api-gateway service?" |
| **Combined** | "Link these three Jira tickets to the 'Release Plan' page" |