---
layout: "default"
title: "C++ SPAGxEmix_local example"
parent: "C++ four methods"
nav_order: 4
permalink: "/docs/spagxe_cpp/spagxemix_local.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

**Development source.** SPAGxE 1.2.0 is published on [develop](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop). [Hosted checks for d90fb4c](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904) passed Windows and Ubuntu; macOS numerical unit checks failed and the platform remains unvalidated. The C++ release tag and runtime assets are not yet published. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the tested revision and download instructions. Later source commits require their own checks.

# SPAGxEmix_local C++ example {#spagxemix_local-c-example}

Use the complete source checkout or binary bundle with its example files. First follow
[installation](/RetroSPAgwas.github.io/docs/spagxe_cpp/installation.html) and read [the development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html).
The Bash commands below run inside `cpp/`, after a successful source build:

```sh
SPAGXE=./build/bin/SPAGxE
OUT=results/website_four_methods
mkdir -p "$OUT"
```

For an extracted Windows binary bundle, the executable inside `cpp/` is `./SPAGxE.exe`.
Use the supplied CMD/PowerShell examples from the [tutorial scripts](/RetroSPAgwas.github.io/docs/spagxe_cpp/tutorial_scripts.html)
when running in Windows; Bash backslash continuations are not PowerShell syntax.

## Analysis command {#analysis-command}

<!-- example: UG05_local_text -->
```sh
"$SPAGXE" --method SPAGxEmix_local \
  --local-manifest examples/local/cohort.local.tsv \
  --pheno examples/local/samples.pheno \
  --pheno-name Quantitative,Binary,Time:Event,Ordinal \
  --covar-name X,E --envir-name E --mac 0 --maf 0 --geno 1 \
  --out "$OUT/local_text"
```

This writes each trait's `.SPAGxE_local` ancestry-specific table,
`.SPAGxE_local_CCT` across-ancestry table and a `.local.settings.tsv` receipt.
H must be known ancestry chromosome copies 0/1/2. Supply the complete ancestry
collection, with sum(H)=2 per complete person/variant. The program does not
infer ancestry. See [input preparation](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_preparation.html).

## Read and retain the result {#read-and-retain-the-result}

Inspect the analysis settings receipt, sample/variant counts, branch and failure status.
The LOG10P columns report -log10(P); NA indicates a missing/failed calculation, not P=1.
The small bundled examples use permissive QC to expose edge cases. Choose and record
scientific cohort thresholds before interpreting a scan.

Continue with the [complete tutorial](/RetroSPAgwas.github.io/docs/spagxe_cpp/full_tutorial.html#run-the-four-methods) for phenotype models,
residual reuse, other genotype formats, selection/QC, local packing, CCT, AF export,
output compression and resource settings. The [CLI reference](/RetroSPAgwas.github.io/docs/spagxe_cpp/cli.html) defines each option.

Read [local input preparation](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_preparation.html), [count packing](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_packing.html) and [known-H BGEN](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_bgen.html) before converting real ancestry-specific data.
