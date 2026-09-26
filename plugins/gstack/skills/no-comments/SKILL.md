---
name: no-comments
description: "Spawn a comment-hunting subagent, fix accepted findings, and offer encodings for claimed constraints."
---

# No comments

Spawn a fresh subagent to hunt comments. Act on accepted findings.

Defer to the subagent's fresh perspective.

## Scope

Use the caller's files or diff. Otherwise use the current diff against the base branch, default `main`, including the working tree.

## Steps

1. Spawn an `Agent` with `subagent_type: "general-purpose"`. Pass the scope and this brief: delete every comment in scope that restates what the code shows, narrates a phase, or hedges; mark each deletion `MUST KILL` with a one-line reason; flag a comment as a keep only when it explains a non-obvious *why* the code cannot show or names a constraint outside our code, with proof; flag scoped lint and TypeScript suppressions the same way; touch no application code; report deletions, keeps, and flags with `file:line`.
2. Inspect its report and diff. Reject application-code edits, scope escapes, exception-protected deletions, misstated `MUST KILL` reasons, and flags that treat kept intentional code as guilty. Reshape flags on our-code surprises stay actionable. Do not restore those comments. A keep survives only with proof it is about something we cannot change. Audit missed scoped lint and TypeScript suppressions. Correctness or safety suppressions stay actionable `MUST KILL`s. Restore deletions only with exact exceptions and scoped proof. Before accepting thin `IMPORTANT` or `do not remove` kills or keeps, read the symbol's callers and its git history. If a kill is ambiguous, do not restore. If a keep is refuted or still ambiguous, delete it. Revert and rerun one rejected report with the failure named. Reject a second, report it open, and fail `/no-comments`.
3. Fix trivial accepted flags directly by deleting a dead path, dropping a parameter, or using the real API. If any fix needs a shape, sketch the types and signatures once for the accepted set and surrounding code. Stop at the sketch. Step 4 implements.
4. Implement the smallest root-cause fix in scope. Remove every named workaround. If the root cause is out of scope, land the smallest in-scope fix and report the rest open. The **principle-fix-root-causes** skill guides intent only. It does not authorize widening the fence nor fixing instances outside it. Never bolt on symptom guards.
5. Constraint comments say `do not remove`, `do not change wording`, or `talk to X before changing`. Leave keeps about things we cannot change. Offer the cheapest in-scope type, runtime, test, or CI lint. Wait for interactive approval. Unattended and eval require caller pre-approval. If approved, encode then delete. Otherwise delete, report the constraint open, and sketch out-of-scope work.
6. Report the deletion count, restored comments, reruns, the shape sketch, fixes, encoding offers, encodings, unenforced constraints, and other open work.
