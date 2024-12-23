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

[```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) has been thoroughly examined and validated on both Linux and Windows operating systems.

- Currently, R package [```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) supports three formats for genotype input: the R matrix (Rdata) format, the **PLINK** format, and the **BGEN** format.

- In the near future, R package [```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) is planned to be rewritten using Rcpp code to improve its performance and efficiency.


##  Summary and comparison of main features for efficient G×E analysis methods.

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



## Quick start-up examples

The below gives an example to use SPAGxE<sub>CCT</sub> to analyze binary trait. 

```
library(SPAGxECCT)
# Simulate phenotype and genotype
N = 10000 # sample size

# phenotype data
Phen.mtx = data.frame(ID = paste0("IID-",1:N),
                      Y=rbinom(N,1,0.5),
                      Cov1=rnorm(N),
                      Cov2=rbinom(N,1,0.5),
                      E = rnorm(N))

Cova.mtx = Phen.mtx[,c("Cov1","Cov2")]    # covariates dataframe excluding environmental factor E
E = Phen.mtx$E                            # environmental factor E

# Step 1: fit a null model
R = SPA_G_Get_Resid("binary",
                    glm(formula = Y ~ Cov1+Cov2+E, data = Phen.mtx, family = "binomial"),
                    data=Phen.mtx,
                    pIDs=Phen.mtx$ID,
                    gIDs=paste0("IID-",1:N))


nSNP = 100                                       # number of SNPs
MAF = 0.1                                        # minor allele frequency
Geno.mtx = matrix(rbinom(N*nSNP,2,MAF),N,nSNP)   # genotype matrix
# NOTE: The row and column names of genotype matrix are required.
rownames(Geno.mtx) = paste0("IID-",1:N)
colnames(Geno.mtx) = paste0("SNP-",1:nSNP)


# Step 2: conduct a marker-level association study

binary.res = SPAGxE_CCT("binary",
                        Geno.mtx,                     # genotype vector
                        R,                            # residuals from genotype-independent model (null model in which marginal genetic effect and GxE effect are 0)
                        E,                            # environmental factor
                        Phen.mtx,                     # phenotype dataframe
                        Cova.mtx)                     # covariates dataframe excluding environmental factor E

# we recommand using column of 'p.value.spaGxE.CCT.Wald' to associate genotype with binary phenotypes
head(binary.res)
```

## Quick start-up examples  (genotype input using PLINK file format)

The below gives an example to use SPAGxE<sub>CCT</sub> to analyze binary trait. 

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
binary.res = SPAGxE_CCT(traits = "binary",                       # trait type
                        GenoFile = GenoFile,                     # a character of genotype file
                        R = R,                                   # residuals from genotype-independent model (null model in which marginal genetic effect and GxE effect are 0)
                        E = E,                                   # environmental factor
                        Phen.mtx = Phen.mtx,                     # phenotype dataframe
                        Cova.mtx = Cova.mtx)                     # a covariate matrix excluding the environmental factor E


# we recommand using column of 'p.value.spaGxE.CCT.Wald' to associate genotype with binary phenotypes
head(binary.res)
```


## Quick start-up examples  (genotype input using BGEN file format)

The below gives an example to use SPAGxE<sub>CCT</sub> to analyze binary trait. 

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




