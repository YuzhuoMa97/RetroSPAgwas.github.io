---
layout: default
title: Input and output formats
parent: WtGxE C++ manual
grand_parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 4
permalink: /docs/wtgxe_cpp/input_formats.html
has_toc: true
---

# Input and output formats

## Study inputs

|Input|Required content|
|---|---|
|Genotypes|SNP-major PLINK BED/BIM/FAM with complete biallelic hardcalls|
|Subject table|Whitespace-delimited header with IID, binary Y, numeric E, and selected covariates|
|Sampling information|Population prevalence using `--prevalence K`, or a positive supplied weight column using `--weight-name W`|
|Relatedness|Optional sparse GRM with sample identifiers and explicit diagonal entries|
|Reference AF|Optional PLINK2 `.afreq` with variant and allele identifiers, `ALT_FREQS`, and `OBS_CT`|
|AF background|Heldout summary prepared by the background-export command for the default external-AF workflow|

The adapter aligns IIDs to FAM order. Provide unique IDs and valid numeric
inputs; incomplete subject rows are reported. The covariate model includes
an intercept and the E main effect. Additional columns are selected with
`--covar-name C1,C2`. A separate `--covar FILE` can supply a named covariate table.

## Sampling information

`--prevalence K` is population prevalence, not the selected-sample case
fraction. Alternatively, supply weights and declare
`--sampling-design individual-case-control`. Use weights that are constant
within cases and constant within controls, reflecting the study's own-Y
case-control sampling. Choose prevalence or a weight column, rather than both.
Case oversampling means that cases are enriched relative to population
prevalence; it also occurs in balanced or control-rich case-control studies.

## Sparse GRM

Use `--sp-grm-grab FILE` for ID1/ID2/value text with explicit diagonal entries,
or `--sp-grm-plink2 PREFIX` for `.grm.sp` and `.grm.id`. Choose one GRM option.
Omitting a GRM uses identity covariance for Unrelated samples. Pedigree-role
labels are unnecessary.

For the current weighted workflow, prepare at least 50 approximately
independent GRM components and keep the largest component smaller than N/10.
Check sample alignment before analysis.

## Reference AF and background

The reference header is:

```text
#CHROM ID REF ALT ALT_FREQS OBS_CT
```

`OBS_CT` is the positive integer allele count: 4000 diploid reference
individuals contribute 8000 observed alleles. The importer counts BIM column 5
(A1) as ALT and aligns reversed biallelic reference rows. Match study and
reference population, technical properties, variant IDs, and alleles.

Create the `ID AF_STUDY VAR_STUDY AF_REF AN` background table using the
[export workflow](background_preparation.html). Use independent, heldout
variants within the target's narrow MAF/reference-count group. Prepare and
analyze separate groups when needed.

## Result files

For phenotype `Y`, the main scan writes:

```text
PREFIX.Y.WtGxE
PREFIX.Y.WtGxE.summary.json
PREFIX.Y.WtGxE.af_batch_background.json
```

The last file records the active AF-background configuration. The main table
retains marker metadata, analyzed counts, main and interaction P-value fields,
test statuses, and `REASON`. All `LOG10P` fields mean **minus log10 of P**.
For an environment named `E`, read `LOG10P_GxE` and `SPA_STATUS_GxE` for the
interaction test. The field suffix is Gx followed by the selected environment name.

`BETA_GxE`, `SE_GxE`, and `LOG10P_Wald_GxE` are reserved output columns and can be
NA even when the interaction test is available. In the fast branch, `BETA_G`
and `SE_G` can also remain NA while the main-effect P value is available.
Use the P-value/status fields, not reserved coefficient columns, to establish
test availability. Retain unavailable rows and reasons; a missing result is
not a P value of one.

Background export writes a summary, all-marker QC table, and manifest. Use a
fresh prefix for every scan. This adapter analyzes one binary phenotype and
one numeric environment per command using PLINK hardcalls.
