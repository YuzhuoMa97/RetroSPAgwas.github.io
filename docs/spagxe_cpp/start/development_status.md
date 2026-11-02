---
layout: "default"
title: "C++ development status"
parent: "C++ download and first run"
nav_order: 5
permalink: "/docs/spagxe_cpp/development_status.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

**Development source.** SPAGxE 1.2.0 is published on [develop](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop). [Hosted checks for d90fb4c](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904) passed Windows and Ubuntu; macOS numerical unit checks failed and the platform remains unvalidated. The C++ release tag and runtime assets are not yet published. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the tested revision and download instructions. Later source commits require their own checks.

# Development source, maintenance and platform checks {#development-source-repairs-and-platform-checks}

The **SPAGxE 1.2.0** C++ source is public on the
[develop branch](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop).
The reviewed source revision is
[d90fb4c45849757c816c5d1ba5d191911443e83c](https://github.com/YuzhuoMa97/SPAGxECCT/commit/d90fb4c45849757c816c5d1ba5d191911443e83c).
This manual is deployed from the separate documentation repository; updating
the software repository does not deploy these pages automatically.

## Public source and hosted checks {#what-the-downloaded-source-did}

The [hosted run for this revision](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904)
passed its Windows and Ubuntu jobs. The macOS build completed, but five of its
53 numerical unit checks failed. The overall workflow is not green and
macOS remains unvalidated. Inspect the actual
commit and each job rather than treating a successful documentation deployment
as a successful software build. Later source commits require their own checks.

## Local implementation validation {#local-validation-of-the-repaired-source}

The [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html)
separates the local builds, numerical units, method/reader regressions,
paired outputs and runtime tutorial checks from hosted CI. The
[maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html)
explain the numerical contracts. Finite tests do not prove universal tail
calibration, every-machine portability or a biobank-scale speed advantage.

## Select the revision to install {#use-the-corrected-development-revision}

The commands below inspect the public development branch. Record the actual
commit returned by Git, then inspect that exact commit's Actions. Before a
fixed C++ release is published, do not assume the default main branch or its
automatic archive already contains the development C++ edition.

```sh
git clone --branch develop --single-branch https://github.com/YuzhuoMa97/SPAGxECCT.git
cd SPAGxECCT
git rev-parse HEAD
```

## Binary downloads and supported scope {#source-notices}

At the 2 November 2026 review, no C++ release tag or runtime Release assets
were public. Local archives and CI artifacts are not published Release
downloads. The planned Windows/Linux packages must be matched to their final
source, documentation and checksums before publication.

Use the [installation guide](/RetroSPAgwas.github.io/docs/spagxe_cpp/installation.html)
for source builds and the runtime package instructions that apply after
the assets are uploaded. Default prepared x86-64 binaries require Haswell/AVX2;
the Linux binary also requires compatible system libraries. macOS has no
validated runtime package.

The historical R installation has a separate interface and dependency chain.
It remains available alongside the independent C++ edition.
