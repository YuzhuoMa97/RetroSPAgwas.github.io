---
layout: default
title: Genome-wide gene-environment interaction (GxE) studies
nav_order: 3
description: "Genome-wide gene-environment interaction (GxE) studies using retrospective methods"
has_children: true
has_toc: true
---

<!-- SPAGXE_CPP_WEB_BEGIN -->
## Standalone C++ software

The official standalone **SPAGxE 1.2.0** C++ edition is available as a development
source in the same [SPAGxECCT repository](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop).
It provides SPAGxE, SPAGxE+, SPAGxEmix and SPAGxEmix_local. The original R edition,
its method descriptions and examples remain below.

The [complete C++ manual](/RetroSPAgwas.github.io/docs/spagxe_cpp/index.html) keeps the new installation and teaching material
in one place, with separate pages for the four methods, local formats, all current
options and worked examples. Start with [download and first run](/RetroSPAgwas.github.io/docs/spagxe_cpp/start.html), then
follow the [complete tutorial](/RetroSPAgwas.github.io/docs/spagxe_cpp/full_tutorial.html). Read [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the
tested source revision and current platform/CI limits; do not assume a release
binary or tag exists merely because the source branch is public.

| Method | C++ tutorial |
|---|---|
| SPAGxE | [Shared AF, unrelated subjects](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxe.html) |
| SPAGxE+ | [Shared AF and sparse GRM](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxe_plus.html) |
| SPAGxEmix | [Individual AF and ancestry PCs](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxemix.html) |
| SPAGxEmix_local | [Known-H ancestry-specific G/H](/RetroSPAgwas.github.io/docs/spagxe_cpp/spagxemix_local.html) |

<a id="standalone-cpp-installation"></a>
The former C++ installation section is now the [dedicated installation page](/RetroSPAgwas.github.io/docs/spagxe_cpp/installation.html).
R and C++ have separate installation routes; installing the R package does not install
the executable. This is the sole official standalone C++ distribution designated
and maintained by Yuzhuo Ma. Contact: [yuzhuoma@amss.ac.cn](mailto:yuzhuoma@amss.ac.cn).

**Maintenance candidate.** This page accompanies local SPAGxE 1.2.0 maintenance source that has not yet been pushed or tagged. The [public baseline](https://github.com/YuzhuoMa97/SPAGxECCT/commit/c7c11590efbd10504115cd0ad8dbb9c6ca2634e1) passed hosted Windows and Ubuntu checks; its macOS build failed. Those hosted results do not validate this new candidate. Read the [candidate validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the current evidence and download boundaries.
<!-- SPAGXE_CPP_WEB_END -->


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


# License & Copyright

**Copyright © 2025 Yuzhuo Ma and collaborators. All rights reserved.**

This repository (including code, documentation, and materials related to SPAGxE, SPAGxE+, SPAGxEmix+, WtGxE, and SPAGxE‑GENE) is shared for learning and research purposes.

## You are permitted to:
- Download and read the code.
- Modify it privately for your own non‑commercial research or personal study.
- Run the modified code locally for your own analyses.

## You are NOT permitted to (without explicit written permission):
1. **Publicly integrate this code, in whole or in part, into any other software package, library, or tool** – whether open‑source or proprietary. This includes:
   - Bundling the code into an R/Python/Julia package;
   - Including it as a dependency in another project;
   - Distributing a modified or "polished" version as a separate package;
   - Any form of re‑packaging, regardless of how much the code has been modified or adapted.
2. Publicly redistribute the code (verbatim or modified) through any channel.
3. Use the code for commercial purposes.
4. Remove or alter this copyright notice.

## Attribution
If you use or adapt the methodological ideas (especially the retrospective‑SPA framework for G×E studies), please cite:
- Master's thesis (2022): DOI:10.27272/d.cnki.gshdu.2022.002946
- Ma et al., *Nature Communications* (2025): DOI:10.1038/s41467‑025‑57887‑3

## Contact
For any questions or collaborative projects, please contact yuzhuoma@amss.ac.cn.

---


