# We run a pull request's own checks — and hand you a receipt of exactly what ran

Your queue is filling with AI-assisted pull requests that look plausible at a glance. Writing code stopped being the bottleneck; deciding which changes actually do what they claim is the work now — and it lands on you.

Point us at a pull request. We run *its own declared checks* — the tests, lint, and build your project already defines — in a locked-down, throwaway container on our machines, and send you this:

```text
run record · M-008 · RaspberryPiFoundation/blockly-samples · PR #2748

repo       RaspberryPiFoundation/blockly-samples
commit     c37ab067  (base)  →  db5ccc98  (the change under review)
image      node:22-bookworm @ sha256:a25c9934…   pinned by digest
network    dependency install: on  ·  declared checks: OFF

ran        npm run test --workspace=@blockly/plugin-workspace-search
           exit 0  ·  6.5s

bundle     sha256:58c3a6dd…   signed, in a public transparency log
label      Contributor self-run. Not maintainer verification.
```

That's a **run record**. It costs you nothing and touches nothing: no repo access, no token, no workflow file, and not one of your Actions minutes. You never have to click *"approve and run workflows"* on a stranger's code just to find out what it does.

## How to start

1. **You invite us.** Open an issue in [verification-pilot](https://github.com/northset-oss/verification-pilot/issues) or email [oss@northset.ai](mailto:oss@northset.ai) and point us at the PR. For a repo we already work with, applying the `northset-verify` label is your standing OK.
2. **We run its declared checks** — your project's own commands, in a hardened, network-isolated, throwaway container.
3. **You get the result, privately.** The exact commands, their outcomes, and the redacted output. A public, signed copy exists only if you ask for one.

> [!IMPORTANT]
> Nothing runs until you say so. A disclosure inside a pull request is never, by itself, consent. Say "stop" and we stop — we close anything open and don't come back unless you invite us.

## What a run record is — and isn't

| A run record **is** | A run record is **not** |
| :--- | :--- |
| The **declared commands** that ran | A verdict that your code is correct or well-designed |
| On the **declared code** — a pinned commit | A security review or an audit |
| In the **declared container** — pinned by digest | An approval, sign-off, or merge recommendation |
| With the **declared outputs** — redacted, size-capped | A statement that the code is ready to ship |

You stay the judge. A passing check means a command exited zero in a clean room — nothing more. The full terms we hold ourselves to: [Claims Boundary](https://github.com/northset-oss/verification-pilot/blob/main/policies/claims_boundary.md).

## Verify one yourself

Download any bundle from the [public ledger](https://northset-oss.github.io/verification-pilot/) and check it:

```sh
gh attestation verify run-record-M-008.tar.gz \
  --repo northset-oss/verification-pilot \
  --signer-workflow northset-oss/verification-pilot/.github/workflows/attest-bundle.yml
```

That proves **provenance**: this record came from our published workflow and hasn't been altered since. It does *not* prove our pipeline does what this page says it does — for that, you still take our word, so we made the word checkable: the whole thing is Apache-2.0 in [verification-pilot](https://github.com/northset-oss/verification-pilot). Go read it.

## Being straight with you

**Where we actually are.** Twelve run records so far: three rehearsals on our own repo, nine on pull requests we wrote and submitted ourselves. **No maintainer has invited a verification yet** — you would be the first. Every record is in the [ledger](https://northset-oss.github.io/verification-pilot/), labeled by type, including the ones whose PRs were rejected.

**We do sometimes open pull requests** — but only where your project already invites contribution (a `good first issue` / `help wanted` label, an assignment, an invitation), through your normal process, as a named person, with AI assistance disclosed in your format. Any record we publish about our own PR is labeled *"Contributor self-run. Not maintainer verification."* Your merge or rejection is the only outcome we count. Full promise: [Maintainer Respect Policy](https://github.com/northset-oss/verification-pilot/blob/main/policies/maintainer_respect_policy.md).

**The sandbox is good, not magic.** It is not a kernel-grade sandbox against a determined privilege-escalation exploit, and we won't pretend otherwise.

<details>
<summary>Full isolation spec</summary>

Checks run in a hardened, stock Docker container: non-root, all Linux capabilities dropped, `no-new-privileges`, a read-only root filesystem, and — while your checks run — no network.

Installing dependencies is a separate, earlier step that *does* use the network; every record discloses this as its network policy (you can see it in the receipt above: `phaseA:bridge, phaseB:none`). We treat all pull-request code as hostile and isolate it accordingly, and we review that isolation adversarially.

</details>

**It's free, and no money is moving.** During this pilot we send no payments, honoraria, or bounties. The [Payment Policy](https://github.com/northset-oss/verification-pilot/blob/main/policies/payment_policy.md) is the rule set for if that ever changes, and its first rule is the one that matters: nothing we pay is ever tied to whether you merge.

**Who we are.** Northset — a small team building verification tooling for AI-assisted software work. Anything automated is labeled as automation; anything about consent comes from a person.

---

## Start here

- **Tooling, policies, issues** — [northset-oss/verification-pilot](https://github.com/northset-oss/verification-pilot)
- **Public ledger** — [northset-oss.github.io/verification-pilot](https://northset-oss.github.io/verification-pilot/)
- **Opt in, opt out, or ask anything** — [oss@northset.ai](mailto:oss@northset.ai)
