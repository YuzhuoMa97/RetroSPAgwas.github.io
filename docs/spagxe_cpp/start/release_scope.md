---
layout: "default"
title: "C++ release scope"
parent: "C++ download and first run"
nav_order: 6
permalink: "/docs/spagxe_cpp/release_scope.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

**Development source.** SPAGxE 1.2.0 is published on [develop](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop). [Hosted checks for d90fb4c](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904) passed Windows and Ubuntu; macOS numerical unit checks failed and the platform remains unvalidated. The C++ release tag and runtime assets are not yet published. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the tested revision and download instructions. Later source commits require their own checks.

<a id="development-verification-31-october-2026"></a>
<a id="model-and-distribution-boundaries"></a>
<a id="official-release-channel"></a>

# SPAGxE 1.2.0 release scope {#spagxe-120-release-scope}

SPAGxE is the author-designated official standalone C++ distribution of the
SPAGxE method family, maintained by Yuzhuo Ma (yuzhuoma@amss.ac.cn).
It runs without R or Python. Preserved R sources retain their historical
interface, version and dependency chain.

## Methods and inputs {#methods-and-inputs}

| Method | Scope |
|---|---|
| SPAGxE | Shared AF, unrelated subjects |
| SPAGxE+ | Shared AF, sparse-GRM score-variance correction |
| SPAGxEmix | Individual-specific AF, unrelated multi-ancestry subjects |
| SPAGxEmix_local | Ancestry-specific G/H conditional on known H |

All four methods use one paper-oriented statistical policy with guarded
partial-normal CGF acceleration. Included are additive genotype/dosage
BED/PGEN/BGEN/VCF/BCF, native linear/logistic/Breslow Cox/ordinal null models,
explicit CCT weights, AF diagnostics, local text/count/BGEN input and native
hard-count packing. See [feature coverage](/RetroSPAgwas.github.io/docs/spagxe_cpp/features.html).

SPAGxEmixPlus is planned for a future release and is not included. Current
mix/local modes reject GRM input. The homogeneous GRM workflow corrects score
variance and is not a general GLMM null fitter. Local inputs require known H;
the program does not infer ancestry or implement arbitrary uncertain-H joint
posterior tests. Arbitrary R model objects, dominant/recessive recoding and
general counting-process/stratified survival formulas are not native inputs.

## Maintenance revision {#maintenance-revision}

The current source includes maintainability changes in file resource handling,
subject mapping, null-model result assembly, outlier partitioning, numerical
helper selection and shared SIMD coefficients. Public result columns,
statistical formulas, arithmetic/reduction order and convergence rules remain
unchanged. See [maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html).

The canonical sparse-GRM table option is --grm-file. An obsolete pre-release
GRM option alias was removed; update old development commands to --grm-file.
Both sparse-triplet and PLINK GRM input layouts remain supported.

## Validation interpretation {#validation-interpretation}

Windows fresh source compilation and numerical units passed. All 17
regression suites passed, covering CLI/scope, global/local readers, AF, CCT,
independent references and stability. The six source tutorials passed.
The full 33-group walkthrough was run with the previous accepted executable
and the current executable: 85 files were byte-identical, including 145,985
numeric fields with maximum delta 0. These finite fixtures are implementation
checks, not universal population/extreme-tail calibration proofs.

Linux maintenance-source execution: passed; see the current acceptance record for exact stages and output comparisons.
macOS has not passed validation. Default x86 builds require Haswell/AVX2;
dynamic Linux binaries also require compatible glibc/libstdc++.

The public source baseline reviewed on 1 November 2026 was develop commit
c7c11590efbd10504115cd0ad8dbb9c6ca2634e1. Its hosted Windows/Ubuntu jobs passed and macOS failed.
The maintenance source was subsequently published as develop commit
d90fb4c45849757c816c5d1ba5d191911443e83c. Its 2 November 2026
[hosted workflow](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904)
passed the Windows and Ubuntu jobs, including source and extracted-runtime
tutorial checks. The macOS build/unit job failed, so the workflow as a whole
is not green. macOS support must not be inferred from the other two jobs.
This record identifies the checked commit; later changes need their own CI.
The documentation website was deployed from commit
ca8e1d39e1b01732e2c4dd8015f6dc886862725a, including the Linux installation
section and maintenance page. A source push or website deployment does not
create a C++ Release or publish its runtime attachments.

A follow-up test-only revision replaces five platform-dependent reference
calculations with exact combinatorial fixtures or multiprecision oracles.
The original accuracy criteria and all test cases remain; production
analysis code is unchanged. The revised units passed locally on Windows.
A new hosted run, especially the actual macOS job, is still required before
calling this follow-up validated on that platform.

Original R/full-CGF comparisons apply only to matched common domains.
Partial-normal SPA adds a declared approximation; a full-CGF diagnostic
threshold is not a bound on P-value error. No representative biobank-scale
speed advantage or all-platform compatibility is claimed.

## Distribution boundaries {#distribution-boundaries}

The C++ version is 1.2.0; DESCRIPTION retains the historical R version.
R installation does not install the standalone executable.
The candidate preserves applicable component copyright and license files.

At review, public Releases contained only historical R v1.1.0, with no
cpp-v1.2.0 C++ tag or runtime assets. Development sources can be downloaded
and compiled. A future tagged source archive will contain R plus cpp/.
Prepared local archives and CI artifacts are not already published Releases.
Match the final reviewed commit, tag, complete runtime archives and checksums.
An initial Windows/Linux pre-release should state its tested platform scope.
See [distribution instructions](/RetroSPAgwas.github.io/docs/spagxe_cpp/distribution.html).
