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

# Development source, repairs and platform checks {#development-source-repairs-and-platform-checks}

This handbook mirrors software version **SPAGxE 1.2.0** from the public development
commit [`ce9c2473649e`](https://github.com/YuzhuoMa97/SPAGxECCT/commit/ce9c2473649e0be2a8b70dd2f6186a03b25d21aa).
The source text on the mirrored pages describes that published **pre-fix** snapshot.
The local repair and validation results below were completed on 31 October 2026.
The repairs have not yet been pushed to the public branch; its failed CI run is
not changed by a successful local test.

## What the downloaded source did {#what-the-downloaded-source-did}

The downloaded Linux source compiled and passed its numerical unit tests.
Its integration tests then exposed an input parsing error: a CRLF-terminated
PLINK BIM line could leave a trailing carriage return in the REF allele.
Successful compilation alone was therefore insufficient to approve that snapshot.

Two local repairs were prepared: trim line terminators correctly when reading
BIM records, and use the intended static-link policy for the Windows build.
They change input handling and build linkage, not the SPAGxE statistical formulas.
The static-link repair passed local Windows testing; the exact cause of the
earlier remote Windows failure still requires the matching remote job to be rerun.

## Local validation of the repaired source {#local-validation-of-the-repaired-source}

| Scope | Actual result |
|---|---|
| Linux environment | Ubuntu 24.04.5 under WSL2, x86-64, GCC 13.3 |
| Linux acceptance | 22 stages passed, including the 14 CI regression programs, 51 checks and 52,416 rows |
| Linux examples | Six focused tutorials and the complete 33-group walkthrough passed |
| Linux distribution/install | Built and extracted the complete bundle; all 45 comparable tutorial outputs matched; installation check passed |
| Windows repaired build | 17 regression suites and the complete-bundle 45-output comparison passed |
| Windows/Linux comparison | 43 tables and 139,709 numeric fields compared; maximum absolute difference 1.4210854715202004e-14 |
| Published GitHub CI | The inspected public commit's jobs still failed; local repairs await a new push and new matching CI run |
| macOS | Not validated by these local Windows/Linux runs |

These are measured build, input, example and regression results for the repaired
source in the stated environments. They do not prove universal tail calibration,
every-machine portability or a biobank-scale performance advantage.

## Use the corrected development revision {#use-the-corrected-development-revision}

Before starting a new analysis, obtain the development revision containing the
maintainer's BIM parsing and Windows build repairs, and check its actual CI results.
The inspected `ce9c2473649e` snapshot does not contain those unpublished repairs.
Do not treat it as an already corrected release merely because the branch is public.

```sh
git clone --branch develop --single-branch https://github.com/YuzhuoMa97/SPAGxECCT.git
cd SPAGxECCT
git rev-parse HEAD
```

Record the displayed full SHA, confirm that it includes the repairs, and then
follow [installation](/RetroSPAgwas.github.io/docs/spagxe_cpp/installation.html).
After the maintainer pushes the repaired source, rerun the matching remote
[GitHub Actions](https://github.com/YuzhuoMa97/SPAGxECCT/actions?query=branch%3Adevelop).
A queued, skipped or failed job is not platform validation. The default main
branch or a historical R tag may still lack the C++ tree.

Download the complete source, including bundled dependencies and examples.
The supplied x86-64 build policy requires Haswell/AVX2. A source archive is not
a precompiled executable. A Windows release asset, once published, must be paired
with its matching checksum and corresponding repaired source.

## Source notices {#source-notices}

The inspected public snapshot omits a consolidated `THIRD_PARTY_NOTICES.md`.
Its [bundled component sources](https://github.com/YuzhuoMa97/SPAGxECCT/tree/ce9c2473649e0be2a8b70dd2f6186a03b25d21aa/cpp/third_party)
retain individual source headers and license files. The local software repair
delivery restores the consolidated attribution record. It remains to be pushed
with the repaired source; this website does not assert that it already exists
in the inspected public commit.

The [consolidated attribution record](/RetroSPAgwas.github.io/docs/spagxe_cpp/source_notices.html)
is also supplied with this handbook. Required authorship, licenses and notices
must accompany the corresponding distributed source and executable.

See [release scope](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html) for method
boundaries and [the dated historical validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html)
for earlier acceptance. The table above is the current local development review;
the older record must not be mistaken for a test of the edited public commit.
