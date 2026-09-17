---
layout: default
title: SPAGxE‑QRS
nav_order: 9
description: "SPAGxE‑QRS: quantile regression G×E analysis for quantitative traits in single-population unrelated cohorts."
parent: Genome-wide gene-environment interaction (GxE) studies
has_children: false
has_toc: false
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# SPAGxE‑QRS

SPAGxE‑QRS is a quantile‑regression G×E method proposed in **"Quantile regression gene-environment interaction GWAS for admixed and multi-ancestry cohorts"** (this article). It extends **SPAGxE<sub>CCT</sub>** from mean‑/link‑based retrospective score tests to **quantile regression score test (QRS)**. It builds directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** first described in my master's thesis ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), DOI: [10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

## Introduction of SPAGxE‑QRS

SPAGxE‑QRS is applicable to **quantitative traits** in **single‑population cohorts without sample relatedness**, and serves as the baseline member of the QRS family in this article. The framework involves two main steps:

- Step 1: SPAGxE‑QRS fits a covariates‑only model to calculate model residuals. These covariates include, but are not limited to, confounding factors such as age, sex, SNP‑derived principal components (PCs), and environmental factors. The residuals are then replaced by **quantile regression score test residuals** computed at a specified quantile $\tau$.

- Step 2: SPAGxE‑QRS identifies genetic variants with marginal G×E effects at the given quantile. It first tests marginal genetic effects using score statistics. If the marginal genetic effect is not significant, $S_{G\times E}$ is used as the test statistic; if significant, it is updated to genotype‑adjusted test statistics. To balance computational efficiency and accuracy, SPAGxE‑QRS employs a hybrid strategy combining normal distribution approximation and saddlepoint approximation (SPA), as used in SPAGxE<sub>CCT</sub>, and uses Cauchy combination (CCT) to combine p‑values across quantiles. All test statistics are derived from the **quantile regression score test (QRS)**.

## Main features of SPAGxE‑QRS

- SPAGxE‑QRS is the **single‑population, unrelated‑cohort** member of the QRS family.
- It controls for unbalanced phenotypic distributions through QRS and SPA calibration.
- It is specifically designed for **quantitative traits**.

## Method comparison

| Method | Population structure | Local ancestry | Family relatedness | Quantile regression |
|:------:|:-------------------:|:--------------:|:------------------:|:-------------------:|
| SPAGxE<sub>CCT</sub> | YES | NO | NO | NO (mean‑based) |
| **SPAGxE‑QRS** | **YES** | **NO** | **NO** | **YES (QRS)** |

## Relationship with SPAGxE<sub>CCT</sub>

SPAGxE‑QRS is a direct, independent extension of SPAGxE<sub>CCT</sub>. While SPAGxE<sub>CCT</sub> focuses on mean‑/link‑based G×E association tests, SPAGxE‑QRS introduces the **quantile regression score test (QRS)** to detect G×E effects across the entire phenotypic distribution. It retains SPAGxE<sub>CCT</sub>'s core innovations (retrospective SPA, hybrid normal/SPA calibration, Cauchy combination) and applies them in a quantile‑specific context. The scope of application remains identical: single‑population unrelated cohorts. No part of this work is derived from other quantile‑regression G×E implementations.

## Citation

These three methods — SPAGxE‑QRS, SPAGxEmix‑QRS, and SPAGxE‑QRS+ — are described in one article:

- **This article:**  
  Ma, Y. et al. *Quantile regression gene-environment interaction GWAS for admixed and multi-ancestry cohorts* (to be updated).

- **SPAGxE‑QRS (this work, Section X):**  
  Ma, Y. et al. SPAGxE‑QRS: quantile regression G×E analysis for quantitative traits in single‑population unrelated cohorts.

- **Foundational framework:**  
  Ma, Y. et al. *A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits* (to be updated).

- **Retrospective‑SPA original thesis idea:**  
  Ma, Y. (2022). Empirical Saddlepoint Approximation and Its Application to Genome‑Wide Association Studies.  
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
