# Working in sample-estate

This is one Project's repository. It holds two kinds of source and nothing else.

- `templates/` — notation blueprints, one `templates/<code>.md` per notation.
- `apps/<app>/` — React + Vite applications, each discovered from its direct `portal/package.json`.

Filename stems use the Project code (hyphens become `_`) then `__name`; `code:` matches.

Navigator imports each template and records the commit SHA as provenance.

Build each app for `/app/projects/sample-estate/<app>/`; the `apps/` source grouping is not a URL segment.

Derive every in-app path from `import.meta.env.BASE_URL` rather than writing an absolute path by hand.

A Vite base rewrites module and asset URLs and never an `href` in source.

A root `portal/` is also accepted while repositories move that workspace to `apps/portal/`.

## Project codes are client identifiers

A Project code names a matter and its repository. It identifies a client, so it is client data.

The one legitimate use here is this repository naming itself, as in `navigator.yaml`, its paths, and its portal mount.

Do not copy a Project code from another repository into this codebase.

Do not put it into a commit message, code comment, branch name, or pull-request body.

A precedent citation is still a breach; cite the governing issue by its bare identifier instead.

Read matter data through Navigator's `/api` read surfaces and write through its one REST command boundary.

Do not add a second backend.

Do not put a legal file, a client upload, an answer, a generated document, or a secret in this repository.

## Navigator CLI feedback

When Navigator's CLI is missing or wrong, open a Linear issue on the Lawyers team rather than documenting a CLI
workaround here.

The `stay-in-repo` skill under `.agents/skills/` — synced into this checkout by `navigator project repository
sync-skills` — is the scope rule to read before reaching outside this tree.

## What this is

A Navigator **project application**: the client portal for the fixture matter *Estate of Cornelius Montgomery*. Vite,
React 19, and [Navigator UX](https://github.com/neon-law-source-code/navigator-ux) for every component and every color.

**All of it is fixture data.** Nobody named in `portal/src/matter.ts` exists. Real client material must never be added
here — see `README.md`.

## Commands

```bash
pnpm --dir portal check
```

That is lint → typecheck → build → test, and it is the gate. `pnpm --dir portal test` alone reads the built output in
`portal/dist/`, and builds it first itself, so it is safe to run alone. The shared gate runs `test` before `build`,
which is why the build lives inside the test script rather than being left to the caller.

Use the Browser pane's preview tools to run the dev server, never a bare `pnpm --dir portal dev` in a shell. The portal
is served at its mount, not at the origin root: `http://localhost:5173/app/projects/sample-estate/portal/`.

## The three things that break silently

1. **The mount.** `MOUNT` in `portal/vite.config.ts` is the single most load-bearing line here. A bundle built with the
   wrong base 404s on every asset, and only once published.
2. **In-bundle links.** Every link inside this bundle goes through `portalPath()` in `portal/src/mount.ts`. A hardcoded
   path fails only when somebody clicks it. Links to Navigator's own routes (`/app/projects`) stay absolute.
3. **The ready hook.** `portal/src/ready.tsx` renders `id="sample-estate-portal-ready"`, which Navigator's walkthrough
   waits for. It must be rendered by React, never written into `portal/index.html`.

## Styling

Navigator UX ships the tokens, the typeface, and every component rule. Compose its components; do not reach for a
literal color. When something genuinely local is needed, add it to `portal/src/index.css` reading `--nav-*` tokens, and
say in a comment why the library did not cover it.

## The research folder

`portal/src/research/opinions/` holds the full text of the Washington intestacy cases the portal shows under its
*Research* tab. The `.json` files come from the Caselaw Access Project and the `.md` files are generated from them:

```bash
python3 portal/src/research/convert.py
```

Nothing in `portal/src/research/opinions/` is edited by hand. `portal/src/research.ts` is the index the portal renders;
`portal/src/research/README.md` records where the text came from and what has not been verified.

## Notation lint

`pnpm --dir portal check` covers the TypeScript. The Markdown and the YAML answer to the Neon Law Navigator rule set
instead, and the only thing that reads them is the Navigator CLI:

```bash
brew install neon-law-source-code/navigator/navigator   # macOS, and tap-qualified on purpose
pnpm validate                                          # navigator project gate, over the whole tree
```

Install it tap-qualified. An unqualified `brew install navigator` resolves to a Homebrew cask for a trackpad utility of
the same name, which installs cleanly and then has no `project` subcommand. `brew upgrade` keeps it current, and
`navigator --version` says which rule set you are holding this repository to.

CI does not use Homebrew. The `verify` job in `.github/workflows/ci.yml` runs on `ubuntu-latest` and unpacks the Linux
tarball from a pinned public Navigator release into `$HOME/.local/bin`: one static binary, no tap, no account, no sudo.
The pin is deliberate, so that a rule added upstream arrives when somebody bumps that line rather than turning a green
branch red overnight. `verify` is one of the three jobs the required `ci` check waits on, so a finding blocks the merge
— and the pinned version is worth keeping in step with the formula above, since the two together are what "it passed on
my machine" means here.

`pnpm validate` is deliberately not part of `pnpm --dir portal check`: `check` needs only what `pnpm --dir portal
install` brings, so a contributor who has not installed the CLI is not blocked by it. Run both before pushing.

`project gate` takes no file list, and there is no list to keep current. It walks the tree itself and finds every
Markdown, event, and YAML file under it, so a document is covered the moment it exists rather than the moment somebody
remembers to register it. Each Markdown file it also classifies as it reads: prose gets the structural rules (`M*`) and
the line-width rules (`S*`), and a file whose frontmatter makes it a notation — a `code:`, a `questionnaire:`, a
`workflow:` — additionally gets the notation rules (`N*`). Vendored trees such as `node_modules/` are skipped, but
`.gitignore` is not consulted, so a generated file that sits in the tree is linted like any other.

A finding prints as `path:line RULE: message`, and an error exits non-zero where a warning is only reported.

`navigator project gate` applies in place the fixes that are safe by construction — whitespace, ATX heading spacing,
blockquote spacing — and then re-checks; `--ci`, which is what CI runs, refuses to write and fails instead. The rest are
diagnostic only: the `N*` notation rules, duplicate headings (M024), trailing heading punctuation (M026). Those it names
and leaves for a human, which is the right split; a notation state machine is not something a formatter should rewrite.

Every document here is filled greedily to 120 columns, because that is what the width rules ask for: **S101** rejects a
line over 120, and **S102** rejects a line that stopped short of 120 with a word still to come. Match that when you edit
rather than rewrapping a paragraph to 80 or 100 columns.

Four things about writing prose that passes, none of them obvious from the message the rule prints:

- **Some spans cannot be broken across lines.** A link, because CommonMark forbids a line break inside a destination; an
  inline code span, because a break leaves whitespace at its edge (M038); an emphasis span, because the rules are
  line-scoped and a span crossing a line reads as unbalanced (M037). So a ~100-character link that lands at the start of
  a line reports S102 permanently — reword the sentence until the link sits inside a line, or make it the first thing in
  its paragraph.
- **Reference-style links are not the way out of that.** A definition line carrying a bare URL reports M034.
- **A literal too long to shorten belongs in a fenced block.** S101 does not reach inside a fence, so a CSP header or a
  long command goes in one — with a language tag, which is what M040 wants.
- **Italics inside a list item bulleted with an asterisk report M037.** The bullet's own asterisk is counted as an
  inline marker. A dash bullet has no such problem, and M004 holds a file to whichever character its first bullet used.

`portal/src/research/opinions/` is generated, and it stays clean by construction rather than by hand.
`portal/src/research/convert.py` fills court paragraphs to 120 columns and escapes what wrapping turns into accidental
Markdown — the `*5` of a LEXIS citation, a statute number like `11.04.015` that lands at the start of a line, a bare URL
in a footnote. `portal/src/markdown.tsx` undoes exactly those two things when it renders, and
`portal/src/test/markdown.test.tsx` pins the pair. So a finding in that folder is a bug in the converter, never a file
to edit: change `convert.py`, re-run it, and validate again.

## Merging

A green gate arms GitHub auto-merge on its own: the `enable-automerge` job in `.github/workflows/ci.yml` squash-merges
the pull request once `ci` passes and review threads are resolved. To hold a pull request that is ready, convert it to
draft rather than disabling auto-merge — a push re-arms it.

It arms as the `neon-law-staging-merge-queue` App and never as `GITHUB_TOKEN`, and that distinction is load-bearing
rather than cosmetic. GitHub creates no workflow runs for a push attributed to `GITHUB_TOKEN`, and auto-merge merges as
whoever armed it, so a merge armed with the run's own token lands on `main` and starts nothing — not a skipped run, not
a red one: none. Nothing goes red, because nothing runs. `.github/automerge-identity.py` runs inside `ci` and fails the
gate if that fallback is ever reintroduced.

If the App secrets are absent the job arms nothing and the pull request visibly waits for a human, which is the safe
direction to fail. Merge by hand in that case.

## Why `navigator.yaml` allows each off-origin string

Rule Y011 forbids comments in `navigator.yaml`, so the reason each allowlist entry is not a request is recorded here, in
the repository contract, rather than beside the entry. The wording below is carried over from the manifest as it stood
before the 26.9.15-rc.2 migration. An entry added later records its reason here and in the pull request that adds it.

### Off-origin strings the bundle may name

**`https://github.com/neon-law-staging/`** — Apache-2.0 source pointer in a comment banner

The Apache-2.0 source pointer, inside the preserved `/*!` banner on every emitted chunk and stylesheet. The licence
requires the notice be kept and the engine never evaluates a comment. Stripping it to satisfy the gate would be
removing a licence notice, which is the one edit here that would actually be wrong.

**`http://www.courts.wa.gov/`** — URL inside quoted judicial text — an autolink in a quotation

Inside the quoted text of `In re Estate of Borghi`, bundled from `portal/src/research/opinions/`. The court wrote this
footnote — "available at <http://…> (last visited Oct. 29, 2009)" — and the Markdown renderer turns the angle-bracket
form into an anchor, which is why it reaches the bundle as a link rather than as prose. Editing a URL out of a quoted
opinion would alter the quotation, and an accurate quote is not negotiable here.

This entry does not generalise: every opinion added under `portal/src/research/` may carry its own footnote URLs, and
answering each with a new allowlist line scales badly and dulls the gate. Filed separately.
