---
layout: default
title: Software overview
parent: WtGxE C++ manual
grand_parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 5
permalink: /docs/wtgxe_cpp/development_status.html
has_toc: true
---

# Software overview

WtGxE **0.7.4.1-dev-af-batch** provides a standalone C++ workflow for binary
GxE analysis with adjustment for genetic relatedness. Sampling-aware analysis,
optional finite external AF, and retrospective SPA are available through a
consistent command-line interface.

## Analysis workflow

1. Align study IDs, phenotype, environment, covariates, sampling information,
   and the sparse GRM.
2. For external AF, prepare a heldout background summary within the target
   group's MAF/reference-count range.
3. Run target analysis and retain interaction P values, statuses, QC, and
   input manifests.
4. Interpret the scan with its documented study design and keep the complete
   results, including unavailable-marker reasons.

The source package contains the CLI, library interface, bundled Eigen headers,
developer checks, and a complete two-step example with four target variants.
The analysis executable runs independently of R and Python. See the [installation guide](installation.html) for
build and optional test commands.

## Research use

The scientific goal is greater GxE detection power with calibrated type one
error rate. Sampling-aware analysis uses declared case-control ascertainment;
finite reference AF can add population information; and sparse-GRM analysis
keeps related participants available while accounting for their correlation.
Background-based AF discrepancy calibration supports the external-AF workflow.
Power comparisons should be read together with their matching null settings.
Use the [input guide](input_formats.html) to prepare each study consistently.

The [source repository](https://github.com/YuzhuoMa97/WtGxE)
provides the package and its documentation; repository access is required.
The public [synthetic download](../assets/wtgxe/WtGxE-example-inputs.zip)
contains artificial input data for learning the interface.

For software access, installation, or scientific enquiries, contact
[yuzhuoma@amss.ac.cn](mailto:yuzhuoma@amss.ac.cn).
