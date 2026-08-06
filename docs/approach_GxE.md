---
layout: default
title: Genome-wide gene-environment interaction (GxE) studies
nav_order: 3
description: "Genome-wide gene-environment interaction (GxE) studies using retrospective methods"
has_children: true
has_toc: true
---

# Genome-wide gene-environment interaction (GxE) studies

[```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) package gives generic GxE analytical frameworks to analyze a wide variaty of phenotypes. 


## Software dependencies and operating systems
[```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) has been thoroughly examined and validated on both Linux and Windows operating systems.

- Currently, R package [```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) supports three formats for genotype input: the R matrix (Rdata) format, the [**PLINK**](https://www.cog-genomics.org/plink2/) format, and the [**BGEN**](https://www.chg.ox.ac.uk/~gav/bgen_format/index.html) format.

- In the near future, R package [```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) is planned to be rewritten using Rcpp code to improve its performance and efficiency.

## How to install and load R package SPAGxECCT
```
library(devtools)  # author version: 2.4.5
install_github("YuzhuoMa97/SPAGxECCT")
library(SPAGxECCT)
?SPAGxECCT  # manual of SPAGxECCT package
```
- Current version is 1.1.0. For older version and version update information, plesase refer to OldVersions.


##  Summary and comparison of main features for efficient G×E analysis methods

| Method   | Trait | Prospective/Retrospective  |Account for population admixture|Account for local ancestry|Account for family relatedness| Account for unbalanced phenotypic distribution  |
|:----------------------:|:------------------------------:|:------------------------:|:----------------------------:|:---------------------:|:---------------------:|:---------------------:|
| SPAGE                  | Binary              | Prospective           |             |    |   |  YES  |
| SPAGxE                 |Quantitative/Binary/Survival/Ordinal/Others|Retrospective|     |      |      | YES |
| SPAGxE<sub>Wald</sub>  |Quantitative/Binary/Survival/Ordinal/Others|Retrospective|     |      |      | YES |
| SPAGxE<sub>CCT</sub>   |Quantitative/Binary/Survival/Ordinal/Others|Retrospective|     |      |      | YES |
| SPAGxE+                |Quantitative/Binary/Survival/Ordinal/Others|Retrospective|     |      |  YES | YES |
| SPAGxEmix<sub>CCT</sub>|Quantitative/Binary/Survival/Ordinal/Others|Retrospective| YES    |      |      | YES |
| SPAGxEmix<sub>CCT-local</sub>|Quantitative/Binary/Survival/Ordinal/Others|Retrospective| YES    |   YES   |      | YES |
| SPAGxEmix<sub>CCT-local-global</sub>|Quantitative/Binary/Survival/Ordinal/Others|Retrospective| YES    |   YES   |      | YES |
| SPAGxEmix+|Quantitative/Binary/Survival/Ordinal/Others|Retrospective| YES    |  YES    |   YES   | YES |


## Quick start-up examples (genotype input using R matrix format)

The following example illustrates how to use SPAGxE<sub>CCT</sub> to analyze a binary trait, with genotype data input provided in the R matrix format.

### Step 1. Read in data and fit a genotype-independent model
```
library(SPAGxECCT)
# Simulate phenotype and genotype
N = 10000                                        # sample size
nSNP = 100                                       # number of SNPs
MAF = 0.1                                        # minor allele frequency
Geno.mtx = matrix(rbinom(N*nSNP,2,MAF),N,nSNP)   # genotype matrix
# NOTE: The row and column names of genotype matrix are required.
rownames(Geno.mtx) = paste0("IID-",1:N)
colnames(Geno.mtx) = paste0("SNP-",1:nSNP)

# phenotype data
Phen.mtx = data.frame(ID = paste0("IID-",1:N),
                      Y=rbinom(N,1,0.5),
                      Cov1=rnorm(N),
                      Cov2=rbinom(N,1,0.5),
                      E = rnorm(N))

Cova.mtx = Phen.mtx[,c("Cov1","Cov2")]    # covariates dataframe excluding environmental factor E
E = Phen.mtx$E                            # environmental factor E

# fit a genotype-independent model
R = SPA_G_Get_Resid("binary",
                    glm(formula = Y ~ Cov1+Cov2+E, data = Phen.mtx, family = "binomial"),
                    data=Phen.mtx,
                    pIDs=Phen.mtx$ID,
                    gIDs=paste0("IID-",1:N))
```

### Step 2. Conduct a marker-level association study

```
# calculate p values
binary.res = SPAGxE_CCT(traits = "binary",                       # trait type
                        Geno.mtx = Geno.mtx,                     # genotype matrix
                        R = R,                                   # residuals from genotype-independent model (null model in which marginal genetic effect and GxE effect are 0)
                        E = E,                                   # environmental factor
                        Phen.mtx = Phen.mtx,                     # phenotype dataframe
                        Cova.mtx = Cova.mtx)                     # covariates dataframe excluding environmental factor E

# we recommand using column of 'p.value.spaGxE.CCT.Wald' to associate genotype with binary phenotypes
head(binary.res)
```


## Quick start-up examples (genotype input using PLINK file format)

The following example illustrates how to use SPAGxE<sub>CCT</sub> to analyze a binary trait, with genotype data input provided in PLINK file format.

### Step 1. Read in data and fit a genotype-independent model

```
library(SPAGxECCT)
# Simulate phenotype and genotype
N = 10000 # sample size

# PLINK format for genotype data
GenoFile = system.file("", "GenoMat_SPAGxE.bed", package = "SPAGxECCT")

# phenotype data
Phen.mtx = data.frame(ID = paste0("IID-",1:N),
                      Y=rbinom(N,1,0.5),
                      Cov1=rnorm(N),
                      Cov2=rbinom(N,1,0.5),
                      E = rnorm(N))

Cova.mtx = Phen.mtx[,c("Cov1","Cov2")]    # covariates dataframe excluding environmental factor E  
E = Phen.mtx$E                            # environmental factor E

# fit a genotype-independent model
R = SPA_G_Get_Resid("binary",
                    glm(formula = Y ~ Cov1+Cov2+E, data = Phen.mtx, family = "binomial"),
                    data=Phen.mtx,
                    pIDs=Phen.mtx$ID,
                    gIDs=paste0("IID-",1:N))
```

### Step 2. Conduct a marker-level association study

```
# calculate p values
binary.res = SPAGxE_CCT(traits = "binary",                       # trait type
                        GenoFile = GenoFile,                     # a character of genotype file
                        R = R,                                   # residuals from genotype-independent model (null model in which marginal genetic effect and GxE effect are 0)
                        E = E,                                   # environmental factor
                        Phen.mtx = Phen.mtx,                     # phenotype dataframe
                        Cova.mtx = Cova.mtx)                     # a covariate matrix excluding the environmental factor E


# we recommand using column of 'p.value.spaGxE.CCT.Wald' to associate genotype with binary phenotypes
head(binary.res)
```


## Quick start-up examples (genotype input using BGEN file format)

The following example illustrates how to use SPAGxE<sub>CCT</sub> to analyze a binary trait, with genotype data input provided in BGEN file format.

### Step 1. Read in data and fit a genotype-independent model

```
library(SPAGxECCT)
# Simulate phenotype and genotype
N = 10000

# BGEN format for genotype data
GenoFile = system.file("", "GenoMat_SPAGxE.bgen", package = "SPAGxECCT")
GenoFileIndex = c(system.file("", "GenoMat_SPAGxE.bgen.bgi", package = "SPAGxECCT"),
                  system.file("", "GenoMat_SPAGxE.sample", package = "SPAGxECCT"))

# phenotype data
Phen.mtx = data.frame(ID = paste0("IID-",1:N),
                      Y=rbinom(N,1,0.5),
                      Cov1=rnorm(N),
                      Cov2=rbinom(N,1,0.5),
                      E = rnorm(N))

Cova.mtx = Phen.mtx[,c("Cov1","Cov2")]    # covariates dataframe excluding environmental factor E  
E = Phen.mtx$E                            # environmental factor E

# fit a genotype-independent model
R = SPA_G_Get_Resid("binary",
                    glm(formula = Y ~ Cov1+Cov2+E, data = Phen.mtx, family = "binomial"),
                    data=Phen.mtx,
                    pIDs=Phen.mtx$ID,
                    gIDs=paste0("IID-",1:N))
```

### Step 2. Conduct a marker-level association study

```
# calculate p values
binary.res = SPAGxE_CCT(traits = "binary",                       # trait type
                        GenoFile = GenoFile,                     # a character of genotype file
                        GenoFileIndex = GenoFileIndex,           # additional index file(s) corresponding to GenoFile
                        R = R,                                   # residuals from genotype-independent model (null model in which marginal genetic effect and GxE effect are 0)
                        E = E,                                   # environmental factor
                        Phen.mtx = Phen.mtx,                     # phenotype dataframe
                        Cova.mtx = Cova.mtx)                     # a covariate matrix excluding the environmental factor E


# we recommand using column of 'p.value.spaGxE.CCT.Wald' to associate genotype with binary phenotypes
head(binary.res)
```



## Note: choose ```traits``` 

Argument ```traits``` is to specify the type of phenotype data. Currently, ```SPAGxECCT``` package supports the below combinations

| phenotype                 | ```traits``` | 
|:-------------------------:|:---------------:|
| binary trait              | "binary"        |
| quantitative trait        | "quantitative"  | 
| ordinal categorical trait | "categorical"   | 
| time-to-event trait       | "time-to-event" |
| Other trait (e.g. longitudinal trait)       | "Resid" |


# Copyright Notice — All Rights Reserved

**Copyright © 2025 Yuzhuo Ma and collaborators. All rights reserved.**

**No license is granted.** The software, code, documentation, and materials in this 
repository related to **SPAGxE** (including SPAGxE, SPAGxE+, SPAGxEmix+, etc.) 
and **WtGxE** are provided for **viewing only**.

**⚠️ IMPORTANT: Unauthorized integration into other packages is strictly prohibited.**  
This repository is not authorized to be included, in whole or in part, into any 
open-source or proprietary software package, library, or tool without explicit 
written permission from the copyright holder. Any such inclusion without prior 
consent constitutes copyright infringement and **may subject the infringer to 
legal liabilities**, including but not limited to:
- DMCA takedown actions and removal of the infringing repository/package from GitHub;
- Civil liabilities for copyright infringement (including damages and injunctive relief);
- Potential criminal liabilities under applicable copyright laws when infringement is committed 
  for profit-making purposes with serious circumstances;
- Academic misconduct proceedings against individuals or institutions involved.

You are **NOT permitted** to:
- Reproduce, copy, or partially copy any part of this code;
- Modify, adapt, translate, or create derivative works from this code;
- Distribute, redistribute, publish, or make this code available to third parties;
- **Incorporate this code or algorithm, in whole or in part, into any other software package, library, or tool (whether open-source or proprietary);**
- Use this code for any commercial or non-commercial purpose without prior written permission.

The retrospective-SPA framework applied to G×E studies was originally proposed by 
Yuzhuo Ma in his master's thesis (2022, DOI:10.27272/d.cnki.gshdu.2022.002946) and 
formalized in Ma et al., *Nature Communications* (2025, DOI:10.1038/s41467-025-57887-3). 
Any implementation of this methodological idea must properly cite the original work.

**To request permission for any use, please contact: yuzhuoma@amss.ac.cn**

