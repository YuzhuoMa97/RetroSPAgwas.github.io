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

SPAGxE 1.2.0 source is available on [main](https://github.com/YuzhuoMa97/SPAGxECCT/tree/main). [The checked main revision](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41449646442) passed Windows, Ubuntu and macOS builds, numerical checks, regressions and tutorials. C++ Release downloads are not yet published; macOS uses a source build. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [source status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for scope and installation routes. Later commits require their own checks.

# Development source, maintenance and platform checks {#development-source-repairs-and-platform-checks}

The **SPAGxE 1.2.0** C++ source is public on the
[main branch](https://github.com/YuzhuoMa97/SPAGxECCT/tree/main).
The reviewed source revision is
[a6099f305c7b5b63da5c19b6c8320aa36d06ec15](https://github.com/YuzhuoMa97/SPAGxECCT/commit/a6099f305c7b5b63da5c19b6c8320aa36d06ec15).
This manual is deployed from the separate documentation repository; updating
the software repository does not deploy these pages automatically.

## Public source and hosted checks {#what-the-downloaded-source-did}

The [hosted run for this revision](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41449646442)
passed its Windows, Ubuntu and macOS jobs on 2 November 2026. Each job completed
source compilation, numerical unit checks, reader/method regressions and
source/extracted-bundle tutorials. The workflow is green for this exact
commit. It does not publish a Release or certify later changes. A successful
documentation deployment is a separate check.

Earlier revisions failed platform-dependent numerical references on macOS.
The reference calculations were corrected without changing the analysis
formulas or relaxing their accuracy criteria; the current run exercises
the repaired suite on the actual macOS runner. Existing checks that require
wider native long double precision retain their documented platform guards.

## Local implementation validation {#local-validation-of-the-repaired-source}

The [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html)
separates the local builds, numerical units, method/reader regressions,
paired outputs and runtime tutorial checks from hosted CI. The
[maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html)
explain the numerical contracts. Finite tests do not prove universal tail
calibration, every-machine portability or a biobank-scale speed advantage.

## Select the revision to install {#use-the-corrected-development-revision}

The main branch contains the complete C++ source alongside the original R
package. Record the commit returned by Git and inspect its Actions. Once a
fixed C++ tag is published, use that tag for reproducible installation;
develop remains available for ongoing development.

```sh
git clone --branch main --single-branch https://github.com/YuzhuoMa97/SPAGxECCT.git
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
the Linux binary also requires compatible system libraries. macOS source
builds passed the hosted checks, but no macOS precompiled runtime package is
supplied. Source-build CI success does not establish compatibility with
every machine or CPU.

The historical R installation has a separate interface and dependency chain.
It remains available alongside the independent C++ edition.

SPAGxEmixPlus and SPAGxEmixLocalPlus are planned for upcoming updates.
Neither method is released or included in this C++ version.
