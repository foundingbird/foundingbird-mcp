---
name: incorporate-sdn-bhd
description: Use when the user wants to incorporate (register) a new Malaysian Sdn Bhd with Foundingbird, check a proposed company name, pick MSIC codes, or get an incorporation quote.
---
# Incorporate a Sdn Bhd with Foundingbird

1. `get_firm_overview`: confirm the flow is `incorporation-sdn-bhd` and note the policy links.
2. `describe_flow` with flow `incorporation-sdn-bhd`: learn each step's fields. Ask only for what the schema needs, a few questions at a time.
3. Name: `check_company_name`. If `naming_problems` is non-empty, the name must change. `approval_warnings` are allowed, and the firm follows up on them. Tell the user SSM confirms availability when the firm files.
4. `start_application` (it resumes an open draft if there is one), then `update_application_step` for each step. If a field is refused, nothing was saved: fix it and resend.
5. After `company_details` is saved, poll `get_business_classification` until it's ready. Show the drafted description and MSIC codes for review (up to three codes). Use `search_msic_codes` for alternatives and `regenerate_business_classification` for a fresh draft.
6. `get_application`: confirm every step is complete.
7. Show the terms and policy links and the declaration that the application is true and complete. Only after an explicit "yes", call `submit_application` with `terms_accepted: true`.
8. `get_checkout`, then `choose_package` per step. Read the prices back from the tool and never estimate them. Before submitting, `list_packages` / `estimate_quote` can give an early quote.
9. `create_handoff_link` with purpose `payment`, then `verification` and `signing` as `get_status` requires. Payment, ID and signatures happen only on the website.
10. Later: `get_status` shows progress, whose move it is, and who still needs to verify or sign.

Never invent fees, timelines or approval outcomes.
