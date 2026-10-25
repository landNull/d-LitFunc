# Memory master

This document is the portable record of decisions, conventions, and facts established while collaborating. It is written so any language model can read it and apply it without prior context.

Add every new durable fact here. Do not leave a fact only in a conversation. The source of truth is this file in the repository.

## How to use this document

1. Read this file at the start of work on any project that uses d-LitFunc.
2. Apply every rule below unless the user overrides it in the current conversation.
3. When a new durable fact appears, append it under the correct heading with the date.
4. Do not copy personal facts. This file holds project and standard facts only.
5. One fact per entry. Short phrases. No editorializing.

## Documentation standard

- Use d-LitFunc. Diátaxis + Literal + Functional. [2026-10-23]
- Every document is one of four kinds: tutorial, how-to, reference, explanation. Do not mix kinds. [2026-10-23]
- Names and documents say exactly what the code does. A function named `pull_code` pulls code. [2026-10-23]
- Comments explain why or a non-obvious contract. They do not restate the next line. [2026-10-23]
- Use existing standards unless the user defines one. [2026-10-23]
- The repository is the source of truth for documentation. One master document links to every page with a relative path. Do not copy the same document into another folder or repository. [2026-10-25]
- Relative links only. `[title](path/to/page.md)` resolves on any forge and in a local clone. Do not use host features (wiki, Pages, Actions). [2026-10-25]
- The forge is interchangeable. GitHub, GitLab, Gitea, Forgejo, Codeberg, or a bare remote all work. [2026-10-25]
- A shared standard lives in its own repository. Projects point at it. They do not copy it. Offline reading uses a git submodule. [2026-10-25]
- Canonical d-LitFunc document: the d-LitFunc repository, file `d-LitFunc.md`. [2026-10-25]

## Build standard

- Build in three stages. Do not skip one. Prototype the functionality. Adopt existing tools. Bake a helper only for a gap. [2026-10-25]
- A helper is small, does one job, and is called by the application. The user does not run the helper by hand unless debugging. [2026-10-25]
- Prefer a tool that reduces friction, errors, or attack surface, or that is faster. Do not adopt a tool that forces a rewrite of working parts. [2026-10-25]
- If a tool requires systemd and the host is SysVinit, do not adopt the tool. [2026-10-25]
- An application built with d-LitFunc has no required dependency on a proprietary service. It runs from a git clone. Optional remote services are optional. Reduced capacity is acceptable when they are absent. [2026-10-25]

## Service Module

- Service Module (SM) is the Apollo term for the sidecar. Captain Rocket present in a project's hidden `.captainrocket/` folder, loaded with capabilities the host application does not carry itself. Service Module and SM are interchangeable. [2026-10-25]
- The application is the Command Module. The SM is optional. The contract is not. [2026-10-25]
- The SM pattern is the standard for application development with d-LitFunc. An application exposes a committed contract. It accepts an SM in a hidden folder. It runs alone when the SM is absent. [2026-10-25]
- Capcom never shells into the application. It calls the contract, reads JSON, and reads one `SPEAK:` line. [2026-10-25]

## Captain Rocket

- Capcom is always AI-free. It never is an LM/LLM and never uses an LM/LLM as its core. It orchestrates and filters. [2026-10-20]
- Flight Director owns the human loop and emits only a validated CapcomJobEnvelope. Capcom owns decomposition, sandbox dispatch, and self-heal. Approval gate is mandatory. [2026-10-22]
- Flight Director and Capcom are built the Captain Rocket way: typed envelopes, async IPC, Landlock/Bubblewrap, Functional Core Imperative Shell. OVOS is architectural reference only. Borrow only data shapes, utterance transformers, and pure functions that already fit. Forbidden: skill loader, message-bus ownership, persona process model, audio stack. [2026-10-22]
- Contractors are any resource outside the local boardroom: remote LM/LLM or a person. Same resume shape. Role contractor, kind person or model. [2026-10-23]
- Cheaper means time, then energy, then money. A small local function wins over a long fight with an existing tool. [2026-10-23]
- n20 is a project memory, not an implementation task. [2026-10-23]
- New-idea is for humans only. It is on hold. Models stay on ContributorHarness under `contrib/`. [2026-10-23]
- Shell commands: one command per line, or a trailing backslash to continue. Do not give multi-command blocks that must be pasted together. [2026-10-24]
- After every commit, show the pull commands for the user's local repo. [2026-10-12]
- Stardust checkout is `$HOME/Apps/Stardust`. Always write `$HOME`, never `~`. [2026-10-24]

## Stardust

- Preferred command form is verb-first (`pull site`, `add platform`, `heal site`, `list sites`, `promote platform`). Object-first forms remain aliases. [2026-10-25]
- Code and versioned config move by Git. User content moves by Bee/rsync. `settings.local.php` is a single template write. [2026-10-25]
- Site pull accepts `@host:plat/site + @host:plat/site`. `->` still works. [2026-10-24]
- Slug keeps underscores. `kl_test` stays `kl_test`, not `kl-test`. [2026-10-24]
- WireGuard: reuse `wg0` if up, start it if not, only tear down a tunnel this process started. [2026-10-24]
- Installer writes `/etc/sudoers.d/stardust-wg`: `%www-admin` NOPASSWD for `wg` and `wg-quick`. [2026-10-24]
- `.zsh_stardust` noglob wrapper lives at `~/.zsh_stardust` and is sourced from `~/.zshrc`. [2026-10-24]
- Capcom contract: `contrib/captainrocket/run-tool.sh` resolves phrases to the runner or stardust. Emits JSON plus `SPEAK`. `STARDUST_SPEAK` and `STARDUST_JSON` never prompt. [2026-10-25]
- Test preflight: `stardust test <command>` runs site-debug, heals if safe, re-checks, refuses if still failing. [2026-10-25]

## How to add a memory

Append a new line under the correct heading:

```
- Fact in one short phrase. [YYYY-MM-DD]
```

If the fact changes an existing one, replace the old line. Do not leave both.
