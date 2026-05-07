# builds

Auto-generated software prototypes from the **software-scout** pipeline.

## What this repo is

This repository hosts working prototypes that the `software-scout` Hermes profile generates in response to detected software needs (Reddit, HN, Indie Hackers, Product Hunt). Each prototype lives under its own directory:

```
proto-<short-hash>/
├── README.md         # what was asked for, who asked, source signal URL
├── spec.md           # generated spec
├── src/              # generated source
├── tests/            # generated tests + LLM-verified pass log
├── review.md         # LLM code-review report + bandit/eslint output
└── meta.json         # signal_id, contact_id, generation timestamps, costs
```

## Provenance

Every prototype is linked to a single source signal via `meta.json:signal_id` in the `software-scout` `contacts.db`. The companion outreach (Smartlead email or Reddit comment) cites the prototype URL.

## Status

Repo is reserved for V2.1+. V0/V1 outreach (no codegen) does not write here.

## Operational

* Generation: profile `software-scout`, scripts under `~/.hermes/profiles/software-scout/scripts/`.
* Sandbox: containerized, `--read-only`, `--cap-drop=ALL`, no socket mount, AppArmor + seccomp.
* Review gate: code review LLM pass + `bandit` + `eslint` + dependency allowlist before merge.
* Acceptance gate to V2.2: 5 prototypes passing review + manual quality approval.

License: Apache-2.0 unless overridden per-prototype.
