# Contributing to Oeros

Thank you for your interest in Oeros, a reference distribution for
OpenEmbedded (OE) and the Yocto Project with the Robot Operating System (ROS).

This guide applies to every repository in the
[oerosproject](https://github.com/oerosproject) organization unless a
repository provides its own `CONTRIBUTING.md`, in which case that file takes
precedence.

## Where changes go

| Change | Where to send it |
| --- | --- |
| Oeros distro configuration, recipes and layer metadata | [oerosproject/meta-oeros](https://github.com/oerosproject/meta-oeros) |
| Container and runtime tests | [oerosproject/oeros-container-tests](https://github.com/oerosproject/oeros-container-tests) |
| Specifications, RFCs, ADRs and project planning | [oerosproject/community](https://github.com/oerosproject/community) |
| ROS recipes and the ROS layers themselves | Upstream [ros/meta-ros](https://github.com/ros/meta-ros), not here |
| OE-Core, BitBake, meta-openembedded, meta-virtualization | Upstream through the [Yocto Project contributor guide](https://docs.yoctoproject.org/dev/contributor-guide/) |

If a fix belongs upstream, send it upstream first. A temporary
`.bbappend` or backport in meta-oeros is fine while it lands, as long as the
commit message links the upstream submission.

## How to contribute

1. **Open an issue first** for anything larger than a small fix, so the
   approach can be agreed before you spend time on it.
2. **Fork the repository and create a topic branch** from the default branch.
3. **Make focused commits.** Each commit should do one thing and build on its
   own.
4. **Sign off every commit** (see [Developer Certificate of Origin](#developer-certificate-of-origin-dco)).
5. **Disclose any use of generative AI tools** (see
   [AI-assisted contributions](#ai-assisted-contributions)).
6. **Open a pull request** against the default branch and fill in the pull
   request template.
7. **Respond to review.** Push follow-up commits to the same branch. A
   maintainer may ask you to squash or reword commits before merging.

## Commit messages

Oeros follows the
[Yocto Project commit message conventions](https://docs.yoctoproject.org/dev/contributor-guide/submit-changes.html#implement-and-commit-changes)
so that changes can move between Oeros and upstream layers without being
rewritten.

```
component: Short summary in the imperative, under 72 characters

Explain what the change does and why it is needed. Wrap the body at
72 characters. Reference issues as "Fixes: #123" or link upstream
submissions and bug reports where relevant.

Signed-off-by: Your Name <your.name@example.com>
```

- The **subject** starts with the component being changed, such as a recipe
  name (`python3-foo: Upgrade to 1.2.3`), a configuration file
  (`oeros.conf: Enable systemd`) or an area (`docs: Describe the release process`).
- The **body** explains the reason for the change, not just what changed.
- **Trailers** go at the end, separated from the body by a blank line.
  `Signed-off-by:` is always the last trailer you add.

## Developer Certificate of Origin (DCO)

Oeros does not use a Contributor License Agreement. Instead, every commit must
carry a `Signed-off-by:` trailer certifying the
[Developer Certificate of Origin 1.1](https://developercertificate.org/),
the same requirement used by the Linux kernel, OpenEmbedded and the Yocto
Project.

By adding the line below you certify that you wrote the change, or otherwise
have the right to submit it under the open source license of the repository
you are contributing to:

```
Signed-off-by: Your Name <your.name@example.com>
```

Use your real name and an email address you can be reached at. `git commit -s`
adds the line for you.

**Only a human can sign off.** The `Signed-off-by:` line must be written by
you, never by an AI tool or bot on your behalf. Commits without a valid
sign-off will not be merged. To fix a missing sign-off on your branch:

```
git rebase --signoff <base-branch>
git push --force-with-lease
```

## AI-assisted contributions

Contributions made with the help of generative AI tools are welcome, provided
they are disclosed and you take full responsibility for them. Read the
[AI-Assisted Contribution Policy](https://github.com/oerosproject/.github/blob/main/AI_POLICY.md) before contributing.

In short, every commit that contains AI-generated content must carry both of
these trailers, before your `Signed-off-by:` line:

```
AI-Generated: Uses GitHub Copilot
Generated-by: GitHub Copilot v3.2

Signed-off-by: Your Name <your.name@example.com>
```

The pull request description must repeat the disclosure.

## Reviews and merging

- Every pull request needs approval from at least one maintainer of the
  repository and passing CI before it is merged.
- Maintainers may decline changes that do not fit the project's direction,
  even when they are technically correct. Opening an issue first avoids this.
- Reviewers hold AI-assisted changes to the same standard as any other
  change. "The tool wrote it" is never an answer to a review question.

## Reporting security issues

Please do not report security vulnerabilities in public issues. Use GitHub's
[private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
on the affected repository instead.

## Licensing

Contributions are accepted under the license of the repository they are made
to. Each new file should carry the copyright and license header used by the
surrounding files, or an SPDX identifier such as
`SPDX-License-Identifier: MIT`.
