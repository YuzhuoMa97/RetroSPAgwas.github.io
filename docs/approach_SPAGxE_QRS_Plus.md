---
layout: default
title: SPAGxE‑QRS+
nav_order: 11
description: "SPAGxE‑QRS+: quantile regression G×E analysis controlling for sample relatedness and unbalanced phenotypes in admixed and diverse populations."
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

SPAGxE‑QRS+ is a quantile‑regression G×E method proposed in **"Quantile regression gene-environment interaction GWAS for admixed and multi-ancestry cohorts"** (this article). It extends **SPAGxE+** from mean‑/link‑based retrospective score tests to **quantile regression score test (QRS)**, and builds directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** ([Ma, 2022](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

## Introduction of SPAGxE‑QRS+

SPAGxE‑QRS+ is applicable to a wide range of complex traits, including binary, quantitative, time‑to‑event, ordinal categorical, longitudinal, and other complex traits. It is designed for **admixed and diverse populations with sample relatedness**, and is the most comprehensive member of the QRS family in this article. The framework involves two main steps:

- Step 1: SPAGxE‑QRS+ fits a covariates‑only model to calculate model residuals. Incorporating random effects to account for sample relatedness in null model fitting is optional. The residuals are then replaced by **quantile regression score test residuals** at a specified quantile $\tau$.

- Step 2: SPAGxE‑QRS+ identifies genetic variants with marginal G×E effects at the given quantile. It first tests marginal genetic effects using score statistics. If the marginal genetic effect is not significant, $S_{G\times E}$ is used as the test statistic; if significant, it is updated to genotype‑adjusted test statistics. To balance computational efficiency and accuracy, SPAGxE‑QRS+ employs a hybrid strategy combining normal distribution approximation and SPA, as used in SPAGxE+, and uses Cauchy combination (CCT) to combine p‑values across quantiles and ancestries. All test statistics are derived from QRS.

## Main features of SPAGxE‑QRS+

Currently, there is still a lack of scalable and accurate gene‑environment interaction analytical frameworks that can control for sample relatedness and be applicable to binary, time‑to‑event, ordinal categorical, or longitudinal trait analysis in admixed populations. SPAGxE‑QRS+ fills this gap:

- Compared to SPAGxE‑QRS and SPAGxEmix‑QRS, a **sparse genetic relationship matrix (GRM)** is used for characterizing familial structure.
- **Individual‑specific allele frequencies (ISAF)** and **local ancestry** information are incorporated.
- SPAGxE‑QRS+ provides accurate p‑values even when case‑control ratios are extremely unbalanced (e.g., case:control = 1:99).
- It maintains high accuracy even when phenotypic distribution is unbalanced.

## Method comparison

| Method | Population structure | Local ancestry | Family relatedness | Quantile regression |
|:------:|:-------------------:|:--------------:|:------------------:|:-------------------:|
| SPAGxE+ | YES | YES | YES | NO (mean‑based) |
| **SPAGxE‑QRS+** | **YES** | **YES** | **YES** | **YES (QRS)** |

## Relationship with SPAGxE+

SPAGxE‑QRS+ is a direct, independent extension of SPAGxE+. While SPAGxE+ focuses on mean‑/link‑based G×E association tests controlling for relatedness and unbalanced phenotypes, SPAGxE‑QRS+ introduces the **quantile regression score test (QRS)** to detect G×E effects across the entire phenotypic distribution. It retains SPAGxE+'s core innovations (sparse GRM adjustment, ISAF estimation, retrospective SPA, local ancestry handling) and applies them in a quantile‑specific context. The scope of application remains identical: admixed and diverse populations with relatedness.

## Citation

These three methods — SPAGxE‑QRS, SPAGxEmix‑QRS, and SPAGxE‑QRS+ — are described in one article:

- **This article:**  
  Ma, Y. et al. *Quantile regression gene-environment interaction GWAS for admixed and multi-ancestry cohorts* (to be updated).

- **SPAGxE‑QRS+ (this work, Section X):**  
  Ma, Y. et al. SPAGxE‑QRS+: quantile regression G×E analysis controlling for sample relatedness and unbalanced phenotypes.

- **Foundational framework:**  
  Ma, Y. et al. *A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits* (to be updated).

- **Retrospective‑SPA original thesis idea:**  
  Ma, Y. (2022). Empirical Saddlepoint Approximation and Its Application to Genome‑Wide Association Studies.  
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
