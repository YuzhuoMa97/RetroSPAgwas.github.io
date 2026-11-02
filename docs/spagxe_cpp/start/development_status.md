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

**Maintenance candidate.** This page accompanies local SPAGxE 1.2.0 maintenance source that has not yet been pushed or tagged. The [public baseline](https://github.com/YuzhuoMa97/SPAGxECCT/commit/c7c11590efbd10504115cd0ad8dbb9c6ca2634e1) passed hosted Windows and Ubuntu checks; its macOS build failed. Those hosted results do not validate this new candidate. Read the [candidate validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the current evidence and download boundaries.

# Development source, maintenance and platform checks {#development-source-repairs-and-platform-checks}

This manual documents a local maintenance candidate of **SPAGxE 1.2.0**.
The candidate is not yet a public development commit or a tagged Release.
Its own build, numerical, format and tutorial acceptance must be read from the
[candidate validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html).

## Public source baseline {#what-the-downloaded-source-did}

The public source baseline is the revision inspected at the start of this work.
It already contains the CRLF-aware BIM reader and Windows static-link repairs.
Its hosted Windows and Ubuntu jobs passed; its macOS build/unit step failed.
These dated baseline results do not establish that the new maintenance source
has passed hosted CI.

## Local candidate validation {#local-validation-of-the-repaired-source}

Implementation changes keep the published-method numerical policy and require
fresh builds, numerical units, reader/method regressions and paired outputs
against the accepted executable. The [maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html)
explain the contracts; the [validation page](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html)
records measured results and unfinished checks. Finite tests do not prove
universal tail calibration, every-machine portability or a biobank-scale speed advantage.

## Select the revision to install {#use-the-corrected-development-revision}

The commands below inspect the public development branch. This new candidate
will appear there only after its maintainer reviews and pushes it. Record the
actual commit returned by Git, then inspect that exact commit's Actions.

```sh
git clone --branch develop --single-branch https://github.com/YuzhuoMa97/SPAGxECCT.git
cd SPAGxECCT
git rev-parse HEAD
```

## Binary downloads and supported scope {#source-notices}

No C++ release tag or binary Release assets were public at the baseline review.
A local archive or CI artifact is not a maintainer-published Release. Use
the [installation guide](/RetroSPAgwas.github.io/docs/spagxe_cpp/installation.html)
and [release scope](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html);
only advertise platform binaries after matching their source, docs and checksums.
The historical R installation has a separate interface and dependency chain.
