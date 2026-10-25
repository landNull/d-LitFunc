# Standards

This page is a reference. It states the contract for standards that apply to every project built with d-LitFunc. It is not project-specific and not application-specific. It does not teach and it does not explain why.

The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174) when, and only when, they appear in all capitals.

Document shape follows [Diátaxis](https://diataxis.fr). Every document is one of four kinds and nothing else.

d-LitFunc is three words joined by a hyphen: Diátaxis + Literal + Functional.

This page is the single source of truth. Add a new standard here. Do not copy a standard into another document. Link to this page.

## Documentation

- A document MUST be one of four kinds: tutorial, how-to, reference, explanation.
- A document MUST NOT mix kinds.
- A how-to MUST NOT teach. A reference MUST NOT argue. An explanation MUST NOT list flags.
- Names and documents MUST say exactly what the code does. A name MUST NOT use a metaphor.
- A reader MUST be able to read the documentation as a story. The parts MUST make sense in order.
- The four Diátaxis kinds MUST interconnect. A tutorial MAY link to a how-to. A how-to MAY link to a reference. A reference MAY link to an explanation. An explanation MAY link back to a tutorial.
- A deeper dive MUST be a link. The destination MUST contain a link that returns the reader to the place they left, so they can continue with a deeper understanding of that part.
- Comments MUST explain why or a non-obvious contract. Comments MUST NOT restate the next line.
- A code comment that addresses a function MUST include a link to this page, or to the specific section of a document that addresses that function.
- When a feature, a module, or a function is implemented, tested, and working, documentation MUST be written for it. That documentation MUST include comments in the code.
- An author SHOULD use an existing standard. An author MUST NOT invent a standard when one already exists, unless the user defines one.
- A document MUST be named for what it describes.
- The repository MUST be the source of truth for documentation.
- A repository MUST have one master document: `docs/index.md` or `docs/outline.md`.
- The master MUST link to every page with a relative path.
- A document MUST NOT be copied into another folder or repository. A link MUST be used instead.
- Links MUST be relative. `[title](path/to/page.md)` MUST resolve on any forge and in a local clone.
- Links MUST NOT use host features (wiki, Pages, Actions, or any feature that exists only on one forge).
- The forge MAY be any of GitHub, GitLab, Gitea, Forgejo, Codeberg, or a bare remote.
- Documentation that exists only on a website and not in the clone MUST NOT exist.
- A shared standard MUST live in its own repository. A project MUST point at it. A project MUST NOT copy it. Offline reading SHOULD use a git submodule.

## Build

- An application MUST be built in three stages. Do not skip one. Prototype the functionality. Adopt existing tools. Bake a helper only for a gap.
- An author MUST prototype first. An author MUST NOT design the final shape before something runs.
- A prototype MAY be rough. A prototype MUST NOT be abstract. If it does not run, it is not a prototype.
- A tool SHOULD be adopted only when it does the job better than the prototype and does not force a rewrite of the parts that already work.
- A tool SHOULD be preferred when it reduces friction, errors, or attack surface, or when it is faster.
- A tool that requires systemd MUST NOT be adopted when the host is SysVinit.
- A helper MUST be written only for a gap. A helper MUST be named for the gap it fills.
- A helper MUST be small, do one job, and be called by the application. The user MUST NOT run the helper by hand unless debugging.
- The core MUST be pure. Side effects MUST live in the shell. Functional Core, Imperative Shell.
- A function MUST take values and return values. It MUST NOT open sockets, write files, or prompt. The shell around the core does the side effects.

## Independence

- An application MUST NOT have a required dependency on a proprietary service.
- The code MUST run from a git clone. Any forge MAY host the remote.
- Optional remote services (a model API, a tunnel, a package index) MAY be used. They MUST NOT be required.
- Reduced capacity is acceptable when an optional service is absent. The application MUST say so and MUST continue with what it can do locally.
- Standalone is the requirement. The application MUST run on a machine with no network access to a specific vendor.
- The documentation MUST remain readable from the clone alone.

## Service Module

- The Service Module (SM) is the sidecar. It is present in a project's hidden folder, loaded with capabilities the host application does not carry itself.
- The application is the Command Module. The SM MUST be optional. The contract MUST NOT be optional.
- An application MUST expose a committed contract. It MUST accept an SM in a hidden folder. It MUST run alone when the SM is absent.
- The SM MUST be discovered by presence.
- The SM MUST NOT own the application's data. The SM MUST NOT rewrite the application's verbs. It MUST call them.
- The coordinator MUST NOT shell into the application. It MUST call the contract, read machine lines, and read one spoken line.
- The coordinator MUST NOT run `sudo` on the application. It MUST NOT prompt for a password.

## How to add a standard

Append one short phrase under the correct heading. Do not copy the phrase into another file. Link to this page instead.

See [standards-standalone.md](standards-standalone.md) for the page applications link to.
