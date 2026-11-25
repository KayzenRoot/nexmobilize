# NMO-CORE-WO-001 — Conditional one-shot executor
**Status:** PREPARED / BLOCKED. Risk HIGH_ASSURANCE. Issue #3. Phase A is correction NMO-BOOTSTRAP-001/CD-01, issue #2, PR #1; phase B is CORE and must not start before independent APPROVED + squash merge of bootstrap and fresh Context Lock.

## OBJECTIVE
Close bootstrap evidence and governance in its existing PR; only on a subsequent invocation after independently approved bootstrap merge, implement the first functional foundation, not the whole MVP.

## CONTEXT / SOURCE CHECK / CONTEXT LOCK
Repository KayzenRoot/nexmobilize; initial main 3e15fd3f14ba69a69d7fd0b99febf01ef732bc1a; audited original PR #1 HEAD 7c6a160d4db2d4a52a645013395da918f21e6ce3; workflow commit 20df7cff7fad9766007741131e14b06a57924d78. Read actual PR head including this file; verify descendant and no unrelated drift; lock fresh exact SHA and critical file hashes before edits. Baseline Git blobs at workflow commit:
- README.md 675810b51cecae28655969a9e9a4d42b74053003
- docs/checkpoint.md 4eda8f844c9b1040470857b5723ef4981151b006
- docs/decisions.md 8c438dbb7c17f75f7be2d20266f257b1361e63c1
- docs/scope.md 98dbee9d7f97b178c70dde42276563fae0daaf4d
- docs/dod.md f0201421a301f38708077ae5270178b3d1ed9670
- docs/architecture.md 32a1d92d6929b1c1943dec819d3c4818f5171dea
- docs/requirements.md eafb5fe74d7a37c7af84838cec4ccca98b2bd43a
- docs/security.md 7b0a53c1da3dd14496b1324ede22053ff393e36a
- docs/data-model.md 9fb8a255e60c616fc0d062d4e5b023fe82e9a97a
- docs/governance.md 63da881260dbd06013ed3b1f3633306b8bf48d47
- .github/workflows/docs-validation.yml 10c13eac07888a4925ca52240b34cd7bd870c368
Use git rev-parse, git hash-object and SHA256 evidence. Read all 18 canonical files, workflow, issues #2–11 and PR #1; inspect local git status/remote/auth; preserve user changes, no reset or force. If relevant drift not explained by approved corrections, STALE and stop. The user ratified MVP direction, not all specific stack versions, hosting or prices.

## Phase A — NMO-BOOTSTRAP-001/CD-01
Audit of original PR: 18/18 documents read from diff; all 10 issues #2–11 match backlog IDs and dependencies. Source pack structurally present; no runtime implementation. GitHub API reported public repository, admin rights, squash allowed but merge and rebase also allowed; original HEAD had zero checks/workflows. Official docs establish free standard runners for public repos and free public-repo rulesets:
https://docs.github.com/en/actions/concepts/billing-and-usage
https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets
Actual settings require authenticated read-back. Newly added docs-validation workflow not yet proven green. Overall CORRECTION REQUIRED/BLOCKED until findings resolved:
- F01 HIGH governance: read current repository settings, rulesets, branch protection, Actions permissions with gh api; preserve unrelated protections. Configure main active ruleset: require PR, prohibit force-push and deletion, require docs-validation check after it actually exists, no bypass actors; squash enabled, merge/rebase disabled, avoid mandatory external reviewer that cannot be satisfied (independent chat audit remains mandatory). Verify API read-back with IDs, enforcement, checks and merge modes; do not use admin bypass. If permissions or verified no-cost eligibility absent, BLOCKED, report exact error; do not purchase. Never expose tokens.
- F02 HIGH CI evidence: inspect workflow; run its checks locally, test failure by removing required file in temporary copy, validate YAML; verify exact event commit fetch, read-only permissions, no secrets, no paid/larger runners, no deployment, no artifacts billed. Trigger PR CI through authorized normal push/update, inspect runs/jobs tied to latest head/merge event and logs; no fabricated green. If needed fix workflow in same PR, with pinned verified action SHA if replacing direct git fetch. Do not use pull_request_target. Ensure check name exact and then enforce F01. No unsafe workflow edits from forks.
- F03 HIGH tenant boundary ambiguity: clarify data model global identity User vs tenant-scoped Membership and operational rows; no globally accessible operational data; cross-tenant composite FKs, least-privileged non-owner runtime DB role without BYPASSRLS, FORCE RLS where applicable, transaction-local verified tenant context, fail closed missing context, separate migration role; do not implement in phase A. Clarify audit events retain only minimal pseudonymous metadata with approved retention and access restrictions; document deletion vs audit integrity policy without claiming legal compliance. No real data.
- F04 STANDARD traceability: add explicit R01–R12/NFR01–04 -> responsible WO -> acceptance/evidence mapping including MFA before pilot, retention/deletion/export/incident R12 and backup/restore, review independence, pilot gate. Resolve distinction between demo acceptance, MVP deploy (authorized only), real pilot and commercial release. Document source dates as candidates and verify official references; no universal NR checklist. Pricing/hosting/provider remain hypotheses/proposed. Record ratification of MVP direction without blanket approval.
Phase A AC: 18 required docs preserved, 10 issues reconciled, F01–F04 evidence, green docs CI with actual required check and effective ruleset, no unrelated changes. Commit/push same branch PR #1, publish evidence with exact base/head, diff, commands, logs and proposed checkpoint delta. STOP for independent audit. Do not self-approve or merge or promote checkpoint. Do not start CORE when bootstrap is unmerged or blocked. If no GitHub credentials use existing authorized login or report BLOCKED; no paid plans or token exposure.

## Phase B — SCOPE (only after independently approved bootstrap squash merge)
Fresh main HEAD and critical canonical file hashes must replace provisional lock. Branch feat/nmo-core-wo-001; new PR referencing issue #3. Scaffold modular TypeScript web/API monolith, PostgreSQL migrations, local Docker Compose, reproducible toolchain and lockfile, minimum identity/tenant/membership/session/invite lifecycle, server authorization, RLS, privilege isolation, minimal login and tenant-switch UI, audit security events, health/readiness, CI and synthetic fixtures. Prefer maintained libraries over homemade cryptography; evaluate stable compatible versions and licenses from official sources; document ADR proposals and qualify no-cost prerequisites. If toolchain/auth choice needs material unapproved decision, stop with ADR proposal before irreversible work. No public endpoint or real data.

## OUT OF SCOPE
No workers/contracts/policies/document upload/OCR/AI/jobs beyond CORE necessity, no real customer or health data, portal access, billing, paid services, public deployment, remote database, external LLM, additional modules or automatic merge. No broad cleanup or secret publication.

## REQUIREMENTS / ARCHITECTURE RULES
R01 and NFR01 (CORE portion), NFR02 basic accessibility, security and data model rules, AC01. Global identity plus tenant-scoped memberships; explicit role matrix (tenant admin, operator, reviewer, viewer; platform admin separately restricted); every route/action authorized server-side, no trusting tenant_id from request, tenant switches verify membership and session; RBAC deny by default. Runtime DB role non-owner, no superuser/BYPASSRLS, migration separate; RLS on operational tenant tables, composite tenant constraints, transactional context isolation across pooled connections; no user-controlled session claims. Session secure HttpOnly/SameSite cookie, Secure in TLS environment, rotation/revocation/expiration, CSRF/origin checks on mutations, safe credential hashing using maintained library (if password-based), rate limit login, generic errors; one-time expiring invites stored hashed, revoked membership denies next request. No public registration by default, no default real passwords. Explicitly mark MFA privileged before pilot as outstanding unless implemented and proven; no pilot allowed. Minimal audit logs with no credentials, PII or session tokens. Compose binds local only, secrets generated locally and ignored, health checks, reproducible migrations; use existing tooling and zero-cost only.

## ACCEPTANCE CRITERIA (AC01 proof obligations)
AC01.1 fresh clone reproducible install/build/typecheck/lint; pinned lockfile/images or explicit immutable digests and verified versions; license evidence.
AC01.2 local Compose services healthy; clean PostgreSQL migration and repeat migration behavior; two isolated synthetic tenants; no public listening interface except loopback.
AC01.3 authentication success/failure, secure session lifecycle, one-time invitation, expiry/replay/revocation, disabled memberships, rate limit, CSRF; no secret logging; clear demo-only mode.
AC01.4 role matrix and tenant switching verified, every protected endpoint denies unauthenticated/unauthorized requests, no cross-tenant read/write/list by app API and direct restricted SQL; absent context fail closed; pool reuse/concurrency tests; runtime owner/superuser/BYPASSRLS negative proof.
AC01.5 responsive pt-BR login + basic authorized tenant dashboard, keyboard and accessible error/empty states; no future module mock pretending functional.
AC01.6 CI docs + runtime checks with actual green runs on PR SHA, unit, integration PostgreSQL, E2E, dependency/secret/SAST/SBOM checks with verified free availability; no HIGH/CRITICAL known; independent security audit required before approval.
AC01.7 baseline measured and declared limitations; exact setup/teardown instructions, schema/API docs, ADR proposals, evidence and checkpoint delta. No deployment or real-data claim.

## TESTS
Unit role permission matrix/session/invite expiry/replay, validation, errors. Real PostgreSQL integration with migrations, role privileges, tenant context, FKs and negative RLS on SELECT/INSERT/UPDATE/DELETE; pool isolation and revoked membership. E2E login/logout, switch authorized tenants, reject unauthorized tenant and role, invite and expiry. CSRF/session fixation, brute-force throttling, unauthenticated access, SQL injection regression, no secrets in logs. Build/lint/typecheck, dependency/secret/SAST and SBOM. No tests skipped to manufacture pass. Record commands, versions, counts and exact head. No network to real systems.
## DELIVERABLES
Branch, commits, push, draft PR; reproducible source/lockfile/migrations/Compose/tests/CI; docs delta and evidence in pt-BR. Evidence Bundle base/head SHAs, source fingerprints, file list, architecture/security decisions, tests and actual CI run URLs, role/RLS negative proofs, cost/license evidence, failures corrected, residual risks, checkpoint delta proposed. No self-promotion.
## REVIEW FORMAT
Português brasileiro: VEREDITO PROPOSTO (READY FOR INDEPENDENT AUDIT / CORRECTION REQUIRED / BLOCKED), Context Lock, findings severity and evidence, AC01.1–7 matrix, test counts/commands, CI links, diff and risk, checkpoint delta. Only independent audit can APPROVE. Stop at first unresolved gate; no next increment.
