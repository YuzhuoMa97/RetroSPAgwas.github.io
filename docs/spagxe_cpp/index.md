---
layout: "default"
title: "SPAGxE C++ manual"
parent: "Genome-wide gene-environment interaction (GxE) studies"
nav_order: 0
permalink: "/docs/spagxe_cpp/index.html"
has_children: true
has_toc: true
---

SPAGxE 1.2.0 source is available on [main](https://github.com/YuzhuoMa97/SPAGxECCT/tree/main). [The checked main revision](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41449646442) passed Windows, Ubuntu and macOS builds, numerical checks, regressions and tutorials. C++ Release downloads are not yet published; macOS uses a source build. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [source status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for scope and installation routes. Later commits require their own checks.

# SPAGxE C++ manual {#spagxe-c-manual}

The native C++ program provides SPAGxE, SPAGxE+, SPAGxEmix and SPAGxEmix_local.
This is the sole official standalone C++ distribution designated and maintained by
**Yuzhuo Ma**, the method designer and author of the original SPAGxE software.
Questions, installation help and bug reports: [yuzhuoma@amss.ac.cn](mailto:yuzhuoma@amss.ac.cn).

This manual documents the public C++ source of **SPAGxE 1.2.0**.
The four methods share one statistical policy and standalone executable.
Windows, Ubuntu and macOS hosted checks passed for the reviewed source
revision. A fixed C++ release tag and matching runtime downloads are still
pending. macOS users compile the source; no macOS precompiled package is supplied.
The original R package remains a separate interface for compatibility and reproducibility;
installing it does not install this independent executable.

## Follow an analysis from download to results {#follow-an-analysis-from-download-to-results}

1. [Download, compile and run the first example](/RetroSPAgwas.github.io/docs/spagxe_cpp/start.html).
2. [Choose the appropriate one of the four methods](/RetroSPAgwas.github.io/docs/spagxe_cpp/methods.html).
3. [Work through the complete tutorial](/RetroSPAgwas.github.io/docs/spagxe_cpp/full_tutorial.html), including input tables, all four methods,
   global/local formats, QC, phenotype models, CCT, AF utilities and output interpretation.
4. [Prepare and validate local G/H input](/RetroSPAgwas.github.io/docs/spagxe_cpp/inputs.html) when ancestry-specific data are available.
5. Use the [technical reference](/RetroSPAgwas.github.io/docs/spagxe_cpp/reference.html) for exact options, equations and boundaries.

## Four method examples {#four-method-examples}

| Method | Intended analysis | Tutorial |
|---|---|---|
| SPAGxE | Unrelated subjects, shared AF | [Example](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxe.html) |
| SPAGxE+ | Shared AF and sparse-GRM score correction | [Example](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxe_plus.html) |
| SPAGxEmix | Individual AF, unrelated multi-ancestry/admixed subjects | [Example](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxemix.html) |
| SPAGxEmix_local | Ancestry-specific G/H conditional on known H | [Example](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxemix_local.html) |

All four routes use one documented guarded partial-normal SPA policy. Automatic full-CGF
evaluation protects unsuitable approximations; the diagnostics do not provide a universal
P-value error bound. The native workflows cover additive counts/dosages. Read the
[feature boundaries](/RetroSPAgwas.github.io/docs/spagxe_cpp/features.html) before transferring a historical R model or formula.

SPAGxEmixPlus and SPAGxEmixLocalPlus are planned for upcoming updates.
Neither method is released or included in this C++ version.
Required [incorporated-source notices](/RetroSPAgwas.github.io/docs/spagxe_cpp/source_notices.html), authorship and licenses remain in force.

## Maintenance and validation {#maintenance-and-validation}

Read the [maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html), [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [release scope](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html) before installing or publishing this revision.
