---
layout: default
title: SPAGxE‑QRS+
nav_order: 11
description: "SPAGxE‑QRS+: quantile regression G×E analysis for quantitative traits in single-population cohorts with relatedness."
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

# SPAGxE‑QRS+

SPAGxE‑QRS+ is a quantile‑regression G×E method proposed in **"Efficient quantile regression gene-environment interaction analysis for admixed and multi-ancestry cohorts"** (this article). It extends **SPAGxE+ (single‑population version)** from mean‑/link‑based retrospective score tests to **quantile regression score test (QRS)**, and builds directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** ([Ma, 2022](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

## Introduction of SPAGxE‑QRS+

SPAGxE‑QRS+ is applicable to **quantitative traits** in **single‑population cohorts with sample relatedness**. It accounts for familial structure via a sparse genetic relationship matrix (GRM) but does not incorporate local ancestry, as it targets homogeneous populations. The framework involves two main steps:

- Step 1: SPAGxE‑QRS+ fits a covariates‑only model to calculate model residuals. Incorporating random effects to account for sample relatedness in null model fitting is optional. The residuals are then replaced by **quantile regression score test residuals** at a specified quantile $\tau$.

- Step 2: SPAGxE‑QRS+ identifies genetic variants with marginal G×E effects at the given quantile. It first tests marginal genetic effects using score statistics. If the marginal genetic effect is not significant, $S_{G\times E}$ is used as the test statistic; if significant, it is updated to genotype‑adjusted test statistics. To balance computational efficiency and accuracy, SPAGxE‑QRS+ employs a hybrid strategy combining normal distribution approximation and SPA, as used in SPAGxE+, and uses Cauchy combination (CCT) to combine p‑values across quantiles. All test statistics are derived from QRS.

## Main features of SPAGxE‑QRS+

- SPAGxE‑QRS+ is designed for **single‑population cohorts with sample relatedness**.
- It uses a **sparse GRM** to capture family structure without requiring local ancestry.
- It provides accurate p‑values even when the phenotypic distribution is unbalanced.
- It is specifically designed for **quantitative traits**.

## Method comparison

| Method | Population structure | Local ancestry | Family relatedness | Quantile regression |
|:------:|:-------------------:|:--------------:|:------------------:|:-------------------:|
| SPAGxE+ (single‑pop) | YES | NO | YES | NO (mean‑based) |
| **SPAGxE‑QRS+** | **YES** | **NO** | **YES** | **YES (QRS)** |

## Relationship with SPAGxE+ (single‑population version)

SPAGxE‑QRS+ is a direct, independent extension of the single‑population version of SPAGxE+. While SPAGxE+ (single‑pop) focuses on mean‑/link‑based G×E association tests controlling for relatedness in homogeneous populations, SPAGxE‑QRS+ introduces the **quantile regression score test (QRS)** to detect G×E effects across the entire phenotypic distribution. It retains SPAGxE+'s core innovations (sparse GRM adjustment, retrospective SPA) and applies them in a quantile‑specific context. The scope of application remains identical: single‑population cohorts with relatedness.

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
