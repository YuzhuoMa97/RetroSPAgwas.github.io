---
layout: default
title: AF background preparation
parent: WtGxE C++ manual
grand_parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 3
permalink: /docs/wtgxe_cpp/background_preparation.html
has_toc: true
---

# Prepare background AF summaries

The external-AF workflow includes a dedicated background-calibration step.
WtGxE exports the study AF summary and its variance using the same study
adapter as the target analysis. The target scan then combines this summary
with the target reference file.

## Choose the background variants

Prepare an LD-pruned, independent heldout set of variants with the same study
subjects, phenotype/covariate inputs, sampling information, and sparse GRM.
Use a narrow allele-frequency and reference-allele-count group appropriate
to the targets. Keep background and target marker IDs disjoint.

Use one matched MAF/reference-count group per scan. Prepare separate
background and target PLINK subsets for different groups. `--maf` supplies
the minimum-frequency filter; define the upper-frequency bound when preparing
the subsets. The program checks target-ID overlap and allele alignment;
the study design supplies LD independence and population/technical matching.

## Export the summary

Run the background command in the [worked example](quickstart.html), using
`--af-target-bim targets.bim` and
`--af-background-out background_summary.tsv`.
This mode exports summaries without association tests and requires no existing
background-calibration file. Use `--af-background-out` in place of `--out`.

The table contains:

```text
ID AF_STUDY VAR_STUDY AF_REF AN
```

Retain the accompanying `.qc.tsv` and `.manifest.json`. Every attempted
variant appears in QC. At least 200 eligible background rows are required
for the calibration; inspect the manifest and QC reasons before target analysis.

## Use it in the target scan

Supply the target reference AF with `--ref-af` and the prepared summary with
`--af-batch-background background_summary.tsv`. The default external-AF policy
uses this background calibration to address study-reference AF discrepancies.
Use the study's actual reference allele count, allele orientation, and sampling
information consistently in both steps.

The explicit option `--af-policy matched` selects the matched-reference
workflow instead of background adjustment. A study-only scan uses neither
external-AF nor background arguments. Keep the summary and manifests so the
chosen analysis can be reproduced.
