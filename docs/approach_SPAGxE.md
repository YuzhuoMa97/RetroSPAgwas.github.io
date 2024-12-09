---
layout: default
title: SPAGxE<sub>CCT</sub>
nav_order: 1
description: "SPAGxECCT approaches: quantitative, binary, time-to-event, and ordinal trait analysis."
parent: Genome-wide gene-environment interaction (GxE) studies
has_children: false
has_toc: false
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# SPAGxE<sub>CCT</sub> method 

**SPAGxE<sub>CCT</sub> is a G×E analysis framework designed for a wide range of complex traits with intricate structures, including time-to-event, ordinal categorical, binary, quantitative, longitudinal, and other complex traits.** The framework involves two main steps:

- Step 1: SPAGxE<sub>CCT</sub> fits a covariates-only model to calculate model residuals. These covariates include, but are not limited to, confounding factors such as age, sex, SNP-derived principal components (PCs), and environmental factors. The specifics of the model and residuals vary depending on the trait type. Since the covariates-only model is genotype-independent, it only needs to be fitted once across a genome-wide analysis.

- Step 2: SPAGxE<sub>CCT</sub> identifies genetic variants with marginal G×E effects on the trait of interest. First, marginal genetic effects are tested using score statistics. If the marginal genetic effect is not significant, S<sub>G×E</sub> is used as the test statistic to characterize the marginal G×E effect. If significant, S<sub>G×E</sub> is updated to genotype-adjusted test statistics. To balance computational efficiency and accuracy, SPAGxE<sub>CCT</sub> employs a hybrid strategy combining normal distribution approximation and saddlepoint approximation (SPA) to calculate p-values, as used in previous studies such as [SAIGE](https://saigegit.github.io/SAIGE-doc/) and [SPAGE](https://github.com/WenjianBI/SPAGE). For variants with significant marginal genetic effects, SPAGxE<sub>CCT</sub> additionally calculates p value through Wald test and uses Cauchy combination (CCT) to combine p values from Wald test and the proposed genotype-adjusted test statistics.



![plot](https://raw.githubusercontent.com/YuzhuoMa97/RetroSPAgwas.github.io/main/docs/assets/images/workflow_SPAGxECCT_MYZ.png)

## Quick start-up examples

The below gives an example to use SPAGxE<sub>CCT</sub> to analyze binary trait. 

### Step 1. Read in data and fit a genotype-independent model

```
library(SPAGxECCT)
# Simulation phenotype and genotype
N = 10000
nSNP = 100
MAF = 0.1
Geno.mtx = matrix(rbinom(N*nSNP,2,MAF),N,nSNP)
# NOTE: The row and column names of genotype matrix are required.
rownames(Geno.mtx) = paste0("IID-",1:N)
colnames(Geno.mtx) = paste0("SNP-",1:nSNP)
Phen.mtx = data.frame(ID = paste0("IID-",1:N),
                      Y=rbinom(N,1,0.5),
                      Cov1=rnorm(N),
                      Cov2=rbinom(N,1,0.5),
                      E = rnorm(N))
Cova.mtx = Phen.mtx[,c("Cov1","Cov2")]    # covariates dataframe excluding environmental factor E  
E = Phen.mtx$E                            # environmental factor E

# fit a null model
R = SPA_G_Get_Resid("binary",
                    glm(formula = Y ~ Cov1+Cov2+E, data = Phen.mtx, family = "binomial"),
                    data=Phen.mtx,
                    pIDs=Phen.mtx$ID,
                    gIDs=paste0("IID-",1:N))
```

# Step 2. Conduct a marker-level association study

```
binary.res = SPAGxE_CCT("binary",
                        Geno.mtx,                     # genotype vector
                        R,                            # residuals from genotype-independent model 
                        E,                            # environmental factor
                        Phen.mtx,                     # phenotype dataframe
                        Cova.mtx)                     # covariates dataframe excluding environmental factor E
# we recommand using column of 'p.value.spaGxE.CCT.Wald' to associate genotype with binary phenotypes
head(binary.res)
```


## Citation

- **A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits** (to be updated).

