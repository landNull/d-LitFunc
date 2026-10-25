# Documentation source of truth

This page is the rule for where documentation lives and how it is linked.

## The rule

The git repository is the source of truth. Documentation is Markdown files in the repository. A master document links to every page with a relative path.

A click on a link opens the page in the same repository. The link is `[title](path/to/page.md)`. It resolves on any forge that renders Markdown and in a local clone. It does not name a host.

## What is forbidden

- A second copy of the same document in another folder or another repository.
- A link that depends on a forge feature (wiki, Pages, Actions, a host-specific renderer).
- A required dependency on a proprietary service.
- Documentation that exists only on a website and not in the clone.

## What is required

- One master document per repository (`docs/index.md` or `docs/outline.md`).
- Relative links from the master to every page.
- The application runs from the clone with no network access to a specific vendor. Reduced capacity is acceptable when an optional service is absent.

## Shared standards

A shared standard lives in its own repository. A project links to that repository. It does not copy the files.

If the project needs the standard offline, add the standard repository as a git submodule and link relatively into the submodule. A submodule is plain git. It works on any forge.

## What this page is

This page is a reference. It states the contract for documentation storage and linking. It does not teach and it does not explain why.
