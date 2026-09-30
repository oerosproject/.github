# Oeros

**Oeros is an experimental Linux distribution for robots, built with the [Yocto Project](https://www.yoctoproject.org/) and [OpenEmbedded](https://www.openembedded.org/) and shipping the [Robot Operating System (ROS 2)](https://www.ros.org/).**

*Oeros* is the Dutch word for the aurochs, the large wild ox that once roamed Europe, Asia and North Africa before it went extinct. We chose the name as a nod to the cloud-native idea of treating servers, and here robots and edge devices, like **cattle, not pets**: fleets of identical, reproducible, image-based systems that can be rebuilt, updated and replaced at scale, rather than hand-tended one-offs. It also happens to hint at the two projects it combines, **O**pen**E**mbedded and **ROS**.

Think of Oeros as a *concept car*. Automakers build concept cars to try out bold ideas in public, learn what works, and then carry the best of them into production models. Oeros does the same for embedded robotics: it is a place to prototype new ideas (bootable containers, container parity with the official ROS images, faster onboarding for Linux-fluent ROS developers, better CI and tooling) without putting the stability of the upstream layers at risk. Ideas that prove themselves are contributed back upstream.

> [!NOTE]
> Oeros is experimental. Expect rapid change, rough edges and the occasional breaking change. It is a proving ground, not a long-term-support product.

## How Oeros fits with ROS, the Yocto Project and meta-ros

| Project | Who | What it provides | How Oeros relates |
| --- | --- | --- | --- |
| [ROS 2](https://www.ros.org/) | [Open Robotics / OSRF](https://www.openrobotics.org/) | The robotics middleware, tools and packages, and the official Ubuntu-based binaries and container images | Oeros packages ROS 2 for Yocto-built systems and tests its images for parity with the official OSRF images |
| [Yocto Project](https://www.yoctoproject.org/) / [OpenEmbedded](https://www.openembedded.org/) | Linux Foundation | The build system (BitBake, OpenEmbedded-Core) for creating custom embedded Linux distributions | Oeros is an OpenEmbedded `DISTRO`, built with standard Yocto tooling and releases |
| [meta-ros](https://github.com/ros/meta-ros) | ROS / OpenEmbedded community | The OpenEmbedded layer that builds ROS 1 and ROS 2 from source | Oeros builds on meta-ros. Improvements to ROS recipes belong in meta-ros and are sent there first |

In short: **ROS** is the robotics software, the **Yocto Project** is how you build a tailored Linux around it, **meta-ros** is the bridge between the two, and **Oeros** is a reference distribution that puts them together and explores what comes next.

Oeros is an independent community project. It is not an official release of Open Robotics, the Yocto Project or the Linux Foundation.

## Current focus

- ROS 2 **Lyrical** and **Jazzy** (LTS) on Yocto **Wrynose** and **Scarthgap** (LTS)
- Boards such as Raspberry Pi 4 and 5, NVIDIA Jetson Orin, AMD Kria KR260, Qualcomm RB3 and Microchip PolarFire
- ROS 2 container images that behave like the official OSRF images
- Image-based, transactional OS updates with bootable containers (bootc)
- A smoother path to Yocto for Linux-fluent ROS developers

See the [roadmap](https://github.com/oerosproject/community/blob/main/ROADMAP.md) for details.

## Repositories

| Repository | What's in it |
| --- | --- |
| [community](https://github.com/oerosproject/community) | Planning hub: roadmap, backlog, governance, specs, RFCs and architecture decision records (ADRs), plus templates for proposing work |
| [meta-oeros](https://github.com/oerosproject/meta-oeros) | The Oeros `DISTRO` layer for OpenEmbedded / Yocto, used together with meta-ros |
| [meta-bootc](https://github.com/oerosproject/meta-bootc) | A Yocto layer adding [bootc](https://github.com/bootc-dev/bootc) (bootable containers) for image-based, transactional updates and rollback |
| [oeros-container-tests](https://github.com/oerosproject/oeros-container-tests) | Spec-driven tests that check Oeros ROS 2 container images against the official OSRF images and report a parity matrix |
| [.github](https://github.com/oerosproject/.github) | Organization-wide contributing guide, AI policy, commit conventions and templates |

## Where to go

| I want to... | Go to |
| --- | --- |
| Understand where the project is heading | [ROADMAP.md](https://github.com/oerosproject/community/blob/main/ROADMAP.md) and [BACKLOG.md](https://github.com/oerosproject/community/blob/main/BACKLOG.md) |
| Propose a new idea or a significant change | Open an RFC in [community/rfc](https://github.com/oerosproject/community/tree/main/rfc) |
| Read the design of a feature | [community/specs](https://github.com/oerosproject/community/tree/main/specs) and [community/adrs](https://github.com/oerosproject/community/tree/main/adrs) |
| Build an Oeros image | [meta-oeros](https://github.com/oerosproject/meta-oeros) |
| Try bootable containers on Yocto | [meta-bootc](https://github.com/oerosproject/meta-bootc) |
| Test ROS 2 container images | [oeros-container-tests](https://github.com/oerosproject/oeros-container-tests) |
| Fix or improve a ROS recipe | [ros/meta-ros](https://github.com/ros/meta-ros) upstream |
| Report a bug or request a feature | Open an issue in the repository it concerns |
| Ask about Oeros, its RFCs, specs or container images | [Oeros Discussions](https://github.com/oerosproject/community/discussions) |
| Ask about ROS on OpenEmbedded / Yocto in general | [meta-ros Discussions](https://github.com/ros/meta-ros/discussions), [ROS Discourse](https://discourse.openrobotics.org/c/community-groups/openembedded/26) or [Zulip](https://openrobotics.zulipchat.com/#narrow/channel/526059-OpenEmbedded) |

## Get involved

Oeros is built in the open and new contributors are very welcome, whether you are a Yocto veteran, a Linux-fluent ROS developer who is new to Yocto, or just curious.

- **Start small.** Look for issues labelled `good first issue` or `help wanted`, try a build on your own hardware, or improve a doc that confused you.
- **Share your hardware results.** Reports of what does and doesn't work on real boards are among the most useful contributions.
- **Bring an idea.** This is a concept car, so experiments are the point. Open an RFC or start a discussion.
- **Join a meeting.** The ROS OpenEmbedded Community Working Group meets every two weeks ([how to join](https://github.com/ros/meta-ros/discussions/1632), [minutes](https://github.com/ros/meta-ros/discussions/categories/meeting-minutes)).

Before opening a pull request, please read the [contributing guide](https://github.com/oerosproject/.github/blob/main/CONTRIBUTING.md). In short: sign off every commit under the [Developer Certificate of Origin](https://developercertificate.org/) (`git commit -s`), and if you used AI tools, disclose them as described in our [AI policy](https://github.com/oerosproject/.github/blob/main/AI_POLICY.md). Everyone is expected to follow our [Code of Conduct](https://github.com/oerosproject/.github/blob/main/CODE_OF_CONDUCT.md).
