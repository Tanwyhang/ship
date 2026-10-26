---
name: ship
description: Take a project's PR or reviewed change through merge gates, authorized deployment, connected feature verification and handoff. Discover the repository and release process instead of assuming a provider or stack. Use for shipping requests; prefer a matching project-specific shipping skill when available.
---

# Discover → merge → deploy → prove

Carry the user's approved change through the project's actual release process.
Do not assume GitHub, a branch named main, Kubernetes, GitOps, a particular cloud,
or that publishing an artifact deploys it to users.

## Discover the project and establish scope

Inspect the workspace, Git roots/remotes, applicable repository instructions,
manifests, release documentation and CI/CD definitions. In a monorepo or
multi-repository release, identify the affected component, consumers and host
activation/pin steps. Use a matching installed project/provider release skill
when applicable; do not import another project's commands, accounts or defaults.

Resolve the PR/change, reviewed source, destination environment/account/region,
authorized actions and test budget from the request and saved evidence. Prefer
read-only discovery before questions. If several plausible projects or targets
remain, ask before mutation. Never default an unspecified deployment to production.
Invoking this skill does not grant unspecified deployments, permission changes,
live data writes or rollback. Do not repeat requests for clearly approved scope.

Preserve dirty work and other developers' changes. Reuse existing release records
or an appropriately scoped local checkpoint: source/head, approvals, merge result,
workflow/deployment IDs, artifact, serving target, proof and cost reservations.
On resumption, inspect those milestones before repeating a merge, dispatch or test.
Store no tokens or credentials in the record.

## Reconcile and pass the gates

Fetch the relevant target branch/tags and compare the exact current change with
its base. Review applicable checks, required reviews, security gates and local
test instructions. If the head changes, rerun affected validation and refresh its
gates. Fix reproducible failures narrowly; do not include unrelated upgrades or
deferred work merely to make a gate pass.

Merge only when authorized and all applicable gates pass, using normal repository
protection and exact-head/concurrency safeguards where supported. Already merged
means inspect the merge result, not merge again. Skipped checks are not passes;
verify whether they are applicable. Never force-push, admin-merge or bypass gates.

## Release the exact reviewed scope

Discover the current serving artifact and its source. Inspect the complete release
delta, including intervening changes, configuration, dependencies and migrations.
A feature's merge approval does not approve deploying unrelated intervening work.
Stop for material unapproved scope, ambiguous mapping or an unsafe release path.

Verify baseline health and record the exact known-good artifact/configuration
revision and available normal recovery path. Check migration and persistent-data
compatibility: an image rollback alone may not reverse a release safely.
Do not initiate a live rollout without a trustworthy baseline and recovery plan.

Use the established release workflow from a verified reviewed ref. Record actual
run source and generated artifact/version; do not guess versions. Check for an
existing matching release before dispatch. Follow bounded progress checks and
back off on unchanged state; slow builds do not justify duplicate deployments.

Verify adoption at the actual consumer: serving version/digest or deployment ID,
readiness, health, recent restarts/errors and applicable routing/activation state.
For libraries/packages, verify publication and intended consumer adoption instead
of inventing a service rollout. Build success, publication, desired configuration
and actual serving state are distinct milestones.

## Prove the changed behavior

Choose the smallest meaningful connected scenario and affected regression tests.
Record expected versus actual behavior across the relevant UI/API/storage/worker/
consumer boundaries. Test background scheduling separately from manual execution
when autonomy matters. Reuse compatible exact-release evidence; distinguish local
fixtures, mocked results, isolated live execution and deployed end-to-end proof.
Health checks alone do not prove functionality. Correct output alone does not
prove a new path was used; inspect its trace/state. Do not claim speed, quality or
cost improvements without a suitable comparison.

Use authorized disposable synthetic data and real authorization boundaries; no
production/customer mutations just to demonstrate a feature. Reconcile outstanding
spend and reservations before paid tests, reserve a bounded increment and enforce
the user's shared ceiling across retries/workers. No implicit budget reset. If
accounting/access blocks a test, continue unaffected free checks and mark it
unproven rather than weakening verification or expanding permissions.

On a real failure, stop repetitive paid/live probes, diagnose the failing boundary
and add a minimal local fix with regression coverage. New material scope needs
authorization before release. For service regression, stop live test writes and
use only an authorized safe recovery path; do not overwrite a newer unrelated
deployment. Authentication/network inspection failures are not proof the app is
unhealthy. No deploy/rollback loop or destructive migration reversal.

## Handoff

Update the project's existing engineering/release documentation as required.
Report: absolute PR/change links, merge/source revision, actually serving artifact,
passed/failed/unproven feature checks, cleanup, cost and required next action.
Preserve evidence without secret or unrelated customer content. Do not turn a
partial feature test into a full pass. Leave no duplicate release running; create
recurring monitoring only when requested.

Example: `$ship PR_URL — merge after gates pass, deploy the API to staging
only, then prove the changed flow under the existing budget; production untouched.`
