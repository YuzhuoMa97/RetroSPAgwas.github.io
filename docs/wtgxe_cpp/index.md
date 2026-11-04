---
layout: default
title: WtGxE C++ manual
parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 8
has_children: true
permalink: /docs/wtgxe_cpp/index.html
---

# WtGxE C++ usage manual

WtGxE brings sampling-aware, retrospective-SPA binary GxE analysis to a
standalone C++ program. The same workflow accepts Unrelated samples or
Related samples represented by a sparse GRM, with optional finite reference
allele frequencies.

Current numerical version: **0.7.4.1-dev-af-batch**.

|Start here|What you will do|
|---|---|
|[Installation](installation.html)|Retrieve the source and build with C++17 and CMake or g++|
|[Worked example](quickstart.html)|Run a complete background-preparation and target-analysis example|
|[AF background preparation](background_preparation.html)|Choose heldout variants and export the calibration summary|
|[Input and output formats](input_formats.html)|Align samples and alleles, supply sampling information, interpret result fields|
|[Software overview](development_status.html)|Review the workflow and operational checks|

The [source repository](https://github.com/YuzhuoMa97/WtGxE)
contains the independent package and bundled example inputs; repository access
is required. The public [input-data download](../assets/wtgxe/WtGxE-example-inputs.zip)
provides the artificial data used in this manual.

For external AF, prepare an independent background summary first, then use it
in a separate target scan. For a study-only analysis, omit both the reference-AF
and background arguments. Keep the resulting QC files and manifests alongside
each scan.

Contact [yuzhuoma@amss.ac.cn](mailto:yuzhuoma@amss.ac.cn) for software access or assistance.
