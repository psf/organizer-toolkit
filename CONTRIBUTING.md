# PSF Organizers Kit Contributing Guide

Thank you for considering a contribution. This toolkit exists to help volunteers
run Python communities and events anywhere in the world, and it is at its best
when the people who have actually done that work write it.

You do not need to be an experienced open source contributor to help. If you
have organized a meetup, run a conference, revived a community that went quiet,
or simply tried to do one of those things and hit a wall, you know something
worth writing down.

## Code of Conduct

Everyone participating in this project is expected to follow the
[PSF Code of Conduct](https://policies.python.org/python.org/code-of-conduct/).
That applies to issues, pull requests, reviews, and every other space connected
to this repository.

If you need to report a concern, contact the PSF Code of Conduct Working Group at
conduct-wg@python.org.

## Ways to Contribute

Writing new pages is only one option, and often not the most useful one.

- **Share what actually worked.** Concrete experience from a real community is
  the most valuable thing you can add. Numbers, timings, and specifics beat
  general advice.
- **Correct something wrong or out of date.** Programmes change, links rot, and
  contact addresses move. Fixing these is a genuine contribution.
- **Fill a gap.** If you looked for guidance here and it was not there, that
  absence is worth an issue even if you cannot write the section yourself.
- **Improve clarity.** Shortening a rambling paragraph or replacing jargon helps
  every reader who comes after you.
- **Report a problem.** Open an issue. You do not have to supply the fix.
- **Review a pull request.** Reading someone else's draft as an organizer and
  saying whether it would have helped you is real work and genuinely appreciated.

## Before You Start

- **For small fixes**, such as typos, broken links, or clarifications, just open
  a pull request. No discussion needed.
- **For anything substantial**, such as a new page, a restructure, or a change to
  guidance, open an issue first. This saves you from writing something the
  maintainers were planning differently, and it gives other organizers a chance
  to add their experience before you invest the effort.
- **Check existing issues and pull requests** so you are not duplicating work
  already underway.

## Setting Up Locally

Setup, prerequisites, and the full command reference live in the
[README](README.md). The short version:

```bash
uv sync                  # install dependencies
uv run mkdocs serve      # preview at http://127.0.0.1:8000
```

If you have [just](https://github.com/casey/just) installed, `just install` and
`just serve` do the same thing.

## Repository Layout

| Path | Purpose |
|------|---------|
| `docs/` | All site content. One directory per page, each containing `index.md`. |
| `mkdocs.yml` | Site configuration and the `nav` section that controls the sidebar. |
| `justfile` | Task shortcuts for building, serving, validating, and link checking. |
| `AUTHORS.md` | Contributor credits. |
| `README.md` | Setup and local development instructions. |

**If you add a new page, you must add it to the `nav` list in `mkdocs.yml`.** A
page that is not in `nav` will not appear in the sidebar, and a strict build will
warn about it.

## Writing Guidelines

### Know who you are writing for

Assume your reader is a volunteer with limited time, possibly organizing their
first event, possibly reading English as a second or third language, and almost
certainly looking for a specific answer rather than reading the whole site.

### Be global by default

This is the guideline contributors most often miss. The toolkit serves organizers
on every continent, and what is obvious in one country is wrong in another.

- Do not assume US law, tax rules, currency, or nonprofit structures.
- Do not assume a platform is available or popular everywhere. Meetup, Discord,
  WhatsApp, and Telegram all dominate in different regions.
- Do not assume budget. Many communities run on nothing at all, so prefer advice
  that works with zero money and note when something costs.
- Do not assume reliable venues, electricity, or internet.
- When something genuinely is region-specific, say so plainly rather than
  presenting it as universal.

### Be practical and specific

- Prefer "start publicizing at least three weeks ahead" over "publicize early".
- Include the checklist, the template, or the sample email. Readers copy these.
- Explain the reason behind advice, because a reader who understands why can
  adapt it to their own situation.
- Name the failure mode. Knowing what goes wrong is often more useful than
  knowing the ideal path.

### Do not give legal, tax, or financial advice

Point readers toward local professional advice and official sources instead.
Where the toolkit discusses registration, money, or liability, it should help a
reader ask the right questions, not answer them definitively.

### Write plainly

- Second person and active voice. "You can request a subdomain", not "a subdomain
  may be requested".
- Expand an acronym the first time it appears on a page.
- Short paragraphs and lists over dense blocks of text.
- Use standard punctuation. Prefer commas, colons, semicolons, and parentheses,
  and avoid dashes as sentence separators.
- Inclusive, welcoming language. Avoid "simply", "just", and "obviously", which
  quietly tell a struggling reader that they should have found it easy.

### Markdown conventions

- One `#` heading per page, matching its `nav` title.
- Use `##` and `###` for structure. The table of contents is configured to a
  depth of three, so avoid going deeper.
- Match the heading capitalization used elsewhere in the file you are editing.
- Give list items a bold lead-in when they cover distinct topics.
- Use descriptive link text, not "click here" or a bare URL.
- Link between pages with relative Markdown paths, for example
  `../resources/index.md`, so the build can validate them.

## Accuracy and Sources

The toolkit makes claims about PSF programmes, trademarks, and third party
organizations. Getting these wrong actively harms organizers who rely on them.

- **Verify against the official page** and link to it, rather than restating
  policy that may change.
- **Do not invent contact addresses, fees, deadlines, or eligibility rules.** If
  you cannot confirm a detail, leave it out and link to the source instead.
- **Distinguish policy from practice.** If something is how a programme has
  worked in practice rather than a published rule, say so.
- **Flag things that change.** Programme availability and fees date quickly, so
  prefer wording that encourages readers to check the current status.
- **Credit adapted material.** If you draw on another community's documentation,
  link it and note the adaptation, and confirm its license permits reuse.

## Submission Guide

### 1. Fork and branch

Work on a branch, never directly on `main`.

```bash
git switch -c docs/short-description
```

Descriptive branch names help reviewers. `docs/venue-guidance` is better than
`patch-1`.

### 2. Keep pull requests small and focused

One topic per pull request. A change touching two related pages is fine; one
rewriting six unrelated pages is very hard to review and will sit unmerged for
much longer.

If you have written a lot, consider splitting it into several pull requests that
touch separate files. They can then be reviewed and merged independently.

### 3. Write a clear commit message

Use a short prefixed summary, then explain the reasoning if it is not obvious.

```
docs: add guidance on choosing an event format

Explains the trade-offs between talks, workshops, and study groups,
and what to do when no expert speaker is available.
```

### 4. Validate before you push

```bash
just validate      # or: uv run mkdocs build --strict
just link-check    # or: lychee --cache --verbose .
```

A strict build must pass. The link checker reports some pre-existing failures and
false positives from sites that block automated requests, so check that you have
not introduced anything new rather than expecting a clean run.

### 5. Open the pull request

Describe what changed and why. If it relates to an issue, reference it. Mention
anything you were unsure about, since that is exactly where a reviewer's
attention is most useful.

A short checklist worth running through:

- [ ] The strict build passes.
- [ ] Any new page is added to `nav` in `mkdocs.yml`.
- [ ] New internal links use relative paths and resolve.
- [ ] Factual claims link to an authoritative source.
- [ ] The writing works for organizers outside your own country.
- [ ] Adapted material is credited and its license permits reuse.

### 6. Review

This project is maintained by volunteers, so review may take time. That is not
disinterest. Expect questions and suggested changes, especially on guidance that
touches PSF programmes or policy, where maintainers may want to word things
themselves. Push follow-up commits to the same branch and the pull request will
update automatically.

## Adding Yourself to AUTHORS

Contributors are credited in [AUTHORS.md](AUTHORS.md). Add yourself in the same
pull request as your contribution, in alphabetical order by first name, linking
to your GitHub profile or personal site.

```markdown
- [Your Name](https://github.com/yourusername)
```

## Licensing

By contributing, you agree that your work is published under this project's
licenses:

- **Documentation**, meaning Markdown, images, and related content, is licensed
  under a
  [Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).
- **Code** is licensed under the [MIT License](http://choosealicense.com/licenses/mit/).

Only contribute text you wrote or that is compatibly licensed. Do not paste
content from sites, books, or documentation without confirming you have the right
to do so, and always attribute adapted material.

The PSF wordmark and logo are trademarked. See the
[PSF Trademark Usage Policy](https://www.python.org/psf/trademarks/).

## Getting Help

- Open an issue if you are unsure whether an idea fits, or if you are stuck part
  way through a change.
- The [Python conferences mailing list](https://mail.python.org/mailman/listinfo/conferences)
  is where organizers help each other, and a good place to sanity check event
  guidance with people who run events.

An imperfect contribution that gets discussed is far more useful than a perfect
one that never gets written. Please open the pull request.
