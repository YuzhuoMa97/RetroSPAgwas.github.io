---
layout: default
title: SPAGxEmix+
nav_order: 5
description: "SPAGxEmix+ approaches: quantitative, binary, time-to-event, and ordinal trait analysis."
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

# SPAGxEmix+  

As an extension of SPAGxEmix<sub>CCT</sub>, SPAGxEmix+ accommodates individuals from multiple ancestries or multi-way admixed populations while controlling for both population structure and familial relatedness. Admixed individuals can be analyzed within a cohort alone or alongside homogeneous groups using this framework.

## Introduction of SPAGxEmix+


SPAGxEmix+ comprises three main steps:

- Step 0 (a): SPAGxEmix+ employs PC-AiR (Conomos et al., 2015, Gen Epi) to compute ancestry-representative principal components (PCs) that capture distant genetic relatedness, such as population structure.
  
- Step 0 (b): SPAGxEmix+ utilizes PC-Relate (Conomos et al., 2016, AJHG) to estimate an ancestry-adjusted sparse GRM or sparse kinship coefficient matrix, representing recent genetic relatedness.
  
- Step 0 (c): Iterations of Step 0 (a) and Step 0 (b) refine the inference of both population structure (via PC-AiR) and recent genetic relatedness (via PC-Relate).

- Step 1: SPAGxEmix+ fits a genotype-independent (covariates-only) model and computes residuals, as detailed in Step 1 of SPAGxE<sub>CCT</sub>. Incorporating random effects to account for sample relatedness during null model fitting is optional.

- Step 2: SPAGxEmix+ identifies genetic variants with marginal G×E effects on the trait of interest. It first estimates the individual-level allele frequencies of the tested variants using SNP-derived PCs (from Step 0) and raw genotypes. Next, SPAGxEmix<sub>CCT</sub>+ evaluates marginal genetic effects using score statistics. If the marginal genetic effect is not significant, S<sub>G×E(mix)</sub>+ is used as the test statistic to characterize the marginal G×E effect. If significant, S<sub>G×E(mix)</sub>+ is updated with genotype-adjusted test statistics. The hybrid strategy to balance computational efficiency and accuracy follows SPAGxE<sub>CCT</sub>.

## Main features of SPAGxEmix+

- The Genetic Relationship Matrix (GRM) contains information on both ancestry and familial relatedness. As introduced in the PC-Relate paper, the empirical GRM has been widely used for inferring population structure (distant genetic relatedness) in samples without close relatives, as well as for estimating recent kinship and heritability of complex traits in single-population studies. However, in multi-ancestry or admixed population studies, a thresholded GRM cannot be sparsified effectively. To address this, we employ PC-AiR and PC-Relate (implemented in the GENESIS R package) to obtain principal components (representing distant genetic relatedness) and sparse kinship coefficients (representing recent genetic relatedness).

- PC-AiR is specifically designed for robust inference of population structure in the presence of recent genetic relatedness—whether known or cryptic—among sampled individuals. It performs Principal Component Analysis (PCA) on genome-wide SNP data to detect population structure, while accounting for relatedness to avoid confounding ancestry inference with familial relationships. Unlike standard PCA, PC-AiR adjusts for relatedness, allowing accurate estimation of ancestry that is unaffected by family structure. PC-Relate, on the other hand, uses ancestry-representative principal components to adjust for population structure/ancestry and provide precise estimates of recent genetic relatedness.

- To analyze individuals from multi-ancestry or multi-way admixed populations with familial relatedness, SPAGxEmix+ first uses PC-AiR to obtain principal components representing population structure. It then applies PC-Relate to regress out the PCs from the genotypes, yielding ancestry-adjusted genotypes and kinship estimates to assess family structure (i.e., recent genetic relatedness). The PC-Relate paper demonstrates that an iterative process alternating between PC-AiR and PC-Relate can enhance inference for both population structure (via PC-AiR) and recent genetic relatedness (via PC-Relate). Typically, two iterations are sufficient to produce accurate ancestry-adjusted principal components and a sparse GRM.

- Steps 1 and 2 of the SPAGxEmix+ analysis are similar to those in SPAGxEmix<sub>CCT</sub>. In Step 2, the ancestry-adjusted sparse GRM is crucial for characterizing familial structure, and SPA is used to calibrate p-values.


**SPAGxEmix+ is a scalable and accurate G×E analytical framework designed to control for both (1) population structure and (2) familial relatedness across diverse population and family structures. It is especially suited for cohorts that include individuals from multi-ancestry or multi-way admixed populations, effectively handling ancestry-specific minor allele frequencies (MAFs) and ancestry-specific case-control ratios (or other ancestry-specific phenotypic distribution such as event rates for time-to-event traits).**

## Citation

- to be submitted

