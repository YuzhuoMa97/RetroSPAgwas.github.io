---
layout: "default"
title: "SPAGxE C++ manual"
parent: "Genome-wide gene-environment interaction (GxE) studies"
nav_order: 0
permalink: "/docs/spagxe_cpp/index.html"
has_children: true
has_toc: true
---

# SPAGxE C++ manual {#spagxe-c-manual}

The native C++ program provides SPAGxE, SPAGxE+, SPAGxEmix and SPAGxEmix_local.
This is the sole official standalone C++ distribution designated and maintained by
**Yuzhuo Ma**, the method designer and author of the original SPAGxE software.
Questions, installation help and bug reports: [yuzhuoma@amss.ac.cn](mailto:yuzhuoma@amss.ac.cn).

The current documentation snapshot follows software version **1.2.0**, public development
commit [`ce9c2473649e`](https://github.com/YuzhuoMa97/SPAGxECCT/commit/ce9c2473649e0be2a8b70dd2f6186a03b25d21aa).
Local repaired builds have passed native Windows and Linux testing. The inspected public commit still needs the input/build repairs pushed and its failed CI rerun. Read [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) before choosing the revision to install.
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

SPAGxEmixPlus is planned for a future release and is not included in the current C++ distribution.
Required [incorporated-source notices](/RetroSPAgwas.github.io/docs/spagxe_cpp/source_notices.html), authorship and licenses remain in force.
