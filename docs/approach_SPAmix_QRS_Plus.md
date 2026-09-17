---
layout: default
title: SPAmix‑QRS+
nav_order: 5
description: "SPAmix‑QRS+ for quantile regression GWAS with individual‑specific allele frequencies, relatedness, and local ancestry in admixed and diverse populations."
parent: Genome-wide association studies
has_children: false
has_toc: false
---

# SPAmix‑QRS+

[```SPAmix‑QRS+```](https://github.com/YuzhuoMa97/SPAmix-QRSPlus) is an extension of my previously published **SPAmix** (Ma, et al., *Genome Biology* 2025) and **SPAmix+** frameworks, building directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** first described in my master’s thesis ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), DOI: [10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

SPAmix‑QRS+ is designed as a unified quantile‑regression GWAS toolbox for admixed and diverse populations, and it can:

- estimate **individual‑specific allele frequencies (ISAF)** from raw genotypes and SNP‑derived PCs,
- adjust for **sample relatedness** via a sparse genetic relationship matrix (sparse GRM),
- incorporate **local ancestry** via the SPAmixlocal‑QRS+ module,
- apply a **retrospective score test** with **saddlepoint approximation (SPA)** for accurate p‑values,
- combine results across quantiles and ancestries using **Cauchy combination**.

## Method comparison

| Method | Account for population structure | Account for local ancestry | Account for family relatedness | Quantile regression |
|:------:|:-------------------------------:|:--------------------------:|:------------------------------:|:-------------------:|
| SPAmix | YES | YES | NO | NO (mean‑based) |
| SPAmix+ | YES | YES | YES | NO (mean‑based) |
| **SPAmix‑QRS** | **YES** | **YES** | **NO** | **YES (QRS)** |
| **SPAmix‑QRS+** | **YES** | **YES** | **YES** | **YES (QRS)** |

## Relationship with SPAmix and SPAmix+

SPAmix‑QRS+ is the most comprehensive member of the SPAmix family. It combines the quantile‑regression innovation of SPAmix‑QRS (the **quantile regression score test, QRS**) with the relatedness‑adjustment capability of SPAmix+, resulting in the only method that simultaneously handles admixture, local ancestry, family relatedness, and quantile‑specific effects. This work is an independent extension of my own methodological lineage, not adapted from any existing quantile‑regression GWAS.

## Citation

If you use SPAmix‑QRS+, please cite:

- **SPAmix‑QRS+ (this work):**  
  **Ma, Y. et al.**, *SPAmix‑QRS+: quantile regression GWAS with individual‑specific allele frequencies, relatedness, and local ancestry to boost power for admixed and diverse populations*.  

- **SPAmix+ (foundational toolbox for admixture + relatedness + local ancestry):**  
  **Ma, Y. et al.**, *SPAmix+: a scalable, unified toolbox for genome‑wide association studies in admixed and diverse populations with relatedness*.  

- **SPAmix (original ISAF + retrospective SPA framework):**  
  Ma, Y., Xu, H., Li, Y. et al. (2025). SPAmix: a scalable, accurate, and universal analysis framework for large‑scale genetic association studies in admixed populations. *Genome Biology*, 26, 356.  
  [DOI: 10.1186/s13059‑025‑03827‑9](https://doi.org/10.1186/s13059‑025‑03827‑9)

- **Retrospective‑SPA original thesis idea:**  
  Ma, Y. (2022). Empirical Saddlepoint Approximation and Its Application to Genome‑Wide Association Studies.  
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
