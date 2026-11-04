---
layout: default
title: Two-step worked example
parent: WtGxE C++ manual
grand_parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 2
permalink: /docs/wtgxe_cpp/quickstart.html
has_toc: true
---

# Run the synthetic400 example

This complete example uses 400 artificial participants, four target variants,
and 220 regular heldout background variants. Four additional background
variants exercise QC handling. The inputs are included with the source
package and in the [example-data download](../assets/wtgxe/WtGxE-example-inputs.zip).
These small artificial inputs demonstrate the software interface.

Extract the data from the WtGxE source root so that
`examples/synthetic400/targets.bed` and
`examples/synthetic400/background.bed` exist. First
[build WtGxE](installation.html), then use the executable path from your build
in place of `./wtgxe` below.

## Step 1 Prepare background AF summaries

```sh
./wtgxe --method wtgxe --bfile examples/synthetic400/background \
  --pheno examples/synthetic400/study.pheno --pheno-name Y \
  --envir-name E --covar-name C --weight-name W \
  --sampling-design individual-case-control \
  --sp-grm-grab examples/synthetic400/study.grm \
  --ref-af examples/synthetic400/background.afreq \
  --af-target-bim examples/synthetic400/targets.bim \
  --maf .01 --mac 20 --af-background-out example_background.tsv
```

This export-only step produces:

```text
example_background.tsv
example_background.tsv.qc.tsv
example_background.tsv.manifest.json
```

The target BIM prevents overlapping marker IDs from entering the background.
The QC table retains all attempted variants and their decisions. One supplied
reference row deliberately reverses the alleles, demonstrating automatic
biallelic alignment. The manifest reports how many summary rows pass QC.

## Step 2 Analyze the target variants

```sh
./wtgxe --method wtgxe --bfile examples/synthetic400/targets \
  --pheno examples/synthetic400/study.pheno --pheno-name Y \
  --envir-name E --covar-name C --weight-name W \
  --sampling-design individual-case-control \
  --sp-grm-grab examples/synthetic400/study.grm \
  --ref-af examples/synthetic400/targets.afreq \
  --af-batch-background example_background.tsv \
  --maf .01 --mac 20 --out example_targets
```

Keep the resulting files together:

```text
example_targets.Y.WtGxE
example_targets.Y.WtGxE.summary.json
example_targets.Y.WtGxE.af_batch_background.json
```

For the environment column named `E`, **`LOG10P_GxE` is minus log10 of the GxE
P value**. Read it with `SPA_STATUS_GxE` and `REASON`. Reserved interaction
effect/SE/Wald columns can remain NA while the interaction test is available;
use the test's status and P-value fields to determine availability. Keep all
unavailable rows and their reasons in the analysis record.

The fixture's `W` column equals one and should be retained for this example.
The reference allele count is 8000, representing 4000 diploid reference
individuals. Reference individuals are not additional analyzed study samples.

## PowerShell syntax

Use the executable path produced by the build. PowerShell uses backticks for
line continuation; for example, after a direct build to `wtgxe.exe`:

```powershell
./wtgxe.exe --method wtgxe --bfile examples/synthetic400/background `
  --pheno examples/synthetic400/study.pheno --pheno-name Y `
  --envir-name E --covar-name C --weight-name W `
  --sampling-design individual-case-control `
  --sp-grm-grab examples/synthetic400/study.grm `
  --ref-af examples/synthetic400/background.afreq `
  --af-target-bim examples/synthetic400/targets.bim `
  --maf .01 --mac 20 --af-background-out example_background_ps.tsv
```

Run the target command using the same PowerShell syntax, the newly exported
background file, and a fresh target-output prefix.

## Study-only analysis

For 0k external-AF information, repeat the target command with both
`--ref-af` and `--af-batch-background` omitted and a new output prefix such as
`example_targets_0k`. The analyzed study sample stays the same.

Each run needs fresh output filenames. See the
[format guide](input_formats.html) before replacing the artificial inputs
with study data.
