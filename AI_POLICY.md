# OEROS AI-Assisted Contribution Policy

This policy covers the use of generative AI tools in contributions to any
repository in the [oerosproject](https://github.com/oerosproject)
organization. It is based on, and intended to be compatible with:

- the [OSRF Policy on the Use of Generative Tools ("Generative AI") in Contributions](https://github.com/openrobotics/osrf-policies-and-procedures),
  which governs ROS and the other projects OEROS packages; and
- the Yocto Project and OpenEmbedded
  [Acceptance of AI Generated Code](https://docs.yoctoproject.org/dev/contributor-guide/submit-changes.html#acceptance-of-ai-generated-code)
  policy, which in turn follows the
  [Linux Foundation Generative AI Policy](https://www.linuxfoundation.org/legal/generative-ai).

Because OEROS sits between those two communities, a commit that follows this
policy can be sent upstream to either one without its disclosure being
rewritten.

## What counts as a generative AI tool

A **generative AI tool** is any tool that automatically creates some or all of
a contribution using a model trained on existing human-created content. This
includes code completion (such as GitHub Copilot), chat assistants, coding
agents (such as Claude Code), and image, text or translation generators.

It does **not** include tools that generate content with well-known
deterministic methods, such as `devtool`, `recipetool`, `bitbake-layers`,
`superflore`, code formatters, linters, or templates and code generators that
rely on appropriately licensed libraries of content.

Using an AI tool only to answer questions, search, or explain existing code,
where none of its output ends up in the contribution, does not need to be
disclosed.

## Policy

1. **AI-assisted contributions are permitted.** A contribution may consist,
   in whole or in part, of the output of one or more generative AI tools.
2. **All use must be disclosed** at the time the contribution is made, in the
   formats described below.
3. **The disclosure must last as long as the contribution.** For anything
   stored in Git, that means in the commit message.
4. **You are responsible for the whole contribution**, including every part a
   tool produced, exactly as if you had written it yourself.
5. **Only a human signs off.** Every commit needs your own `Signed-off-by:`
   line under the [Developer Certificate of Origin 1.1](https://developercertificate.org/).
   It must be written by you, never added by an AI tool or agent acting on its
   own.
6. **The tool's terms must allow it.** The terms of the tool you used must not
   restrict how its output can be used in a way that conflicts with the
   repository's open source license, the project's policies, or the
   [Open Source Definition](https://opensource.org/osd).
7. **Third-party material must be licensed and attributed.** If the tool's
   output includes pre-existing copyrighted material, including existing open
   source code, you must confirm you have permission to contribute it (for
   example under a compatible open source license), and include notice,
   attribution and license information with your contribution.

## How to disclose

### Commits

Add **both** trailers below to the message of every commit where some portion
of the change was generated, **before** your `Signed-off-by:` line:

| Trailer | Required by | What it holds |
| --- | --- | --- |
| `AI-Generated:` | Yocto Project / OpenEmbedded | A short statement of the tool used, in the form `Uses <tool>` |
| `Generated-by:` | OSRF | The fully qualified name of every tool used, including provider and version or release, separated by `;` |

```
python3-foo: Fix a memory leak when deleting nodes early

The node cache kept a reference to deleted nodes until shutdown.
Release the reference in remove_node() instead.

AI-Generated: Uses GitHub Copilot
Generated-by: GitHub Copilot v3.2

Signed-off-by: Your Name <your.name@example.com>
```

With more than one tool:

```
AI-Generated: Uses GitHub Copilot and Claude Code
Generated-by: GitHub Copilot v3.2; Anthropic Claude Code <version> with <model>

Signed-off-by: Your Name <your.name@example.com>
```

Notes:

- Name the tool **and** the model where the tool lets you choose one, since
  the same tool can run different models.
- Some tools add their own trailers, such as `Co-Authored-By:`. You may keep
  them, but they do not replace the two trailers above, and they are not a
  sign-off.
- Keep one disclosure per commit. If you squash commits, keep the union of
  the tools they used.

### Pull requests

Repeat the disclosure in the pull request description so reviewers see it,
for example:

> Some portions of this pull request were generated using GitHub Copilot v3.2.

The pull request template has a section for this.

### Files (optional)

You may also mark generated content in the files themselves, using the
file's comment syntax. The Yocto Project strongly recommends this for patches
and code; it is optional here because it is easily lost when files are
edited, but it helps reviewers of large generated blocks:

```
# Generated-by: GitHub Copilot v3.2
```

For `.patch` files carried in a layer, put the trailers in the patch header
alongside `Upstream-Status:` and `Signed-off-by:`.

### Content not stored in Git

For documentation, diagrams or other content kept outside Git (for example,
wiki pages or shared documents), include the disclosure in the document's
metadata or description.

### Graphical works

Every image, logo or diagram must include a copyright statement and license
when contributed. If a generative tool created any part of it, include the
disclosure in that statement.

## Contributor responsibilities

Before submitting AI-assisted work:

- **Understand the tool and its limits.** Know what it is good at, what kind
  of data it was trained on, and what to check in its output.
- **Review and test everything it produced** with more scrutiny than you
  would your own work. Generated code can look correct and still be wrong.
  Build the affected recipes and images, run the tests, and confirm existing
  tests still pass.
- **Check security.** Look for insecure defaults, hard-coded credentials,
  unpinned sources, disabled checksums and similar problems, which are easy
  for tools to introduce into recipes and configuration.
- **Check for copied material.** Watch for large blocks that look like
  existing code, and use plagiarism or license scanning tools where you can.
- **Protect what you feed the tool.** Do not paste confidential, proprietary
  or personal data into a tool whose terms allow it to be retained or used
  for training.
- **Be able to explain it.** You must be able to answer review questions
  about any part of your contribution. "The tool wrote it" is not an answer.
- **Keep the contribution proportionate.** Do not submit large volumes of
  generated changes that you have not reviewed yourself, and do not use AI
  tools to generate issues, review comments or pull request descriptions
  that you have not read and checked.

Copyright generally cannot be held on the raw output of a generative tool,
but you still hold copyright on the parts of a contribution you created
yourself. Disclosure exists so that, if a tool's output is later found to be
legally problematic, the affected contributions can be found and reviewed
instead of placing the whole code base under suspicion.

## Maintainers

- Review AI-assisted contributions to the same standard as any other.
- Maintainers may ask for more context about how a change was produced, or
  decline a change they cannot reasonably review.
- A missing or incomplete disclosure blocks merging until it is fixed, in the
  same way as a missing `Signed-off-by:`.
- If a merged contribution is later found to contain problematic generated
  content, handle it as you would any other suspected copyright problem.

## Changes to this policy

The law and community practice around generative AI are changing quickly.
OEROS will update this policy as the OSRF, Yocto Project and Linux Foundation
policies change, and will announce changes publicly. Contributors should
follow the version in effect when they make their contribution.
