---
layout: default
title: SPAGxE<sub>CCT</sub>
nav_order: 3
description: "SPAGxE+ approaches: quantitative, binary, time-to-event, and ordinal trait analysis."
parent: Genome-wide gene-environment interaction (GxE) studies
has_children: false
has_toc: false
---

# SPAGxE+ method 

SPAGxE+ is a scalable and accurate G×E analytical framework that controls for sample relatedness and unbalanced phenotypic distribution (e.g., case-control imbalance in binary trait analysis). 
It is applicable to a wide range of complex traits with intricate structures, including binary, quantitative, time-to-event, ordinal categorical, longitudinal, and other complex traits. The framework involves two main steps:

- Step 1: SPAGxE+ fits a covariates-only model to calculate model residuals. These covariates include, but are not limited to, confounding factors such as age, sex, SNP-derived principal components (PCs), and environmental factors. The specifics of the model and residuals vary depending on the trait type. Since the covariates-only model is genotype-independent, it only needs to be fitted once across a genome-wide analysis. Incorporating random effects to account for sample relatedness in null model fitting is optional, rather than required.

- Step 2: SPAGxE+ identifies genetic variants with marginal G×E effects on the trait of interest. First, marginal genetic effects are tested using score statistics. If the marginal genetic effect is not significant, S<sub>G×E</sub> is used as the test statistic to characterize the marginal G×E effect. If significant, S<sub>G×E</sub> is updated to genotype-adjusted test statistics. To balance computational efficiency and accuracy, SPAGxE+ employs a hybrid strategy combining normal distribution approximation and SPA to calculate p-values, as used in SPAGxE<sub>CCT</sub> and previous studies such as [SAIGE](https://saigegit.github.io/SAIGE-doc/) and [SPAGE](https://github.com/WenjianBI/SPAGE). 

![plot](https://github.com/YuzhuoMa97/SPAGxECCT/blob/main/workflow/workflow_SPAGxE_Plus_MYZ.png)

Currently, there is still a lack of scalable and accurate gene-environmental interaction analytical frameworks that can control for sample relatedness and be applicable to binary, time-to-event, ordinal categorical, or longitudinal trait analysis. It is usually challenging to detect gene-environmental interaction effects efficiently and accurately while adjusting for sample relateness in a large-scale genome-wide analysis. In GWAS for thousands of phenotypes in large biobanks, most binary traits have substantially fewer cases than controls. Existing methods based on logistic mixed model produce inflated type I errors in the presence of unbalanced case-control ratios. 

SPAGxE+ is a scalable and accurate G×E analytical framework that uses saddlepoint approximation to calibrate the null distribution of test statistics while controlling for sample relatedness and case-control imbalance. Compared to SPAGxE, a sparse genetic relationship matrix (GRM) is used for characterizing familial structure. SPAGxE+ provides accurate p-values even when case-control ratios are extremely unbalanced (e.g. case:control = 1:100). Additionally, SPAGxE+ is applicable to other complex traits including time-to-event, ordinal categorical, and longitudinal traits, and it maintains highly accurate even when phenotypic distribution is unbalanced.

## Citation

- **A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits** (to be updated).

