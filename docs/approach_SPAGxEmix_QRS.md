---
layout: default
title: SPAGxEmix‑QRS
nav_order: 10
description: "SPAGxEmix‑QRS: quantile regression G×E analysis for quantitative traits in admixed and multi-ancestry cohorts without relatedness."
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

# SPAGxEmix‑QRS

SPAGxEmix‑QRS is a quantile‑regression G×E method proposed in **"Efficient quantile regression gene-environment interaction analysis for admixed and multi-ancestry cohorts"** (this article). As an extension of SPAGxEmix<sub>CCT</sub>, it is a G×E analytical framework applicable to individuals from multiple ancestries or multi‑way admixed populations, without sample relatedness. It extends SPAGxEmix<sub>CCT</sub> from mean‑/link‑based retrospective score tests to **quantile regression score test (QRS)**, and builds directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** ([Ma, 2022](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

## Introduction of SPAGxEmix‑QRS

SPAGxEmix‑QRS allows for different allele frequencies for genotypes. It estimates **individual‑level allele frequencies** using SNP‑derived principal components (PCs) and raw genotypes. It is designed for **quantitative traits** in admixed and multi‑ancestry cohorts without relatedness. The framework involves two main steps:

- Step 1: SPAGxEmix‑QRS fits a genotype‑independent (covariates‑only) model and calculates the model residuals. The residuals are then replaced by **quantile regression score test residuals** at a specified quantile $\tau$.

- Step 2: SPAGxEmix‑QRS identifies genetic variants with marginal G×E effects on the trait of interest at the given quantile. It first estimates the individual‑level allele frequencies of the tested variants using SNP‑derived PCs and raw genotypes. Next, it evaluates marginal genetic effects using score statistics. If the marginal genetic effect is not significant, $S_{G\times E(\text{mix})}$ is used as the test statistic; if significant, it is updated to genotype‑adjusted test statistics. The hybrid strategy to balance computational efficiency and accuracy follows SPAGxEmix<sub>CCT</sub>, with all statistics derived from QRS.

## Main features of SPAGxEmix‑QRS

Admixed populations are routinely excluded from genomic studies due to concerns over population structure. SPAGxEmix‑QRS addresses this by estimating individual‑level allele frequencies to characterize individual‑level genetic ancestries using information from SNP‑derived PCs and raw genotype data in a model‑free approach.

- It does not necessitate accurate specification of, or the availability of, appropriate reference population panels for the ancestries contributing to the individual.
- It is not sensitive to model misspecification (e.g., missed or biased confounder‑trait associations) or trait‑based ascertainment.
- It is applicable to admixed and multi‑ancestry cohorts **without sample relatedness** and is designed for **quantitative traits**.

## Method comparison

| Method | Population structure | Local ancestry | Family relatedness | Quantile regression |
|:------:|:-------------------:|:--------------:|:------------------:|:-------------------:|
| SPAGxEmix<sub>CCT</sub> | YES | YES | NO | NO (mean‑based) |
| **SPAGxEmix‑QRS** | **YES** | **YES** | **NO** | **YES (QRS)** |

## Relationship with SPAGxEmix<sub>CCT</sub>

SPAGxEmix‑QRS is a direct, independent extension of SPAGxEmix<sub>CCT</sub>. While SPAGxEmix<sub>CCT</sub> focuses on mean‑/link‑based G×E association tests in admixed populations, SPAGxEmix‑QRS introduces the **quantile regression score test (QRS)** to detect G×E effects across the entire phenotypic distribution. It retains SPAGxEmix<sub>CCT</sub>'s core innovations (ISAF estimation, retrospective SPA, local ancestry handling) and applies them in a quantile‑specific context. The scope of application remains identical: admixed and multi‑ancestry cohorts without relatedness.

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
