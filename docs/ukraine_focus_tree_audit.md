# Ukraine Focus Tree Scaffold Audit

Date: 2026-04-25 (UTC)

Scope audited:
- `common/national_focus/ukraine.txt`
- `localisation/english/MD_UKR_focus_l_english.yml`
- `README.md`
- Repository-wide search for `events`, `decisions`, `ideas`, `scripted_effects`, `scripted_triggers`, `ai_strategy_plans`

## 1) Current file inventory

### Present scaffold files
- `common/national_focus/ukraine.txt`
- `localisation/english/MD_UKR_focus_l_english.yml`
- `README.md`
- `docs/Codex Workflow Testing.docx`

### Repository search results for requested content categories
Searched for the following patterns and paths:
- `events`
- `decisions`
- `ideas`
- `scripted_effects`
- `scripted_triggers`
- `ai_strategy_plans`

Result: **no matching files or directories currently exist in this repository**.

## 2) Focus count

- Total focuses in `ukraine_focus` tree: **38**.

## 3) List of all focus IDs

1. `UKR_ukraine_elections`
2. `UKR_kucha_second_terms`
3. `UKR_reform_programm`
4. `UKR_reform_national_guard`
5. `UKR_reform_vsu`
6. `UKR_check_and_balances`
7. `UKR_const_reform`
8. `UKR_push_for_reforms`
9. `UKR_seek_help_eastern_oligarch`
10. `UKR_seek_help_western_investors`
11. `UKR_join_eu_market`
12. `UKR_secure_eastern_trade`
13. `UKR_balance_foreign_policy`
14. `UKR_rebuild_industry`
15. `UKR_independence_referendum`
16. `UKR_build_state_institutions`
17. `UKR_lisbon_protocol`
18. `UKR_budapest_memorandum`
19. `UKR_constitution_1996`
20. `UKR_contested_2004_election`
21. `UKR_orange_revolution`
22. `UKR_reformist_mandate`
23. `UKR_power_vertical`
24. `UKR_suspend_eu_talks`
25. `UKR_euromaidan_protests`
26. `UKR_support_maidan`
27. `UKR_crack_down_maidan`
28. `UKR_sign_association_agreement`
29. `UKR_anti_corruption_drive`
30. `UKR_visa_free_travel`
31. `UKR_church_autocephaly`
32. `UKR_covid_emergency`
33. `UKR_imf_stabilization`
34. `UKR_seek_nato_membership`
35. `UKR_fortify_border`
36. `UKR_general_mobilization`
37. `UKR_secure_western_aid`
38. `UKR_liberate_territories`

## 4) Missing localisation keys, if any

Check performed against both name and description keys (`<focus_id>` and `<focus_id>_desc`).

- Missing localisation keys: **none found**.

## 5) Duplicate focus IDs, if any

- Duplicate focus IDs: **none found**.

## 6) Suspicious prerequisite chains

No outright invalid references were observed in this scaffold, but these chains are noteworthy for later implementation checks:

1. **Dual prerequisite bottlenecks** (intentional but high-impact):
   - `UKR_check_and_balances` requires both `UKR_reform_national_guard` and `UKR_reform_vsu`.
   - `UKR_balance_foreign_policy` requires both `UKR_join_eu_market` and `UKR_secure_eastern_trade`.
   - `UKR_covid_emergency` requires both `UKR_euromaidan_protests` and `UKR_orange_revolution`.

2. **Temporal compression risk** (historical arcs merged into one linear tree):
   - The path from early-statehood focuses to post-2014 and post-2020 focuses is linearized. This is acceptable for a scaffold, but later tasks may need explicit flags/events to avoid ahistorical sequencing in alternate paths.

3. **Potential branch dead-end by design**:
   - `UKR_sign_association_agreement` is reachable only via `UKR_support_maidan`; the crack-down branch has no alternate continuation into EU integration nodes (likely intentional for narrative split).

## 7) Mutually exclusive branch checks

Mutual exclusivity blocks appear correctly mirrored in both branch pairs:

- `UKR_reformist_mandate` ⟂ `UKR_power_vertical`
- `UKR_support_maidan` ⟂ `UKR_crack_down_maidan`

No one-sided or broken exclusivity declarations found.

## 8) Placeholder/simple rewards for later scripted effects or ideas

The scaffold predominantly uses simple numeric rewards (`add_stability`, `add_war_support`, `add_political_power`, `add_army_experience`).

Candidate focuses for future conversion to scripted effects/ideas (without changing mechanics yet):

- Governance/constitutional milestones:
  - `UKR_check_and_balances`
  - `UKR_const_reform`
  - `UKR_constitution_1996`
- Historical diplomatic/security milestones:
  - `UKR_lisbon_protocol`
  - `UKR_budapest_memorandum`
  - `UKR_seek_nato_membership`
- Crisis/transition moments:
  - `UKR_orange_revolution`
  - `UKR_euromaidan_protests`
  - `UKR_covid_emergency`
  - `UKR_general_mobilization`
- Integration/state identity items:
  - `UKR_sign_association_agreement`
  - `UKR_anti_corruption_drive`
  - `UKR_church_autocephaly`

Reason: these represent state changes better modeled as flags, idea swaps, country modifiers, or scripted effect bundles later.

## 9) Existing repository patterns to reuse in later tasks

Observed patterns already present and worth preserving:

1. **Naming conventions**
   - Focus IDs consistently use `UKR_` prefix.
   - Localisation keys mirror focus IDs with `_desc` companion keys.

2. **Tree organization style**
   - Sectioned comments for thematic branches (starter, statehood, Orange Revolution, Euromaidan, EU identity, modern defense).

3. **Branch structure style**
   - Symmetric `mutually_exclusive` definitions for branch forks.
   - Convergence nodes using multiple `prerequisite` lines.

4. **Documentation pattern**
   - `README.md` already describes content scope and suggests iterative next steps (scripted effects, events/decisions, AI plans, triggers).

## 10) Recommended next task

**Next recommended task:**

Introduce non-invasive script scaffolding files (empty/minimal but valid structures) for:
- `common/scripted_effects/`
- `common/scripted_triggers/`
- `common/ideas/`
- `events/`
- `common/decisions/`
- `common/ai_strategy_plans/`

Then wire only a small pilot subset of focus rewards (e.g., 2–3 milestone focuses) to placeholder scripted effects while preserving current gameplay balance behavior.

This follows the README roadmap and prepares the tree for modular expansion without changing core branch logic yet.

## Follow-up: country flag wiring

Added **21 milestone country flags** to `common/national_focus/ukraine.txt` completion rewards:

- `UKR_completed_independence_referendum`
- `UKR_completed_lisbon_protocol`
- `UKR_completed_budapest_memorandum`
- `UKR_adopted_1996_constitution`
- `UKR_orange_revolution_happened`
- `UKR_chose_reformist_mandate`
- `UKR_chose_power_vertical`
- `UKR_euromaidan_happened`
- `UKR_supported_maidan`
- `UKR_cracked_down_maidan`
- `UKR_signed_eu_association_agreement`
- `UKR_anti_corruption_drive_started`
- `UKR_achieved_visa_free_travel`
- `UKR_supported_church_autocephaly`
- `UKR_covid_emergency_measures`
- `UKR_imf_stabilization_program`
- `UKR_sought_nato_membership`
- `UKR_fortified_border`
- `UKR_general_mobilization_ordered`
- `UKR_secured_western_aid`
- `UKR_liberation_campaign_started`

These flags are intended as lightweight state markers for later integration with events, decisions, scripted triggers, scripted effects, and AI strategy plans.

## Follow-up: scripted trigger scaffolding

Added scripted triggers for all **21** Ukraine milestone country flags in `common/scripted_triggers/UKR_milestone_scripted_triggers.txt`.

These scripted triggers should be used as the standard checks in future events, decisions, scripted effects, and AI strategy plans so milestone-state conditions stay centralized and consistent instead of repeating raw `has_country_flag` checks.

## Follow-up: event scaffold

Added four triggered-only milestone country events:
- `ukr_expanded.1`
- `ukr_expanded.2`
- `ukr_expanded.3`
- `ukr_expanded.4`

These events are not wired to focus completion rewards yet.

Event wiring should be done in a later pass once trigger/condition flow and gameplay integration are finalized.

## Follow-up: 2000s event scaffold

Added six triggered-only Ukraine 2000s political events:
- `ukr_expanded.20` — Kuchma's Second Term
- `ukr_expanded.21` — The Cassette Scandal
- `ukr_expanded.22` — Oligarchic Media Networks
- `ukr_expanded.23` — The 2004 Presidential Election
- `ukr_expanded.24` — Yushchenko Poisoned
- `ukr_expanded.25` — Constitutional Reform, 2004

These events are not wired to focus completion rewards yet.

Because Millennium Dawn starts in 2000, this pass begins with Kuchma-era Ukraine rather than the 1990s.

## Follow-up: 2000s event wiring

This pass wires six existing 2000s political events into existing focus completion rewards.

- `UKR_kuchma_second_terms` fires `ukr_expanded.20`
- `UKR_reform_programm` fires `ukr_expanded.21`
- `UKR_push_for_reforms` fires `ukr_expanded.22`
- `UKR_contested_2004_election` fires `ukr_expanded.23`
- `UKR_orange_revolution` fires `ukr_expanded.24`
- `UKR_const_reform` fires `ukr_expanded.25`

Notes:
- This pass does not add gameplay effects to event options.
- This pass does not alter branch structure or focus rewards.
