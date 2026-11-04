---
layout: default
title: Two-step worked example
parent: WtGxE C++ manual
grand_parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 2
permalink: /docs/wtgxe_cpp/quickstart.html
has_toc: true
---

# Run a complete worked example

This complete example uses 400 artificial participants, four target variants,
and 220 regular heldout background variants. Four additional background
variants exercise QC handling. The inputs are included with the source
package and in the [example-data download](../assets/wtgxe/WtGxE-example-inputs.zip).
These small artificial inputs demonstrate the software interface.

First [build and install WtGxE](installation.html). Keep the working directory
at the source root, where `examples/synthetic400/targets.bed` and
`examples/synthetic400/background.bed` should exist. The source package already
contains these inputs; when using the separate data download, extract it from
the source root while preserving its `examples/synthetic400/` directory.

The commands below use the default CMake installation:
`./install/bin/wtgxe` for a Unix-like shell and
`./install/bin/wtgxe.exe` for Windows PowerShell. For a direct compiler build,
replace that executable path with `./wtgxe` or `./wtgxe.exe`, respectively.

## Step 1 Prepare background AF summaries

```sh
./install/bin/wtgxe --method wtgxe --bfile examples/synthetic400/background \
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
./install/bin/wtgxe --method wtgxe --bfile examples/synthetic400/targets \
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
P value**. For example, a value of 3 corresponds to P=0.001. Read it with
`SPA_STATUS_GxE` and `REASON`. Reserved interaction
effect/SE/Wald columns can remain NA while the interaction test is available;
use the test's status and P-value fields to determine availability. Keep all
unavailable rows and their reasons in the analysis record.

The fixture's `W` column equals one and should be retained for this example.
The reference allele count is 8000, representing 4000 diploid reference
individuals. Reference individuals are not additional analyzed study samples.

## Complete Windows PowerShell commands

Run these commands from the source root after the CMake install step.
PowerShell uses a backtick for line continuation; keep it as the last
character on each continued line.

### Step 1 Export the background

```powershell
./install/bin/wtgxe.exe --method wtgxe --bfile examples/synthetic400/background `
  --pheno examples/synthetic400/study.pheno --pheno-name Y `
  --envir-name E --covar-name C --weight-name W `
  --sampling-design individual-case-control `
  --sp-grm-grab examples/synthetic400/study.grm `
  --ref-af examples/synthetic400/background.afreq `
  --af-target-bim examples/synthetic400/targets.bim `
  --maf .01 --mac 20 --af-background-out example_background_ps.tsv
```

### Step 2 Analyze the targets

```powershell
./install/bin/wtgxe.exe --method wtgxe --bfile examples/synthetic400/targets `
  --pheno examples/synthetic400/study.pheno --pheno-name Y `
  --envir-name E --covar-name C --weight-name W `
  --sampling-design individual-case-control `
  --sp-grm-grab examples/synthetic400/study.grm `
  --ref-af examples/synthetic400/targets.afreq `
  --af-batch-background example_background_ps.tsv `
  --maf .01 --mac 20 --out example_targets_ps
```

The main result is `example_targets_ps.Y.WtGxE`, accompanied by its summary
and AF-background JSON files. The bundled target BIM contains four variants;
inspect the result rows and their statuses rather than treating the example
as a power experiment.

## Study-only analysis

A study-only scan uses the same study participants and sparse GRM, without
reference-AF or AF-background arguments. From a Unix-like shell:

```sh
./install/bin/wtgxe --method wtgxe --bfile examples/synthetic400/targets \
  --pheno examples/synthetic400/study.pheno --pheno-name Y \
  --envir-name E --covar-name C --weight-name W \
  --sampling-design individual-case-control \
  --sp-grm-grab examples/synthetic400/study.grm \
  --maf .01 --mac 20 --out example_targets_0k
```

For Windows PowerShell:

```powershell
./install/bin/wtgxe.exe --method wtgxe --bfile examples/synthetic400/targets `
  --pheno examples/synthetic400/study.pheno --pheno-name Y `
  --envir-name E --covar-name C --weight-name W `
  --sampling-design individual-case-control `
  --sp-grm-grab examples/synthetic400/study.grm `
  --maf .01 --mac 20 --out example_targets_0k_ps
```

These scans write the main result table and summary JSON; they do not write
an AF-background JSON file. To supply population prevalence instead of the
fixture weights in an appropriately designed study, replace `--weight-name W`
with `--prevalence K`, using the study's actual population prevalence. See
the [sampling-information requirements](input_formats.html#sampling-information).

Each run needs fresh output filenames. See the
[format guide](input_formats.html) before replacing the artificial inputs
with study data.
