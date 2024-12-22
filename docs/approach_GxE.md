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

The below gives an example to use SPAGxE<sub>CCT</sub> to analyze binary trait. 

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

# Step 2: conduct a marker-level association study
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


## The computational efficiency and statictical power can be enhanced through incorporating polygenic scores (PGSs) as covariates with fixed effects (Optional)

Recent studies have demonstrated that adjusting for polygenic scores (PGSs) can account for polygenic effects and enhance statistical power. In SPAGxE<sub>CCT</sub>, SPAGxE+, SPAGxEmix<sub>CCT</sub>, and SPAGxEmix<sub>CCT-local</sub>, incorporating PGSs as fixed-effect covariates significantly improves computational efficiency. When accurate PGSs are available, a genotype-independent model can be used for genome-wide analyses, enabling the application of regular score statistics followed by a hybrid test employing normal approximation and SPA. By including PGSs as covariates, we eliminate the need to construct statistics through matrix projection or linear regression with genotype data, further optimizing computational efficiency. Additionally, PGS adjustment boosts statistical power by accounting for polygenic effects, complementing the reduced power typically associated with sparse-GRM methods.





Our approach implements a two-stage strategy, referred to as SPAGxE<sub>CCT</sub>(PGS), SPAGxE+(PGS), SPAGxEmix<sub>CCT</sub>(PGS), and SPAGxEmix<sub>CCT-local</sub>(PGS):

- Stage 1: Perform an initial genome-wide association study (GWAS) using tools like SAIGE, and calculate the Leave-One-Chromosome-Out (LOCO) PGS based on summary statistics. Alternatively, use PGSs from external databases like the PGS Catalog.

- Stage 2: Incorporate the LOCO-PGS as an additional covariate in genome-wide G×E analyses using SPAGxE<sub>CCT</sub>, SPAGxE+, SPAGxEmix<sub>CCT</sub>, or SPAGxEmix<sub>CCT-local</sub>.

This general strategy has not yet been fully automated into a function. It's important to note that PGS accuracy varies across genetic ancestries. For multi-ancestry or admixed populations, accurate PGSs must be constructed using methods tailored to these groups, such as the PRS<sub>multi</sub> method for multi-ancestry individuals or the GAUDI method for admixed populations. When testing for ancestry-specific G×E effects using SPAGxEmix<sub>CCT-local</sub>, it is essential to use approaches like the pPRS method, which disentangles ancestry mosaics through local ancestry inference before constructing PGSs.

This strategy not only improves computational efficiency but also enhances statistical power. As part of SPAGxE reproducibility efforts, we will demonstrate how to construct LOCO-PGSs using the clumping and thresholding (C+T) method based on summary statistics. We also plan to develop a function to approximate marginal genetic effects, facilitating the construction of PGSs.



## Rank-based inverse normal transformation to enhance statistical power (Optional)

Model residuals from a fitted null model can be highly unbalanced, especially for longitudinal phenotypes. In such cases, we find that applying a rank-based inverse normal transformation (INT) to the residuals significantly improves empirical power. We propose SPAGxE<sub>CCT(INT)</sub>, SPAGxE+(INT), SPAGxEmix<sub>CCT(INT)</sub>, and SPAGxEmix<sub>CCT-local(INT)</sub>, where the inverse normal transformed residuals are used as input. The p-values from SPAGxE<sub>CCT(INT)</sub>, SPAGxE+(INT), SPAGxEmix<sub>CCT(INT)</sub>, or SPAGxEmix<sub>CCT-local(INT)</sub> can then be combined with those from their untransformed counterparts (SPAGxE<sub>CCT</sub>, SPAGxE+, SPAGxEmix<sub>CCT</sub>, or SPAGxEmix<sub>CCT-local</sub>) using the Cauchy Combination Test (CCT).

