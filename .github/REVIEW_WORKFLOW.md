# Review-first GitHub change control (proposed)

Status: **PROPOSED — Draft PR; not effective until Eiden approves and merges.**

## Applicability and existing safeguards
This workflow applies to new findings, documentation, evaluations, features, fixes, dependency and configuration proposals in this repository. It supplements, and never overrides, existing AGENTS.md/CLAUDE.md, project TODO and inbox, protected-branch rules, ownership, environment/security gates, or explicit human-approval requirements. When existing rules are stricter (including separate preflight and fresh consent before any push or cross-project write), follow them first. An instruction to prepare a Draft PR does not itself authorize pushing where a fresh approval is required.

## Correct lifecycle
1. **Intake and scope:** Identify source, issue/finding, owner, repository, impacted files, dependencies, risk, privacy and acceptance criteria. Read project instructions and active TODO/inbox. Cross-project changes require separate accepted handoffs and required authorization.
2. **Prepare safely:** Make a focused review branch from the current target base, such as `review/<topic>-YYYYMMDD`, `eval/<topic>` or `fix/<topic>`. Keep unrelated work isolated. Never commit secrets, private data or generated artifacts. Respect configured hooks and contributor identity rules.
3. **Validate locally:** Perform the smallest safe tests and security checks available; record exact commands and evidence. Label unrun tests as **NOT RUN**, not passed. Do not start/stop services, install dependencies, access protected data, push or execute risky commands without applicable explicit approval.
4. **Publish for review:** Only after required push authorization, commit and push the review branch and create a GitHub **Draft PR** immediately against the correct base. A pushed branch without a PR is **AWAITING DRAFT PR**, not review complete. Keep one cohesive change per PR; link related PRs rather than silently writing to other repositories.
5. **Review gates:** PR includes purpose, evidence/source, change list, scope exclusions, security/privacy and cross-project impacts, tests (PASS/FAIL/NOT RUN), acceptance criteria, rollback, outstanding risks, owner decision and merge checklist. Run applicable CI and independent review. Reconcile with latest base if behind/diverged. Requested changes stay on the same Draft PR.
6. **Human decision:** Eiden explicitly approves readiness/merge and any security-sensitive or production-impacting execution as distinct decisions. An AI reviewer, CI success, previous scope approval or the Draft PR itself cannot grant these permissions. Keep draft until ready criteria are actually satisfied.
7. **Integrate and verify:** Merge only with the required current approval and branch protections. Any deployment/production operation needs its own authorization. Verify result, log follow-up and rollback outcome, and update the authoritative project TODO/handoff records.

## State vocabulary
`DISCOVERY` → `SCOPED` → `LOCAL REVIEW BRANCH` → `PUSH AUTHORIZED` → `DRAFT PR` → `VERIFIED` → `OWNER APPROVED` → `MERGED` → `POST-MERGE VERIFIED`. Use `BLOCKED` and `NOT VERIFIED` explicitly. Do not equate branch-pushed, PR-opened, reviewed, merged and deployed.

## Exceptions
Emergency or direct-commit workflows are not silently permitted by this policy; any exception requires explicit owner authorization and security impact review. Repository-specific approval requirements always take precedence. No automatic merge, deploy, protected-branch modification, approval bypass or service restart is authorized.
