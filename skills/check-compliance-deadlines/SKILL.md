---
name: check-compliance-deadlines
description: Use when the user asks what's due for their Malaysian company, about annual returns, financial statements, tax or beneficial ownership deadlines, or who still needs to act, for companies managed by Foundingbird.
---
# Check compliance deadlines

1. `list_companies`: find the company (use `com_…` ids). If there are several, ask which one. Status `left` means the company no longer uses Foundingbird.
2. `get_company`: read `attention` (overdue, waiting on the user, due soon) first, then `upcoming`. Give each deadline's `owner`: `cosec` means Foundingbird handles it, `you` means the user, and `tax_agent` or `auditor` means another adviser.
3. For any deadline the user asks about, or one owned by `you`, call `explain_deadline` with its `deadline_key`. It gives what the deadline is, the authority, what to do, the penalty for missing it, and who has or hasn't done their part.
4. Act through `needs_you` → `create_company_link` (purposes: `annual_return`, `signing`, `verification`, `invoices`). Approvals and signatures happen on the website, not in chat.
5. Related: `list_signing_requests` (who has signed), `list_invoices` (outstanding, with `create_billing_link` to pay), `list_letters` (new registered-office mail; titles only).

Only report dates and penalties the tools return. If a tool returns none, say so rather than guessing.
