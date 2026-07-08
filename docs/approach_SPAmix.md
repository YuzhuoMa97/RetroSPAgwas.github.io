---
layout: default
title: SPAmix
nav_order: 1
description: "SPAmix for scalable and accurate GWAS in admixed populations."
parent: Genome-wide association studies
has_children: false
has_toc: false
---

# SPAmix

[```SPAmix```](https://github.com/YuzhuoMa97/SPAmix) is a scalable and accurate retrospective-SPA framework for large-scale genetic association studies in admixed populations.

## Main features

- Supports multiple trait types, including quantitative, binary, time-to-event, ordinal, and longitudinal traits.
- Uses model residuals from a covariate-only model and applies retrospective saddlepoint approximation (SPA) for accurate p-values under unbalanced phenotype distributions.
- Can incorporate local ancestry information for association analyses in admixed populations.
- Designed for large biobank-scale datasets with high computational efficiency.

## Workflow of SPAmix

![plot](https://raw.githubusercontent.com/YuzhuoMa97/RetroSPAgwas.github.io/main/docs/assets/images/workflow_SPAmix_MYZ.png)

## Important notes about SPAmix in function `GRAB.NullModel`

- If the left side of argument `formula` is model residual, please specify `traitType = "Residuals"`.
- For method `SPAmix`, top SNP-derived PCs and related information are required in arguments `formula` and `control`.

## Quick start-up guide

The below gives examples to demonstrate the usage of `SPAmix`.

### Step 1. Read in data and fit a null model

```
library(GRAB)
PhenoFile = system.file("extdata", "simuPHENO.txt", package = "GRAB")
PhenoData = data.table::fread(PhenoFile, header = T)
```

`SPAmix` supports both original trait or model residuals as input. For `SPAmix`, confounding factors of SNP-derived PCs are required and should be specified in `control`.

```
library(GRAB)
PhenoFile = system.file("extdata", "simuPHENO.txt", package = "GRAB")
PhenoData = data.table::fread(PhenoFile, header = T)
N = nrow(PhenoData)
PhenoData = PhenoData %>% mutate(PC1 = rnorm(N), PC2 = rnorm(N))  # add two PCs
obj.SPAmix = GRAB.NullModel(Surv(SurvTime, SurvEvent)~AGE+GENDER+PC1+PC2, data = PhenoData, subjData = IID, method = "SPAmix", traitType = "time-to-event", control = list(PC_columns = "PC1,PC2"))
```

The same results can be obtained via using model residuals:

```
obj.coxph = coxph(Surv(SurvTime, SurvEvent)~AGE+GENDER+PC1+PC2, data = PhenoData)
obj.SPAmix = GRAB.NullModel(obj.coxph$residuals~AGE+GENDER+PC1+PC2, data = PhenoData, subjData = IID, method = "SPAmix", traitType = "Residual", control = list(PC_columns = "PC1,PC2"))
```

### Step 2. Conduct genome-wide association studies

For different trait types, step 2 is the same:

```
GenoFile = system.file("extdata", "simuPLINK.bed", package = "GRAB")
OutputDir = system.file("results", package = "GRAB")
OutputFile = paste0(OutputDir, "/Results_SPAmix.txt")
GRAB.Marker(obj.SPAmix, GenoFile = GenoFile, OutputFile = OutputFile)
```

## Citation

**Cite this article**

Ma, Y., Xu, H., Li, Y. et al. **SPAmix: a scalable, accurate, and universal analysis framework for large-scale genetic association studies in admixed populations.** *Genome Biology* **26**, 356 (2025).  
[https://doi.org/10.1186/s13059-025-03827-9](https://doi.org/10.1186/s13059-025-03827-9)

**Download citation**  
Available from the journal page.

**Received**  
17 December 2023

**Accepted**  
03 October 2025

**Published**  
16 October 2025

**Version of record**  
16 October 2025

**DOI**  
[https://doi.org/10.1186/s13059-025-03827-9](https://doi.org/10.1186/s13059-025-03827-9)

**Share this article**  
Anyone you share the article link with will be able to read this content:  
[https://doi.org/10.1186/s13059-025-03827-9](https://doi.org/10.1186/s13059-025-03827-9)
