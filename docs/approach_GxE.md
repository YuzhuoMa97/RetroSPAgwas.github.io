---
layout: default
title: Genome-wide gene-environment interaction (GxE) studies
nav_order: 3
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: true
has_toc: true
---

# Genome-wide gene-environment interaction (GxE) studies

```SPAGxECCT``` package gives a generic framework to analyze a wide variaty of phenotypes. 

## Quick start-up examples

The below gives an example to use POLMM and POLMM-GENE to analyze ordinal categorical trait. 

```
library(SPAGxECCT)
PhenoFile = system.file("extdata", "simuPHENO.txt", package = "GRAB")
PhenoData = data.table::fread(PhenoFile, header = T)
PhenoData = PhenoData %>% mutate(OrdinalPheno = factor(OrdinalPheno, 
                                                       levels = c(0, 1, 2)))

# Step 1: fit a null model
SparseGRMFile =  system.file("SparseGRM", "SparseGRM.txt", package = "GRAB")
GenoFile = system.file("extdata", "simuPLINK.bed", package = "GRAB")
obj.POLMM = GRAB.NullModel(formula = OrdinalPheno ~ AGE + GENDER,
                           data = PhenoData, 
                           subjData = PhenoData$IID, 
                           method = "POLMM", 
                           traitType = "ordinal",
                           GenoFile = GenoFile,
                           SparseGRMFile =  SparseGRMFile,
                           control = list(showInfo = FALSE, 
                                          LOCO = FALSE, 
                                          tolTau = 0.2, 
                                          tolBeta = 0.1))                                                       

# Step 2(a): conduct a marker-level association study
GenoFile = system.file("extdata", "simuPLINK.bed", package = "GRAB")
OutputDir = system.file("results", package = "GRAB")
OutputFile = paste0(OutputDir, "/simuMarkerOutput.txt")
GRAB.Marker(obj.POLMM, GenoFile = GenoFile,
            OutputFile = OutputFile)

results = data.table::fread(OutputFile)
hist(results$Pvalue)

# Step 2(b): conduct a set-based association study
GenoFile = system.file("extdata", "simuPLINK_RV.bed", package = "GRAB")
OutputDir = system.file("results", package = "GRAB")
OutputFile = paste0(OutputDir, "/simuRegionOutput.txt")
GroupFile = system.file("extdata", "simuPLINK_RV.group", package = "GRAB")
SparseGRMFile = system.file("SparseGRM", "SparseGRM.txt", package = "GRAB")

GRAB.Region(objNull = obj.POLMM,
            GenoFile = GenoFile,
            GenoFileIndex = NULL,
            OutputFile = OutputFile,
            OutputFileIndex = NULL,
            GroupFile = GroupFile,
            SparseGRMFile = SparseGRMFile,
            MaxMAFVec = "0.01,0.005")

data.table::fread(OutputFile)
```

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




