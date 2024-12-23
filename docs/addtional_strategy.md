---
layout: default
title: Additional strategies 
nav_order: 6
description: "Additional strategies to enhance performance"
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

# Additional strategies to enhance performance

## The computational efficiency and statictical power can be enhanced through incorporating polygenic scores (PGSs) as covariates with fixed effects (Optional)

Recent studies have demonstrated that adjusting for polygenic scores (PGSs) can account for polygenic effects and enhance statistical power. In SPAGxE<sub>CCT</sub>, SPAGxE+, SPAGxEmix<sub>CCT</sub>, and SPAGxEmix<sub>CCT-local</sub>, incorporating PGSs as fixed-effect covariates significantly improves computational efficiency. When accurate PGSs are available, a genotype-independent model can be used for genome-wide analyses, enabling the application of regular score statistics followed by a hybrid test employing normal approximation and SPA. By including PGSs as covariates, we eliminate the need to construct statistics through matrix projection or linear regression with genotype data, further optimizing computational efficiency. Additionally, PGS adjustment boosts statistical power by accounting for polygenic effects, complementing the reduced power typically associated with sparse-GRM methods.





Our approach implements a two-stage strategy, referred to as SPAGxE<sub>CCT</sub>(PGS), SPAGxE+(PGS), SPAGxEmix<sub>CCT</sub>(PGS), and SPAGxEmix<sub>CCT-local</sub>(PGS):

- Stage 1: Perform an initial genome-wide association study (GWAS) using tools like SAIGE, and calculate the Leave-One-Chromosome-Out (LOCO) PGS based on summary statistics. Alternatively, use PGSs from external databases like the PGS Catalog.

- Stage 2: Incorporate the LOCO-PGS as an additional covariate in genome-wide G×E analyses using SPAGxE<sub>CCT</sub>, SPAGxE+, SPAGxEmix<sub>CCT</sub>, or SPAGxEmix<sub>CCT-local</sub>.

This general strategy has not yet been fully automated into a function. It's important to note that PGS accuracy varies across genetic ancestries. For multi-ancestry or admixed populations, accurate PGSs must be constructed using methods tailored to these groups, such as the PRS<sub>multi</sub> method for multi-ancestry individuals or the GAUDI method for admixed populations. When testing for ancestry-specific G×E effects using SPAGxEmix<sub>CCT-local</sub>, it is essential to use approaches like the pPRS method, which disentangles ancestry mosaics through local ancestry inference before constructing PGSs.

This strategy not only improves computational efficiency but also enhances statistical power. As part of SPAGxE reproducibility efforts, we will demonstrate how to construct LOCO-PGSs using the clumping and thresholding (C+T) method based on summary statistics. We also plan to develop a function to approximate marginal genetic effects, facilitating the construction of PGSs.



## Rank-based inverse normal transformation to enhance statistical power (Optional)

Model residuals from a fitted null model can be highly unbalanced, especially for longitudinal phenotypes. In such cases, we find that applying a rank-based inverse normal transformation (INT) to the residuals significantly improves empirical power. We propose SPAGxE<sub>CCT(INT)</sub>, SPAGxE+(INT), SPAGxEmix<sub>CCT(INT)</sub>, and SPAGxEmix<sub>CCT-local(INT)</sub>, where the inverse normal transformed residuals are used as input. The p-values from SPAGxE<sub>CCT(INT)</sub>, SPAGxE+(INT), SPAGxEmix<sub>CCT(INT)</sub>, or SPAGxEmix<sub>CCT-local(INT)</sub> can then be combined with those from their untransformed counterparts (SPAGxE<sub>CCT</sub>, SPAGxE+, SPAGxEmix<sub>CCT</sub>, or SPAGxEmix<sub>CCT-local</sub>) using the Cauchy Combination Test (CCT).





