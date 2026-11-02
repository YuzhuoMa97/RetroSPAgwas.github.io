---
layout: "default"
title: "C++ SPAGxE example"
parent: "C++ four methods"
nav_order: 1
permalink: "/docs/spagxe_cpp/spagxe.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

SPAGxE 1.2.0 source is available on [main](https://github.com/YuzhuoMa97/SPAGxECCT/tree/main). [The checked main revision](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41449646442) passed Windows, Ubuntu and macOS builds, numerical checks, regressions and tutorials. C++ Release downloads are not yet published; macOS uses a source build. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [source status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for scope and installation routes. Later commits require their own checks.

# SPAGxE C++ example {#spagxe-c-example}

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

<!-- example: UG02_base -->
```sh
"$SPAGXE" --method SPAGxE --bfile examples/synthetic/synthetic \
  --pheno examples/synthetic/synthetic.pheno --pheno-name Quantitative \
  --covar-name X1,E,PC1,PC2 --envir-name E --regression-model linear \
  --save-resid --mac 0 --maf 0 --geno 1 --out "$OUT/base"
```

This fits a quantitative null in C++, tests GxE, and writes
`base.Quantitative.SPAGxE`, `base.analysis.settings.tsv` and
`base.null.resid`. Residual columns retain the fitted phenotype names.
The simulated permissive QC exposes edge cases; choose scientific thresholds
for real data before the scan.

## Read and retain the result {#read-and-retain-the-result}

Inspect the analysis settings receipt, sample/variant counts, branch and failure status.
The LOG10P columns report -log10(P); NA indicates a missing/failed calculation, not P=1.
The small bundled examples use permissive QC to expose edge cases. Choose and record
scientific cohort thresholds before interpreting a scan.

Continue with the [complete tutorial](/RetroSPAgwas.github.io/docs/spagxe_cpp/full_tutorial.html#run-the-four-methods) for phenotype models,
residual reuse, other genotype formats, selection/QC, local packing, CCT, AF export,
output compression and resource settings. The [CLI reference](/RetroSPAgwas.github.io/docs/spagxe_cpp/cli.html) defines each option.
