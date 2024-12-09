---
layout: default
title: Genome-wide gene-environment interaction (GxE) studies
nav_order: 3
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: true
has_toc: true
---

# Genome-wide gene-environment interaction (GxE) studies

[```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) package gives generic GxE analytical frameworks to analyze a wide variaty of phenotypes. 

[```SPAGxECCT```](https://github.com/YuzhuoMa97/SPAGxECCT) package has been tested under linux and windows systems and will soon be rewritten using Rcpp code to support genotype data in PLINK format!


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

The below gives an example to use SPAGxE<sub>CCT</sub> to analyze ordinal binary trait. 

```
library(SPAGxECCT)
# Simulation phenotype and genotype
N = 10000
Phen.mtx = data.frame(ID = paste0("IID-",1:N),
                      Y=rbinom(N,1,0.5),
                      Cov1=rnorm(N),
                      Cov2=rbinom(N,1,0.5),
                      E = rnorm(N))

Cova.mtx = Phen.mtx[,c("Cov1","Cov2")]    # covariates dataframe excluding environmental factor E

E = Phen.mtx$E

# Step 1: fit a null model
R = SPA_G_Get_Resid("binary",
                    glm(formula = Y ~ Cov1+Cov2+E, data = Phen.mtx, family = "binomial"),
                    data=Phen.mtx,
                    pIDs=Phen.mtx$ID,
                    gIDs=paste0("IID-",1:N))

# Step 2(a): conduct a marker-level association study
nSNP = 100
MAF = 0.1
Geno.mtx = matrix(rbinom(N*nSNP,2,MAF),N,nSNP)
# NOTE: The row and column names of genotype matrix are required.
rownames(Geno.mtx) = paste0("IID-",1:N)
colnames(Geno.mtx) = paste0("SNP-",1:nSNP)

binary.res = SPAGxE_CCT("binary",
                        Geno.mtx,                     # genotype vector
                        R,                            # residuals from genotype-independent model (null model in which marginal genetic effect and GxE effect are 0)
                        E,                            # environmental factor
                        Phen.mtx,                     # phenotype dataframe
                        Cova.mtx)                     # covariates dataframe excluding environmental factor E

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



