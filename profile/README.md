# Northset OSS Run Records

If you maintain an open-source project, your review queue looks different than it did two years
ago: more pull requests, many AI-assisted, most plausible at a glance. Writing code stopped being
the bottleneck. Deciding which of these actually do what they claim is the work now — and it
lands on you.

We're a small team, and we built one narrow thing to help with that. Not another bot that opens
pull requests — a way to check the work already sitting in your queue.

**The offer.** Point us at a pull request — especially an AI-assisted one — and we run its
declared checks in a locked-down, throwaway container and send you the result: the exact commands
we ran, their results, and the (redacted, size-capped) output. It's free, it's private by
default, and it asks nothing of you in return.

**When you want proof others can check, we sign it.** If you'd like a record anyone can
independently verify — to show a downstream user the work was really run, say — we publish a
signed run record to our public ledger, with your agreement. Signing uses a public transparency
log, so a signed record is a public one: anyone can then confirm the bundle came from our
attestation workflow at a specific commit and hasn't been altered, without trusting us:

```
gh attestation verify run-record-<id>.tar.gz \
  --repo northset-oss/verification-pilot \
  --signer-workflow northset-oss/verification-pilot/.github/workflows/attest-bundle.yml
```

That proves *provenance* — where the record came from — which is the opposite of "trust us."
What the record *means* is spelled out exactly in our
[Claims Boundary](https://github.com/northset-oss/verification-pilot/blob/main/policies/claims_boundary.md),
and we hold every word we say to it.

**Two things we do, kept separate.** **Verifying work already in your queue** — running a PR's
declared checks, or publishing a record about it — is strictly consent-first: nothing happens
until you welcome it; you choose the scope and whether a record is ever published; "stop" means
stop; we never comment uninvited or post into a stranger's issues. Separately, when your project
invites contribution (a `good first issue` / `help wanted` label), we may contribute a fix
through your normal process like any contributor, and publish a record of *our own work on it*,
labeled "Contributor self-run. Not maintainer verification." — never a claim about your approval,
removable on request. Your merge or rejection is the only outcome we count. Full promise: the
[Maintainer Respect Policy](https://github.com/northset-oss/verification-pilot/blob/main/policies/maintainer_respect_policy.md).

**About the sandbox, honestly.** Checks run in a hardened, stock Docker container: non-root, all
Linux capabilities dropped, `no-new-privileges`, a read-only root filesystem, and — while your
checks run — no network. (Installing dependencies, a separate earlier step, does use the network;
every record discloses that.) It is not a kernel-grade sandbox against a determined
privilege-escalation exploit, and we won't pretend otherwise.

**Who we are.** Northset — a small team building verification tooling for AI-assisted software
work. Anything automated we do is clearly labeled as automation; anything about consent or your
relationship with us comes from a person.

**Public ledger:** <https://northset-oss.github.io/verification-pilot/> · **Start here:** [northset-oss/verification-pilot](https://github.com/northset-oss/verification-pilot)
· Opt in, opt out, or ask anything by opening an issue there or emailing oss@northset.ai.
