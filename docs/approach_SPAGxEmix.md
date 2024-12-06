---
layout: default
title: SPAGxEmix<sub>CCT</sub>
nav_order: 2
description: "SPAGxEmix<sub>CCT</sub> approaches: quantitative, binary, time-to-event, and ordinal trait analysis."
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

# SPAGxEmix<sub>CCT</sub> method 

## Introduction of SPAGxEmix<sub>CCT</sub>

As an extension of SPAGxE<sub>CCT</sub>, SPAGxEmix<sub>CCT</sub> is a G×E analysis framework which is applicable to individuals from multiple ancestries or multi-way admixed populations. 

SPAGxEmix<sub>CCT</sub> allows for different allele frequencies for genotypes. SPAGxEmix<sub>CCT</sub> estimates individual-level allele frequencies using SNP-derived principal components (PCs) and raw genotypes. Similar to SPAGxE<sub>CCT</sub>, SPAGxEmix<sub>CCT</sub> involves two main steps:

- Step 1: SPAGxEmix<sub>CCT</sub> fits a genotype-independent (covariates-only) model and calculates the model residuals. Detailed information is provided in Step 1 of SPAGxE<sub>CCT</sub>.

- Step 2: SPAGxEmix<sub>CCT</sub> identifies genetic variants with marginal G×E effects on the trait of interest. It first estimates the individual-level allele frequencies of the tested variants using SNP-derived PCs and raw genotypes. Next, SPAGxEmix<sub>CCT</sub> evaluates marginal genetic effects using score statistics. If the marginal genetic effect is not significant, S<sub>G×E(mix)</sub> is used as the test statistic to characterize the marginal G×E effect. If significant, S<sub>G×E(mix)</sub> is updated to genotype-adjusted test statistics. The hybrid strategy to balance computational efficiency and accuracy follows SPAGxE<sub>CCT</sub>.

Admixed populations are routinely excluded from genomic studies due to concerns over population structure. The admixed population analysis is technically challenging as it requires addressing the complicated patterns of genetic and phenotypic diversities that arise from distinct genetic backgrounds and environmental exposures. As the genetic ancestries are increasingly recognized as continuous rather than discrete, **SPAGxEmix<sub>CCT</sub> estimates individual-level allele frequencies to characterize the individual-level genetic ancestries using information from the SNP-derived PCs and raw genotype data in a model-free approach. Therefore, SPAGxEmix<sub>CCT</sub> does not necessitate accurate specification of and the availability of appropriate reference population panels for the ancestries contributing to the individual, which might be unknown or not well defined. In addition, SPAGxEmix<sub>CCT</sub> is not sensitive to model misspecification (e.g. missed or biased confounder-trait associations) and trait-based ascertainment.**

![plot](https://github.com/YuzhuoMa97/RetroSPAgwas.github.io/blob/main/docs/assets/images/workflow_SPAGxEmixCCT_MYZ.png)

## Citation

- **A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits** (to be updated).

