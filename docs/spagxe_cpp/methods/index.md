---
layout: "default"
title: "C++ four methods"
parent: "SPAGxE C++ manual"
nav_order: 2
permalink: "/docs/spagxe_cpp/methods.html"
has_children: true
has_toc: true
grand_parent: "Genome-wide gene-environment interaction (GxE) studies"
---

# C++ four methods {#c-four-methods}

Choose the method from the ancestry and relatedness structure before inspecting association results.

| Method | Intended sample | Example |
|---|---|---|
| SPAGxE | Unrelated, shared allele frequency | [Run SPAGxE](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxe.html) |
| SPAGxE+ | Shared allele frequency with sparse-GRM score correction | [Run SPAGxE+](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxe_plus.html) |
| SPAGxEmix | Unrelated multi-ancestry or admixed samples, individual AF | [Run SPAGxEmix](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxemix.html) |
| SPAGxEmix_local | Unrelated samples with known ancestry copy counts H and ancestry-specific G | [Run local analysis](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxemix_local.html) |

All four routes use additive genotype counts/dosages and one guarded partial-normal SPA policy. The combined individual-AF, cross-individual-GRM interaction method is not included.

- [Equations](/RetroSPAgwas.github.io/docs/spagxe_cpp/equations.html)
- [Statistical policy](/RetroSPAgwas.github.io/docs/spagxe_cpp/policy.html)
- [Implementation choices](/RetroSPAgwas.github.io/docs/spagxe_cpp/choices.html)
- [Partial SPA acceleration](/RetroSPAgwas.github.io/docs/spagxe_cpp/partial_spa.html)
