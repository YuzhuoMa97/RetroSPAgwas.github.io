---
layout: default
title: SPAGxEmix‑QRS+
nav_order: 12
description: "SPAGxEmix‑QRS+: quantile regression G×E analysis for quantitative traits in admixed and multi-ancestry cohorts with relatedness and local ancestry."
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

# SPAGxEmix‑QRS+

SPAGxEmix‑QRS+ is a quantile‑regression G×E method proposed in **"Efficient quantile regression gene-environment interaction analysis for admixed and multi-ancestry cohorts"** (this article). It extends **SPAGxEmix+** from mean‑/link‑based retrospective score tests to **quantile regression score test (QRS)**, and builds directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** ([Ma, 2022](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

## Introduction of SPAGxEmix‑QRS+

SPAGxEmix‑QRS+ is applicable to **quantitative traits** in **admixed and multi‑ancestry cohorts with sample relatedness and local ancestry**. It is the most comprehensive member of the QRS family in this article, simultaneously handling population stratification, local ancestry, and familial correlations. The framework consists of three main steps:

- **Step 0 (a):** SPAGxEmix‑QRS+ employs PC‑AiR (Conomos et al., 2015, *Genet. Epidemiol.*) to compute ancestry‑representative principal components (PCs) that capture distant genetic relatedness, such as population structure.

- **Step 0 (b):** SPAGxEmix‑QRS+ utilizes PC‑Relate (Conomos et al., 2016, *Am. J. Hum. Genet.*) to estimate an ancestry‑adjusted sparse GRM or sparse kinship coefficient matrix, representing recent genetic relatedness.

- **Step 0 (c):** Iterations of Step 0 (a) and Step 0 (b) refine the inference of both population structure (via PC‑AiR) and recent genetic relatedness (via PC‑Relate). Typically, two iterations are sufficient to produce accurate ancestry‑adjusted principal components and a sparse GRM.

- **Step 1:** SPAGxEmix‑QRS+ fits a covariates‑only model to calculate model residuals. Incorporating random effects to account for sample relatedness in null model fitting is optional. The residuals are then replaced by **quantile regression score test residuals** at a specified quantile $\tau$.

- **Step 2:** SPAGxEmix‑QRS+ identifies genetic variants with marginal G×E effects at the given quantile. It first estimates the individual‑level allele frequencies (ISAF) and local ancestry of the tested variants using SNP‑derived PCs (from Step 0) and raw genotypes. Next, it evaluates marginal genetic effects using score statistics. If the marginal genetic effect is not significant, $S_{G\times E(\text{mix})}$ is used as the test statistic; if significant, it is updated to genotype‑adjusted test statistics. To balance computational efficiency and accuracy, SPAGxEmix‑QRS+ employs a hybrid strategy combining normal distribution approximation and SPA, as used in SPAGxEmix+, and uses Cauchy combination (CCT) to combine p‑values across quantiles and ancestries. All test statistics are derived from QRS.

## Main features of SPAGxEmix‑QRS+

- SPAGxEmix‑QRS+ is designed for **admixed and multi‑ancestry cohorts with sample relatedness**.
- It incorporates **individual‑specific allele frequencies (ISAF)** and **local ancestry** to correct for population structure and admixture.
- A **sparse genetic relationship matrix (GRM)** estimated via PC‑AiR and PC‑Relate is used to account for familial correlations.
- It provides accurate p‑values even when the phenotypic distribution is unbalanced.
- It is specifically designed for **quantitative traits**.

## Method comparison

| Method | Population structure | Local ancestry | Family relatedness | Quantile regression |
|:------:|:-------------------:|:--------------:|:------------------:|:-------------------:|
| SPAGxEmix+ | YES | YES | YES | NO (mean‑based) |
| **SPAGxEmix‑QRS+** | **YES** | **YES** | **YES** | **YES (QRS)** |

## Relationship with SPAGxEmix+

SPAGxEmix‑QRS+ is a direct, independent extension of SPAGxEmix+. While SPAGxEmix+ focuses on mean‑/link‑based G×E association tests controlling for relatedness, population structure, and admixture, SPAGxEmix‑QRS+ introduces the **quantile regression score test (QRS)** to detect G×E effects across the entire phenotypic distribution. It retains SPAGxEmix+'s core innovations (PC‑AiR/PC‑Relate iteration, ISAF estimation, sparse GRM, retrospective SPA, local ancestry handling) and applies them in a quantile‑specific context. The scope of application remains identical: admixed and multi‑ancestry cohorts with relatedness.

## Citation

All four methods — SPAGxE‑QRS, SPAGxEmix‑QRS, SPAGxE‑QRS+, and SPAGxEmix‑QRS+ — are described in one article:

- **This article:**  
  Ma, Y. et al. *Efficient quantile regression gene-environment interaction analysis for admixed and multi-ancestry cohorts* (to be updated).

- **Foundational framework:**  
  Ma, Y., Zhao, Y., Zhang, J.-F., & Bi, W. (2025). Efficient and accurate framework for genome-wide gene-environment interaction analysis in large-scale biobanks. *Nature Communications*, 16, 3064.  
  [DOI: 10.1038/s41467-025-57887-3](https://doi.org/10.1038/s41467-025-57887-3)

- **Retrospective‑SPA original thesis idea:**  
  Ma, Y. (2022). Empirical Saddlepoint Approximation and Its Application to Genome‑Wide Association Studies.  
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
