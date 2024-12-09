---
layout: default
title: SPAGxEmix<sub>CCT-local</sub>
nav_order: 3
description: "SPAGxEmix<sub>CCT-local</sub> approaches: quantitative, binary, time-to-event, and ordinal trait analysis."
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

# SPAGxEmix<sub>CCT-local</sub> method 

## Introduction of SPAGxEmix<sub>CCT</sub>

SPAGxEmix<sub>CCT-local</sub> is a scalable and accurate G×E analysis framework that allows tests for ancestry-specific effects by incorporating local ancestry in multi-way admixed populations.

SPAGxEmix<sub>CCT-local</sub> extends SPAGxEmix<sub>CCT</sub> by integrating local ancestry information to enhance the precision of ancestry-specific G×E effect testing and statistical powers. Furthermore, we introduce SPAGxEmix<sub>CCT-local-global</sub>, which combines p-values from both SPAGxEmix<sub>CCT</sub> and SPAGxEmix<sub>CCT-local</sub>, offering an optimal unified approach for various cross-ancestry genetic architectures. As with SPAGxEmix<sub>CCT</sub>, SPAGxEmix<sub>CCT-local</sub> involves two main steps:

- Step 1: SPAGxEmix<sub>CCT-local</sub> fits a genotype-independent (covariates-only) model and calculates the model residuals. Details are described in Step 1 of SPAGxE<sub>CCT</sub>.
  
- Step 2: SPAGxEmix<sub>CCT-local</sub> identifies genetic variants with marginal G×E effects on the trait of interest. First, SPAGxEmix<sub>CCT-local</sub> estimates the ancestry-specific allele frequencies for the variants. Next, SPAGxEmix<sub>CCT-local</sub> evaluates ancestry-specific marginal genetic effects using ancestry-specific score statistics. If an ancestry-specific marginal genetic effect is not significant, we use ancestry-specific test statistic S<sub>G×E(mix)</sub> to characterize the ancestry-specific marginal G×E effect. If significant, S<sub>G×E(mix)</sub> is updated to ancestry-specific genotype-adjusted test statistics. The hybrid strategy to balance computational efficiency and accuracy follows SPAGxE<sub>CCT</sub>.

![plot](https://raw.githubusercontent.com/YuzhuoMa97/RetroSPAgwas.github.io/main/docs/assets/images/workflow_SPAGxEmixCCT_MYZ.png)

**Compared to conventional standard statistical testing methods that account for local ancestry, SPAGxEmix<sub>CCT-local</sub> offers much greater computational efficiency.** 
- SPAGxEmix<sub>CCT-local</sub> leverages local ancestry information to estimate the distribution of ancestry-specific genotypes and the null distribution of test statistics.
- For most tests (ancestry-specific genetic main effect p-values > 0.001) in a genome-wide G×E analysis, SPAGxEmix<sub>CCT-local</sub> utilizes residuals from a genotype-independent model (fitted only once across the genome-wide analysis) to construct test statistics.
- Conventional methods have to incorporate local ancestry as covariates and fit a separate model for each variant, which is computationally burdensome for genome-wide analyses.

## Citation

- **A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits** (to be updated).

