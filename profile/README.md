# Northset OSS Run Records

**Free, private, consent-first checks for the pull requests already in your queue — plus the open-source tooling behind them.** Point us at a PR (especially an AI-assisted one) and we run *its own declared checks* — its tests, linter, build — in a locked-down, throwaway container, then send you exactly what ran.

If you maintain an open-source project, your review queue looks different than it did two years ago: more pull requests, many AI-assisted, most plausible at a glance. Deciding which actually do what they claim is the work now — and it lands on you. We built one narrow thing to help: not another bot that opens PRs, but a way to check the work already in your queue.

**How to start.** Open an issue in [northset-oss/verification-pilot](https://github.com/northset-oss/verification-pilot) or email **oss@northset.ai** and point us at the PR — we confirm before anything runs. For a repo we're already working with, applying the `northset-verify` label is your standing OK. Nothing runs until you say so; a disclosure inside a PR is never, by itself, consent.

**What you get back.** A *run record* — a receipt of exactly what ran (the declared commands, on the declared code, in the declared container), private by default. It's evidence of *what ran*, not a verdict on whether your code is good; you stay the judge. Our pipeline refuses to publish a record whose declared commands don't match what actually executed.

**When you want proof others can check, we sign it.** With your agreement we publish a signed record to our public ledger. Signing writes to a public transparency log (Sigstore/Rekor), so anyone can confirm the record came from our attestation workflow and hasn't been altered — without trusting us. That's *provenance*, the opposite of "trust us." What a record means is spelled out exactly in our [Claims Boundary](https://github.com/northset-oss/verification-pilot/blob/main/policies/claims_boundary.md).

**Why not just read your own CI?** A signed run record is portable in a way a CI dashboard isn't: a downstream user or auditor can confirm what ran without trusting you *or* us — and it lands on the PRs you're already triaging, subtracting review effort rather than adding a tool to babysit.

**Two things, kept separate.** Verifying work in your queue is strictly consent-first (above). Separately, when your project invites contribution (a `good first issue` / `help wanted` label), we may contribute a fix through your normal process like any contributor, and publish a record of *our own work on it*, labeled "Contributor self-run. Not maintainer verification." — never a claim about your approval, removable on request. Your merge or rejection is the only outcome we count. Full promise: the [Maintainer Respect Policy](https://github.com/northset-oss/verification-pilot/blob/main/policies/maintainer_respect_policy.md).

**About the sandbox, honestly.** Checks run in a hardened, stock Docker container: non-root, all Linux capabilities dropped, `no-new-privileges`, a read-only root filesystem, and — while your checks run — no network. (Installing dependencies, a separate earlier step, does use the network; every record discloses that.) It is not a kernel-grade sandbox against a determined privilege-escalation exploit, and we won't pretend otherwise.

**Who we are.** Northset — a small team building verification tooling for AI-assisted software work. Anything automated is clearly labeled as automation; anything about consent comes from a person.

**Public ledger:** <https://northset-oss.github.io/verification-pilot/> · **Start here:** [northset-oss/verification-pilot](https://github.com/northset-oss/verification-pilot) · Opt in, opt out, or ask anything by opening an issue there or emailing oss@northset.ai.
