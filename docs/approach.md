---
layout: default
title: Genome-wide association studies
nav_order: 2
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: true
has_toc: true
---

# Genome-wide association studies

```GRAB``` package gives a generic framework to analyze a wide variaty of phenotypes. 



## Step 1: choose ```traitType``` and ```method```

Arguments ```traitType``` and ```method``` are to specify the type of phenotype data and the analysis approach. Currently, ```GRAB``` package supports the below combinations

| phenotype                 | ```traitType``` |```method```| Related subjects |
|:-------------------------:|:---------------:|:----------:|:----------------:|
| binary trait              | "binary"        | "SAIGE"    |  YES             |
| quantitative trait        | "quantitative"  | "SAIGE"    |  YES             |
| ordinal categorical trait | "ordinal"       | "POLMM"    |  YES             |
| time-to-event trait       | "time-to-event" | "SPACox"   |  NO              |

## Step 2: choose Dense GRM or Sparse GRM

Both dense GRM and sparse GRM are supported in ```GRAB``` package to adjust for family relatedness, which can avoid inflated type I error rates.

| Which GRM   | Pros.    | Cons       | Required arguments  |
|:-----------:|:----------:|:--------:|:-------------------:|
| Dense GRM   | More powerful | Slow  | ```SparseGRMFile``` |
| Sparse GRM  | Fast  | Less powerful | ```GenoFile```      |

NOTE: Extensive simulation results suggests that, for binary and ordinal categorical data analysis, using dense and sparse GRM perform similarly in terms of both type I error rates and powers.

## Note: about argument ```control``` 

Argument ```control``` is to specify a list of parameters for controlling the fitting and association testing process. 




