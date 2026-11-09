---
name: switch-company-secretary
description: Use when the user wants to move an existing Malaysian Sdn Bhd to Foundingbird as its company secretary (a switch-in), or asks what switching costs.
---
# Switch company secretary to Foundingbird

1. `get_firm_overview`, then `describe_flow` with flow `switch-in-sdn-bhd`: learn the steps and fields (for example company details and the current secretary). Ask only for what the schema needs.
2. Price it: `list_packages` with flow `switch-in-sdn-bhd`, plus `estimate_quote` for the user's choices. Pass `flags` such as `requires_virtual_office` when list_packages asks. Quote only the tool's figures.
3. `start_application` with flow `switch-in-sdn-bhd`, then `update_application_step` per step. Fix refused fields and resend.
4. `get_application`: check that every step is complete. Show the terms and policy links and the declaration, and after an explicit "yes" call `submit_application` with `terms_accepted: true`.
5. `get_checkout` → `choose_package` → `create_handoff_link` with purpose `payment`. Use purpose `documents` for the switch-in's document upload, and `verification` / `signing` as `get_status` requires.
6. Explain that Foundingbird contacts the current secretary and collects the records. Track with `get_status`.

Don't promise timelines or fee waivers unless a tool returns them.
