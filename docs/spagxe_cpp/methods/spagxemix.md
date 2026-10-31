---
layout: "default"
title: "C++ SPAGxEmix example"
parent: "C++ four methods"
nav_order: 3
permalink: "/docs/spagxe_cpp/spagxemix.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

# SPAGxEmix C++ example {#spagxemix-c-example}

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

<!-- example: UG04_mix -->
```sh
"$SPAGXE" --method SPAGxEmix \
  --bgen examples/synthetic/synthetic.bgen ref-first \
  --pheno examples/synthetic/synthetic.pheno --pheno-name Quantitative \
  --covar-name X1,E,PC1,PC2 --envir-name E --pc-cols PC1,PC2 \
  --mac 0 --maf 0 --geno 1 --out "$OUT/mix"
```

PC1/PC2 enter both individual-AF fitting and the phenotype null. Their order
and units matter. The minor-oriented pooled/OLS/carrier-logistic cascade is
estimated online. Invalid or nonconverged selected AF fits produce explicit
NA/status 9, rather than a pooled replacement P. An `.afc` export is not an
association-cache argument.

## Read and retain the result {#read-and-retain-the-result}

Inspect the analysis settings receipt, sample/variant counts, branch and failure status.
The LOG10P columns report -log10(P); NA indicates a missing/failed calculation, not P=1.
The small bundled examples use permissive QC to expose edge cases. Choose and record
scientific cohort thresholds before interpreting a scan.

Continue with the [complete tutorial](/RetroSPAgwas.github.io/docs/spagxe_cpp/full_tutorial.html#run-the-four-methods) for phenotype models,
residual reuse, other genotype formats, selection/QC, local packing, CCT, AF export,
output compression and resource settings. The [CLI reference](/RetroSPAgwas.github.io/docs/spagxe_cpp/cli.html) defines each option.
