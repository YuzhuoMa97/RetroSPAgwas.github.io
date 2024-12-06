---
layout: default
title: POLMM / POLMM-GENE
nav_order: 2
description: "POLMM approaches: ordinal categorical trait analysis."
parent: Genome-wide association studies
has_children: false
has_toc: false
---

# POLMM approaches 

```POLMM``` and ```POLMM-GENE``` are accurate and efficient approaches to associate an ordinal categorical trait to single-variant and variant-set (e.g. gene), respectively.

## Main features

```POLMM``` and ```POLMM-GENE``` are

- designed for ordinal categorical trait analysis,
- accurate for unbalanced phenotypic distribution (e.g. sample size proportion in three levels is 30:1:1 ),
- scalable for a large-scale biobank data analysis (e.g. UK Biobank),
- support both dense GRM and sparse GRM (recommanded) to adjust for family relatedness,
- support both single-variant analysis and set-based analysis (Burden tests, SKAT, and SKAT-O).

## Important notes prior to analysis

- For function ```GRAB.NullModel```, the left side of argument ```formula``` should be a factor when fitting a null model in step 1. If function ```factor``` is used to convert phenotype to a factor, we highly recommend specifying argument ```levels``` explicitly.

- We recommend using sparse GRM to adjust for family relatedness due to its high computational efficiency. And generally, we did not observe a power loss compared to using dense GRM.

## Quick Start-up Guide

The below gives an example to demonstrate the usage of POLMM approaches 

### First read in data and convert phenotype to a factor

```
library(GRAB)
PhenoFile = system.file("extdata", "simuPHENO.txt", package = "GRAB")
PhenoData = data.table::fread(PhenoFile, header = T)
PhenoData = PhenoData %>% mutate(OrdinalPheno = factor(OrdinalPheno, 
                                                       levels = c(0, 1, 2)))
```

### Step 1(a): If dense GRM is used in model fitting, please first prepare PLINK files ```GenoFile```

```
GenoFile = system.file("extdata", "simuPLINK.bed", package = "GRAB")
obj.POLMM = GRAB.NullModel(factor(OrdinalPheno) ~ AGE + GENDER,
                           data = PhenoData, 
                           subjData = PhenoData$IID, 
                           method = "POLMM", 
                           traitType = "ordinal",
                           GenoFile = GenoFile,
                           control = list(showInfo = FALSE, 
                                          LOCO = FALSE, 
                                          tolTau = 0.2, 
                                          tolBeta = 0.1))
```

### Step 1(b): If sparse GRM is used in model fitting, please first prepare sparse GRM file ```SparseGRMFile```

```
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
objPOLMMFile = system.file("results", "objPOLMMFile.RData", package = "GRAB")                                       
save(obj.POLMM, file = objPOLMMFile)                                        
```

### Step 2(a): Single-variant tests using POLMM

```
objPOLMMFile = system.file("results", "objPOLMMFile.RData", package = "GRAB")  
load(objPOLMMFile)   # read in an R object of "obj.POLMM"

GenoFile = system.file("extdata", "simuPLINK.bed", package = "GRAB")
OutputDir = system.file("results", package = "GRAB")
OutputFile = paste0(OutputDir, "/simuMarkerOutput.txt")
GRAB.Marker(obj.POLMM, GenoFile = GenoFile,
            OutputFile = OutputFile)

results = data.table::fread(OutputFile)
hist(results$Pvalue)
```

### Step 2(b): Set-based tests using POLMM-GENE

```
objPOLMMFile = system.file("results", "objPOLMMFile.RData", package = "GRAB")  
load(objPOLMMFile)   # read in an R object of "obj.POLMM"

GenoFile = system.file("extdata", "simuPLINK_RV.bed", package = "GRAB")
OutputDir = system.file("results", package = "GRAB")
OutputFile = paste0(OutputDir, "/simuRegionOutput.txt")
GroupFile = system.file("extdata", "simuPLINK_RV.group", package = "GRAB")
SparseGRMFile = system.file("SparseGRM", "SparseGRM.txt", package = "GRAB")

## make sure the output files does not exist at first
file.remove(OutputFile)
file.remove(paste0(OutputFile, ".markerInfo"))
file.remove(paste0(OutputFile, ".index"))

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


## Citation

- POLMM: Bi, Wenjian, Wei Zhou, Rounak Dey, Bhramar Mukherjee, Joshua N. Sampson, and Seunggeun Lee. **Efficient mixed model approach for large-scale genome-wide association studies of ordinal categorical phenotypes.** *The American Journal of Human Genetics* 108, no. 5 (2021): 825-839.

- POLMM-GENE: Bi, Wenjian, Wei Zhou, Peipei Zhang, Yaoyao Sun, Weihua Yue, and Seunggeun Lee. **Scalable mixed model approaches for set-based association studies on large-scale categorical data analysis and its application to 450k exome sequencing data in UK Biobank.** To be submitted.

