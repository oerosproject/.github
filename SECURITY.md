# Security Policy

Oeros is an experimental distribution and is **not intended for production or safety-critical use**. We still take security seriously and appreciate responsible disclosure.

## Supported versions

Oeros has no long-term-support releases. Security fixes land on the **current default branch** of each repository only.

| Repository | Supported branch |
| --- | --- |
| [meta-oeros](https://github.com/oerosproject/meta-oeros) | `wrynose` (default) |
| [meta-bootc](https://github.com/oerosproject/meta-bootc) | `master` (default) |
| [oeros-container-tests](https://github.com/oerosproject/oeros-container-tests) | default branch |
| Oeros container images (`ghcr.io/oerosproject`) | latest published tag |

## Reporting a vulnerability

**Please do not report security vulnerabilities in public issues, Discussions, pull requests or chat.**

Report them privately using GitHub's **private vulnerability reporting**:

1. Go to the **Security** tab of the affected repository.
2. Click **Report a vulnerability**.

If you can't use GitHub, email the maintainers at rob@robertwoolley.com.

Please include as much of the following as you can:

- The affected repository, branch or commit, and the recipe or image (with its version or tag)
- The `MACHINE`, ROS distro and Yocto release you were building
- A description of the issue and its impact
- Steps to reproduce, or a proof of concept
- Any CVE IDs already assigned, and whether you've told anyone else

## What happens next

- We aim to acknowledge your report within **5 business days**.
- We'll keep you updated as we investigate, and agree a disclosure date with you. We ask that you wait until a fix is available or **90 days** have passed, whichever comes first.
- Once a fix is available, we publish a GitHub Security Advisory and credit you, unless you'd rather stay anonymous.

## Upstream components

Most of the software in an Oeros image comes from upstream projects. If a vulnerability is in upstream code rather than in something Oeros adds or configures, please report it upstream so that every user benefits:

| Component | Where to report |
| --- | --- |
| OpenEmbedded-Core, BitBake, Poky and other Yocto Project layers | Yocto Project Security Team: `security@yoctoproject.org` ([process](https://docs.yoctoproject.org/security-reference/reporting-vulnerabilities.html)) |
| ROS 2 core packages | Open Robotics: `security@openrobotics.org` ([policy](https://github.com/ros2/ros2/security/policy)) |
| meta-ros recipes | The [ros/meta-ros](https://github.com/ros/meta-ros) maintainers, privately |
| bootc | The [bootc-dev/bootc](https://github.com/bootc-dev/bootc) project's security policy |
| Any other package | That project's own security contact |

If you're not sure whether an issue belongs to Oeros or to an upstream project, report it to us privately and we'll help route it.

## Scope

**In scope:**

- Oeros distro configuration and policy, such as default users, passwords, services, open ports and hardening flags
- Recipes, classes and scripts in Oeros repositories
- How Oeros container images are built and published, including base images, provenance and signing
- The bootc update and rollback path in meta-bootc
- Leaked credentials or secrets in Oeros repositories or CI

**Out of scope:**

- Known CVEs in upstream packages that are already tracked upstream, unless Oeros makes them worse
- Development and debug images, which are insecure by design (for example `debug-tweaks` or an empty root password)
- Issues that require physical access to an unlocked development board
