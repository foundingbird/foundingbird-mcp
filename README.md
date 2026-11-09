# Foundingbird MCP server

![Foundingbird](assets/logo.png)

**Incorporate and manage your Malaysian Sdn Bhd from your AI**

Foundingbird's MCP server lets you incorporate and manage your Malaysian Sdn Bhd straight from your AI assistant. Start a new incorporation, pull your SSM documents, make company secretary requests and keep on top of every compliance deadline, all backed by Foundingbird's licensed company secretaries. ID checks, e-signing and payments stay in the secure Foundingbird portal and app.

**Server URL:** `https://portal.foundingbird.com/mcp` (remote, Streamable HTTP, OAuth)

Connecting is free. You sign in with your Foundingbird account, and can create one when you connect. Services are charged at Foundingbird's [published prices](https://foundingbird.com/my/).

## What you can do
- **Incorporate a Sdn Bhd:**
  - Check a proposed name against SSM's naming rules and see which words need an authority's approval. SSM confirms availability when we file.
  - Find MSIC codes, or review a drafted business description and codes.
  - Fill in and submit your incorporation application once you accept the terms.
- **Switch your company secretary:** move an existing Sdn Bhd to Foundingbird. We contact your current secretary and collect your records.
- **Packages and checkout:** see packages and add-ons with one-time and recurring totals including tax, choose packages, and get a secure payment link.
- **Track your application:** see each step, whose move it is, and who still has to verify their identity or sign.
- **Manage your company:**
  - See what needs you and your compliance deadlines, with the owner, what to do and the penalty for each.
  - Look up company particulars, directors and shareholders.
  - Pull SSM documents, Statutory Forms and Minutes Book documents.
  - Make company secretary (cosec) requests.
  - See registered-office letters, e-signing requests, invoices and outstanding balances.

Not available yet: company changes (directors, shares, address), certified true copies and SSM extracts. Request these in the Foundingbird portal.

## Setup
**Claude:** Customize → Connectors → + Add → Add custom connector → name it "Foundingbird", paste the URL → Add → Connect → sign in.

**ChatGPT:** Settings → turn on Developer mode → add a custom MCP server → paste the URL and choose OAuth → sign in. Needs a paid plan on the web.

**Grok:** [grok.com/connectors](https://grok.com/connectors) → New Connector → Custom → paste the URL → sign in.

**Cursor:** install this plugin, or add the following to `~/.cursor/mcp.json` (or the project's `.cursor/mcp.json`), then click Connect and sign in:
```json
{ "mcpServers": { "foundingbird": { "url": "https://portal.foundingbird.com/mcp" } } }
```

**Other clients:** add `https://portal.foundingbird.com/mcp` as a remote Streamable HTTP server with OAuth.

## Tools
| Group | Tools |
|---|---|
| Services and prices | `get_firm_overview`, `describe_flow`, `list_packages`, `estimate_quote` |
| Name and business activity | `check_company_name`, `search_msic_codes`, `get_business_classification`, `regenerate_business_classification` |
| Applications | `start_application`, `update_application_step`, `get_application`, `list_applications`, `submit_application`, `cancel_application`, `get_status` |
| Checkout and next steps | `get_checkout`, `choose_package`, `create_handoff_link` |
| Your companies | `list_companies`, `get_company`, `explain_deadline`, `get_company_particulars`, `get_company_registers`, `create_company_link` |
| Documents, mail, signing, billing | `find_company_documents`, `create_document_link`, `list_letters`, `list_signing_requests`, `list_invoices`, `create_billing_link` |

## Example prompts
1. "Incorporate a Sdn Bhd called Kopi Labs with me and my co-founder as directors, 50/50."
2. "Is the name 'Kopi Labs' OK under SSM's naming rules?"
3. "What's due for my company in the next 3 months, and whose job is each one?"
4. "What's the status of my incorporation, and what do I still need to do?"
5. "Switch my company's secretary to Foundingbird."
6. "Get me the SSM documents for my company."

## What's in this repo
- `assets/logo.png`: Foundingbird shield logo (512×512).
- `mcp.json`, `.cursor/mcp.json`: the remote server config.
- `.cursor-plugin/plugin.json`: the Cursor plugin manifest.
- `skills/`: guided flows for incorporation, compliance deadlines and switching company secretary.
- `rules/foundingbird.mdc`: safe-use rules for agents.
- `server.json`: the entry for the official MCP Registry.

## Security
- You sign in with OAuth. Your assistant never sees your password, and you can disconnect at any time.
- Identity verification, document uploads, e-signatures and payment happen only in your Foundingbird portal through secure links, never in chat.
- Your assistant sees document and letter names and dates, not their contents. Registers include no ID numbers or contact details.
- Applications are only submitted, and drafts only cancelled, after you explicitly confirm.

## Support and links
- Support: hello@foundingbird.com
- MCP page: https://foundingbird.com/my/mcp/
- Logo: https://foundingbird.com/assets/images/foundingbird-favicon-shield.png
- Privacy: https://foundingbird.com/my/policies/privacy-policy/
- Terms: https://foundingbird.com/my/policies/terms-of-service/

Foundingbird Sdn Bhd, SSM 201901035214 (1344544-U). The MIT license in this repo covers the docs and config only.
